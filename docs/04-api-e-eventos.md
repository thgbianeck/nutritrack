# API REST e eventos

Prefixo `/api/v1`. JSON. Datas ISO-8601 (`yyyy-MM-dd` para datas de calendário). Erros em Problem Details. Paginação (quando listar) com `page`, `size`.

## Autenticação
- POST /auth/login -> tokens + user + mustChangePassword
- POST /auth/refresh
- POST /auth/logout
- POST /auth/change-password (senha atual, nova senha)
- GET /me

## Usuários e papéis
- GET /roles (papéis com permissões e descrição em pt-BR)
- GET /users, POST /users, GET /users/{id}, PATCH /users/{id}
- PATCH /users/{id}/status (ativar/desativar)
- POST /users/{id}/reset-password
Somente ADMIN.

## Perfil
- GET /profile, PUT /profile (usuário autenticado)
- GET /profile/targets?date= (metas calculadas; inclui goalRealistic e suggestedGoalDate)

## Peso
- PUT /weights/{date} (upsert), DELETE /weights/{date}
- GET /weights?from=&to= (com IMC por registro)
- GET /weights/export (CSV)

## Alimentos
- GET /foods?query= (catálogo global + do usuário)
- POST /foods (alimento personalizado)

## Refeições e água
- POST /meals, GET /meals?date=, PUT /meals/{id}, DELETE /meals/{id}
- POST /meals/copy (fromDate, toDate)
- GET /meals/recent (últimas refeições distintas para registro rápido)
- POST /water (data, ml) e GET /water?date=
Respostas de escrita incluem `dailyStatus` (totais, metas e alertas do dia).

## Dashboard e relatórios
- GET /dashboard?date= retorna: usuário, peso inicial, peso atual, peso perdido/ganho, IMC atual e classificação, meta (peso, data, progresso percentual, projeção), série de peso e IMC (últimos 90 dias) com média móvel, consumo do dia (totais x metas x status por nutriente, água), alertas ativos, sequência, últimas conquistas.
- GET /reports/weekly?weekStart=

## Notificações
- GET /notifications?unreadOnly=, GET /notifications/unread-count
- PATCH /notifications/{id}/read, POST /notifications/read-all
(Frontend faz polling a cada 30 s.)

## Acompanhamento (NUTRITIONIST e ADMIN)
- GET /members (vinculados)
- GET /members/{id}/dashboard (somente leitura)

## Saúde
- GET /actuator/health (público) usado nos healthchecks.

## Eventos Kafka
Tópicos (3 partições, 1 réplica): `nutritrack.weight.recorded`, `nutritrack.meal.registered`, `nutritrack.water.registered`, `nutritrack.limit.exceeded`, e `<tópico>.dlt`.
Envelope: eventId (UUID), type, occurredAt (UTC), userId, payload. Chave da mensagem = userId (ordem por usuário). Serialização JSON.
Idempotência: ignorar eventId já processado.