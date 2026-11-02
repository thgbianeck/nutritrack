---
description: Fase 14. E2E com Playwright e verificação final.
agent: tester
---
Execute a fase 14 de [plano](../../docs/08-plano-de-execucao.md) seguindo [testes](../../docs/07-testes.md) (seção E2E).
Com `docker compose up` rodando, use o Playwright MCP para explorar a UI e depois crie a suíte E2E em `frontend/e2e` com os cenários listados. Corrija defeitos encontrados (frontend, backend ou compose) com mudanças mínimas e registre em `docs/PROGRESS.md`.
Fim: rode `docker compose down -v && docker compose up --build -d`, a suíte E2E, `./mvnw -B verify` e os testes do frontend. Todos devem passar.
