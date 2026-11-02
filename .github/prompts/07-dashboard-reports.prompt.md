---
description: Fase 7. Dashboard, relatórios e acompanhamento do nutricionista.
agent: implementer
---
Execute a fase 7 de [plano](../../docs/08-plano-de-execucao.md).
Leia [API](../../docs/04-api-e-eventos.md) (Dashboard, Relatórios, Acompanhamento) e [domínio](../../docs/03-dominio-e-calculos.md) (regras de peso, ritmo, projeção).
Implemente o contexto `dashboard`: consulta agregada de dashboard (peso perdido, IMC, progresso da meta, série com média móvel, consumo do dia, alertas, sequência, conquistas, projeção), relatório semanal, endpoints de membros vinculados com autorização por papel. Use projeções eficientes e índices para atender RNF-03.
Testes unitários. Rode `./mvnw -B verify`. Atualize `docs/PROGRESS.md`.
