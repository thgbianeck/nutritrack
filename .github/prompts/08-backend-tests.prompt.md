---
description: Fase 8. Completar testes do backend com Testcontainers e cobertura.
agent: tester
---
Execute a fase 8 de [plano](../../docs/08-plano-de-execucao.md) seguindo [testes](../../docs/07-testes.md) (seção Backend).
Auditar lacunas, completar unitários e criar integrações com Testcontainers (MongoDB e Kafka reais), incluindo o fluxo refeição -> evento -> notificação e a matriz de autorização. Garanta JaCoCo com mínimo 80% em domain e application.
Docker deve estar rodando. Rode `cd backend && ./mvnw -B verify` e corrija até ficar verde. Atualize `docs/PROGRESS.md`.
