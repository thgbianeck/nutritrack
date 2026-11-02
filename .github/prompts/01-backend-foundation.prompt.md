---
description: Fase 1. Fundação do backend (Spring Boot 4, Java 21, hexagonal).
agent: implementer
---
Execute a fase 1 de [plano](../../docs/08-plano-de-execucao.md).
Leia [arquitetura](../../docs/02-arquitetura.md) e [infra](../../docs/06-infra-e-docker.md) (apenas variáveis).
Entregue em `backend/`: projeto Maven com wrapper, Java 21, Spring Boot 4 (confirme versão estável atual e starters via Context7), dependências para web, validation, security, data-mongodb, kafka, actuator, testes e Testcontainers, JaCoCo, Surefire/Failsafe; `application.yml` com perfis; handler global Problem Details; configuração de segurança base stateless; esqueleto de pacotes por contexto; teste ArchUnit das regras hexagonais.
Valide: `cd backend && ./mvnw -B verify`. Atualize `docs/PROGRESS.md`.
