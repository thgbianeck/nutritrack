---
description: Fase 3. Perfil do usuário e cálculo de metas.
agent: implementer
---
Execute a fase 3 de [plano](../../docs/08-plano-de-execucao.md).
Leia [domínio](../../docs/03-dominio-e-calculos.md) integralmente, [requisitos](../../docs/01-requisitos.md) (Perfil) e [API](../../docs/04-api-e-eventos.md) (Perfil). Use a skill nutrition-calc.
Implemente o contexto `profile`: perfil, serviços de domínio puros (IMC, idade, TMB, TDEE, meta calórica, macros, água, viabilidade da meta), `GET/PUT /profile` e `GET /profile/targets`.
Testes unitários parametrizados cobrindo todos os casos de `docs/03`. Rode `./mvnw -B verify`. Atualize `docs/PROGRESS.md`.
