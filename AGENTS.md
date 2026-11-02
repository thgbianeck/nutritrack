# AGENTS.md

Projeto NutriTrack. Regras gerais em `.github/copilot-instructions.md`; especificações em `docs/`; regras por tecnologia em `.github/instructions/`.

## Comandos
- Backend build e testes: `cd backend && ./mvnw -B verify`
- Frontend instalar, build e testes: `cd frontend && npm ci && npm run build && npm test -- --watch=false`
- Subir tudo: `docker compose up --build`
- Derrubar e limpar volumes: `docker compose down -v`

## Definição de pronto
Build verde, testes verdes, ArchUnit verde, `docker compose up` saudável, `docs/PROGRESS.md` atualizado.