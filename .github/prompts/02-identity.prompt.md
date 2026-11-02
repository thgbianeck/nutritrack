---
description: Fase 2. Autenticação, usuários, papéis e permissões.
agent: implementer
---
Execute a fase 2 de [plano](../../docs/08-plano-de-execucao.md).
Leia [requisitos](../../docs/01-requisitos.md) (seção Autenticação e Usuários), [API](../../docs/04-api-e-eventos.md) (Autenticação e Usuários), [arquitetura](../../docs/02-arquitetura.md).
Implemente o contexto `identity` completo (domain, portas, casos de uso, adapters REST, Mongo e segurança): login, refresh rotacionado, logout, troca de senha, bloqueio por tentativas, seed do admin inicial com `mustChangePassword`, CRUD de usuários, `GET /roles`, matriz de permissões RF-06, regras RF-08.
Inclua testes unitários e de autorização por papel. Rode `./mvnw -B verify` e corrija. Atualize `docs/PROGRESS.md`.
