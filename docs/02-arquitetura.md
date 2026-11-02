# Arquitetura

## Estilo: Hexagonal (Ports and Adapters)
- Domain: modelo e regras puras.
- Application: casos de uso e portas. `port/in` (o que o mundo pede ao sistema) e `port/out` (o que o sistema precisa do mundo: repositórios, publicador de eventos, relógio, hash de senha, emissor de token).
- Adapters in: REST (controllers) e mensageria (consumers Kafka).
- Adapters out: persistência MongoDB, publicador Kafka, segurança (JWT, BCrypt).
- Regra de dependência: adapter -> application -> domain. Nunca o contrário. Verificada por ArchUnit.

## Estrutura de pacotes (backend)
com.nutritrack
- identity (auth, users, roles, permissions)
- profile (perfil, metas de peso)
- tracking (peso, água)
- nutrition (alimentos, refeições, metas diárias, alertas)
- notification (notificações, conquistas)
- dashboard (consultas agregadas, relatórios)
- bootstrap (config de segurança, Kafka, Mongo, seeders, relógio)
Cada contexto repete: domain, application/{port/in,port/out,usecase}, adapter/{in/rest,in/messaging,out/persistence,out/messaging}.

Comunicação entre contextos: apenas por portas de saída/entrada ou eventos; sem acessar repositório de outro contexto diretamente.

## Fluxo assíncrono (Kafka)
1. Casos de uso gravam no MongoDB e publicam um evento via porta `EventPublisher` (adapter Kafka).
2. Consumers (adapter in/messaging) processam de forma idempotente (coleção `processed_events` com `eventId`).
3. Consumer de `meal.registered` e `water.registered` reavalia limites do dia e cria notificações; publica `limit.exceeded` quando aplicável.
4. Consumer de `weight.recorded` atualiza conquistas e a sequência de dias.
5. Falhas: retry com backoff e dead-letter topic (`<topico>.dlt`).
Justificativa: feedback imediato vem do cálculo síncrono; Kafka cuida de efeitos colaterais desacoplados (notificações, conquistas) sem travar a requisição.

## Segurança
JWT stateless, filtro de autenticação, `mustChangePassword` embutido como claim e verificado no filtro. CORS desnecessário em produção (proxy Nginx na mesma origem); liberar `http://localhost:4200` somente no perfil dev.

## Decisões fixas
- Módulo Maven único (`backend/pom.xml`), sem multi-módulo.
- Sem Lombok. Java records onde cabível.
- OpenAPI via springdoc somente se houver versão compatível com Spring Boot 4; caso contrário, documentar a API em `docs/04` e omitir.
- Mongo sem replica set (sem transações multi-documento); modele agregados para não precisar delas.
