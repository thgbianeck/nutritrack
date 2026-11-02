---
description: Fase 6. Kafka, notificações, conquistas e streak.
agent: implementer
---
Execute a fase 6 de [plano](../../docs/08-plano-de-execucao.md).
Leia [arquitetura](../../docs/02-arquitetura.md) (Fluxo assíncrono), [API](../../docs/04-api-e-eventos.md) (Eventos e Notificações) e [domínio](../../docs/03-dominio-e-calculos.md) (Conquistas, Sequência).
Implemente: publicador Kafka (adapter out), criação dos tópicos, consumers idempotentes com retry e DLT, contexto `notification` (notificações e conquistas), regra de no máximo 1 notificação por nutriente e nível por dia, endpoints de notificações. Conecte os eventos das fases 4 e 5.
Confirme configuração do Spring Kafka no Boot 4 via Context7. Testes unitários; os de Testcontainers vêm na fase 8. Rode `./mvnw -B verify`. Atualize `docs/PROGRESS.md`.
