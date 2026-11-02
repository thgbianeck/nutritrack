---
applyTo: "frontend/**/*.spec.ts,frontend/e2e/**"
---
# Frontend: regras de teste

- Unitários com o test runner padrão do projeto Angular gerado. Teste componentes pelo comportamento (DOM e Signals), serviços com `HttpTestingController`.
- Mock de HTTP sempre; nada de chamar o backend real em unitário.
- E2E com Playwright em `frontend/e2e`, rodando contra `docker compose up`. Seletores por papel/label/`data-testid`, nunca por classe CSS.
- Cenários E2E mínimos: login admin + troca de senha obrigatória; criar usuário; registrar peso; registrar refeição que excede o limite e ver o alerta; ver o dashboard.