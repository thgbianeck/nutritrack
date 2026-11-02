---
applyTo: "backend/src/test/**"
---
# Backend: regras de teste

- Unitários (domínio e casos de uso): JUnit 5 + AssertJ + Mockito, sem contexto Spring, nomes `deve_<resultado>_quando_<condição>`.
- Integração: Testcontainers reais (MongoDB e Kafka). Use o suporte `@ServiceConnection` do Spring Boot 4 quando disponível; confirme módulos e coordenadas atuais do Testcontainers via Context7. Contêineres compartilhados entre classes (singleton) para acelerar.
- Testes de integração terminam com `IT` e rodam na fase `verify` (Failsafe). Unitários terminam com `Test` e rodam em `test` (Surefire).
- ArchUnit: teste que garante (1) domain não depende de Spring/Mongo/Kafka, (2) application não depende de adapter, (3) adapters não dependem uns dos outros.
- Cobertura mínima 80% em `domain` e `application` com JaCoCo; falhe o build abaixo disso.
- Kafka em teste: aguarde com Awaitility, nunca `Thread.sleep`.
- Dados de teste via builders/fixtures; nada de dependência de ordem entre testes.