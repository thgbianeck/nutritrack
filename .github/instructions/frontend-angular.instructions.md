---
applyTo: "frontend/src/**/*.{ts,html,scss,css}"
---
# Frontend Angular: regras

- Angular standalone (sem NgModules), `ChangeDetectionStrategy.OnPush`, Signals para estado local, `inject()` em vez de construtor, controle de fluxo nativo (`@if`, `@for`, `@switch`), `input()`/`output()`.
- Estrutura: `src/app/core` (auth, interceptors, guards, serviços globais), `src/app/shared` (componentes reutilizáveis, pipes), `src/app/features/<feature>` (rotas com lazy loading).
- UI: Angular Material (tema customizado, modo claro/escuro) + Chart.js (via ng2-charts) para gráficos. Layout responsivo mobile-first.
- Formulários reativos tipados. Mensagens de validação em pt-BR, claras e junto ao campo.
- HTTP: serviços por feature, interceptors para JWT (anexar token, renovar com refresh, redirecionar ao login em 401) e para erros (snackbar com mensagem do Problem Details).
- Guards por papel e por `mustChangePassword` (força troca de senha antes de qualquer rota).
- Acessibilidade: labels, contraste AA, foco visível, `aria-*` em gráficos (resumo textual alternativo).
- Estados de UX obrigatórios em toda tela de dados: carregando (skeleton), vazio (ilustração + ação), erro (mensagem + tentar de novo).
- Locale pt-BR (datas, números, moeda não se aplica). Nada de textos hardcoded espalhados: centralize rótulos repetidos em constantes.
- Sem `any`. TypeScript estrito.
- Detalhes de UX: `docs/05-frontend-ux.md`.