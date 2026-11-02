---
description: Fase 5. Alimentos, refeições, metas do dia e alertas síncronos.
agent: implementer
---
Execute a fase 5 de [plano](../../docs/08-plano-de-execucao.md).
Leia [requisitos](../../docs/01-requisitos.md) (Refeições, Metas e alertas), [domínio](../../docs/03-dominio-e-calculos.md) (Refeição, Classificação) e [API](../../docs/04-api-e-eventos.md) (Alimentos, Refeições).
Implemente o contexto `nutrition`: catálogo com seed de cerca de 60 alimentos brasileiros comuns (nutrientes por porção), alimentos personalizados, CRUD de refeições, cópia entre dias, recentes, cálculo de `dailyStatus` com alertas WARNING/EXCEEDED retornado nas escritas.
Testes unitários e de repositório. Rode `./mvnw -B verify`. Atualize `docs/PROGRESS.md`.
