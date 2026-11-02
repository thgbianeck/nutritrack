# Estratégia de testes

Pirâmide: muitos unitários, alguns de integração com contêineres reais, poucos E2E.

## Backend
- Unitários de domínio: IMC, idade, TMB, TDEE, meta calórica (casos de ganho, perda, manutenção, meta irrealista, piso), macros, classificação 80%/100%, média móvel, regressão, streak, conquistas, política de senha.
- Unitários de casos de uso com Mockito nas portas de saída.
- Integração (Testcontainers MongoDB): repositórios, índices únicos, consultas por intervalo de datas.
- Integração (Testcontainers MongoDB + Kafka): fluxo completo registrar refeição -> evento -> consumer -> notificação criada (uma só, idempotente).
- Integração web (MockMvc ou equivalente do Spring Boot 4): login, troca de senha obrigatória, autorização por papel (matriz do RF-06), Problem Details.
- ArchUnit: regras hexagonais.
- JaCoCo: mínimo 80% em domain e application.

## Frontend
- Unitários: guards, interceptors, serviços, componentes principais (dashboard, formulário de refeição, diálogo de criação de usuário mostrando permissões).

## E2E (Playwright, contra docker compose)
Cenários: login admin + troca de senha; criar MEMBER; login do MEMBER + onboarding; registrar peso; registrar refeição que excede calorias e ver alerta; ver peso perdido e gráfico no dashboard; ADMIN vê menu Administração e MEMBER não.

## Critério de aceite
`./mvnw verify` verde, testes do frontend verdes, E2E verdes, compose saudável.
