---
description: Fase 4. Registro de peso e água.
agent: implementer
---
Execute a fase 4 de [plano](../../docs/08-plano-de-execucao.md).
Leia [requisitos](../../docs/01-requisitos.md) (Peso, Água), [domínio](../../docs/03-dominio-e-calculos.md) (regras de peso) e [API](../../docs/04-api-e-eventos.md) (Peso, Água).
Implemente o contexto `tracking`: upsert por data, exclusão, listagem por intervalo com IMC, exportação CSV, água, sincronização do peso atual do perfil via porta, índices MongoDB, publicação do evento `weight.recorded` por porta de saída (adapter Kafka vem na fase 6; aqui use implementação a ser conectada, sem quebrar o build).
Testes unitários e de repositório. Rode `./mvnw -B verify`. Atualize `docs/PROGRESS.md`.
