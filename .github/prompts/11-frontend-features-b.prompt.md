---
description: Fase 11. Peso, refeições e notificações no frontend.
agent: implementer
---
Execute a fase 11 de [plano](../../docs/08-plano-de-execucao.md).
Leia [frontend e UX](../../docs/05-frontend-ux.md) (Telas 5, 6, 8 e Feedback) e [API](../../docs/04-api-e-eventos.md) (Peso, Alimentos, Refeições, Água, Notificações).
Implemente: tela de peso (formulário rápido, histórico editável, gráfico, exportar CSV), tela de refeições (navegação por dia, agrupamento por tipo, busca com autocomplete, entrada manual, copiar de ontem, recentes), água, e central de notificações com contador e polling de 30 s. Ao salvar refeição ou água, exiba destaque visual quando `dailyStatus` trouxer EXCEEDED ou WARNING.
Testes unitários. Valide build e testes. Atualize `docs/PROGRESS.md`.
