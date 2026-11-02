# Plano de execução (fases)

Cada fase: implementar, compilar, testar, atualizar `docs/PROGRESS.md`. Só avance com tudo verde.

1. backend-foundation: pom, app, perfis, Problem Details, segurança base, ArchUnit, actuator.
2. identity: login, refresh, logout, troca de senha, seed do admin, CRUD de usuários, papéis e permissões.
3. profile-targets: perfil, serviços de domínio de cálculo (IMC, TMB, TDEE, metas), endpoint de metas.
4. tracking: peso e água (CRUD, IMC, export CSV).
5. nutrition: catálogo de alimentos com seed, refeições, cópia, recentes, status diário e alertas síncronos.
6. messaging-notifications: eventos Kafka, consumers idempotentes, DLT, notificações, conquistas, streak.
7. dashboard-reports: dashboard, relatório semanal, acompanhamento de nutricionista.
8. backend-tests: completar unitários e integrações com Testcontainers; JaCoCo.
9. frontend-foundation: projeto Angular, tema, layout, auth, guards, interceptors.
10. frontend-features-a: onboarding, perfil e metas, administração (com seletor de papel e permissões), pacientes.
11. frontend-features-b: peso, refeições, notificações.
12. frontend-dashboard: dashboard com gráficos e consumo diário, polimento de UX.
13. docker: Dockerfiles, nginx, compose, .env.example, README.
14. e2e-verify: Playwright, `docker compose up`, correção de falhas até ficar tudo verde.
