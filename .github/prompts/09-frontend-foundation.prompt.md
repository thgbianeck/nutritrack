---
description: Fase 9. Fundação do frontend Angular.
agent: implementer
---
Execute a fase 9 de [plano](../../docs/08-plano-de-execucao.md).
Leia [frontend e UX](../../docs/05-frontend-ux.md) (Identidade, Navegação, Telas 1 e 2, Feedback) e [API](../../docs/04-api-e-eventos.md) (Autenticação).
Crie `frontend/` com Angular estável atual (confirme via Context7), Angular Material com tema claro/escuro, Chart.js via ng2-charts, layout com barra lateral/inferior responsiva, rotas lazy, serviço de auth, interceptors (JWT com refresh, erros Problem Details), guards (autenticação, papel, mustChangePassword), telas de login e troca obrigatória de senha, proxy de dev para `/api`.
Valide `npm run build` e `npm test -- --watch=false`. Atualize `docs/PROGRESS.md`.
