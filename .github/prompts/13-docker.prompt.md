---
description: Fase 13. Dockerfiles, Nginx, Compose e README.
agent: implementer
---
Execute a fase 13 de [plano](../../docs/08-plano-de-execucao.md) seguindo [infra](../../docs/06-infra-e-docker.md).
Crie `backend/Dockerfile`, `frontend/Dockerfile`, `frontend/nginx.conf` (fallback SPA e proxy `/api`), `docker-compose.yml` com healthchecks e `depends_on: service_healthy` (mongodb + kafka -> backend -> frontend), `.env.example`, `.dockerignore` e um `README.md` curto com os comandos e credenciais iniciais de dev.
Valide: `cp .env.example .env && docker compose up --build -d` e aguarde todos os serviços saudáveis; teste `http://localhost:4200` e `http://localhost:8080/actuator/health`. Corrija até funcionar. Atualize `docs/PROGRESS.md`.
