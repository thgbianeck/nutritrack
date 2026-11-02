# Requisitos

## Autenticação e autorização
- RF-01 Admin inicial criado no primeiro start se não existir: e-mail `admin@nutritrack.local`, senha inicial vinda de `ADMIN_INITIAL_PASSWORD` (padrão de dev em `.env.example`: `Admin@12345`), flag `mustChangePassword=true`.
- RF-02 Enquanto `mustChangePassword=true`, a API só permite `change-password`, `me` e logout; o frontend bloqueia todas as rotas e redireciona para a tela de troca.
- RF-03 Política de senha: mínimo 8 caracteres, com maiúscula, minúscula, número e símbolo; nova senha diferente da atual.
- RF-04 Login retorna access token (15 min) e refresh token (7 dias, rotacionado, armazenado com hash). Logout revoga o refresh token.
- RF-05 Bloqueio temporário de 5 minutos após 5 tentativas de login inválidas.
- RF-06 Matriz de permissões:

  | Permissão | ADMIN | NUTRITIONIST | MEMBER |
  |---|---|---|---|
  | USER_MANAGE (criar/editar/desativar/redefinir senha) | sim | não | não |
  | OWN_DATA_WRITE (perfil, peso, refeições, água) | sim | não | sim |
  | OWN_DATA_READ | sim | não | sim |
  | LINKED_MEMBERS_READ (somente leitura dos vinculados) | sim (todos) | sim (vinculados) | não |
  | FOOD_CATALOG_MANAGE (editar catálogo global) | sim | sim | não |

- RF-07 `GET /api/v1/roles` retorna papéis e permissões para a UI exibir, no formulário de criação de usuário, uma descrição clara do que o papel selecionado pode acessar.
- RF-08 O ADMIN nunca pode desativar a si mesmo nem remover o último ADMIN ativo.

## Usuários e perfil
- RF-09 Cadastro de usuário pelo ADMIN: nome, e-mail, papel, senha temporária (gerada ou digitada), vínculo com nutricionista (opcional, para MEMBER). Novo usuário nasce com `mustChangePassword=true`.
- RF-10 Perfil do MEMBER/ADMIN: nome, sexo (FEMALE, MALE), data de nascimento, altura (cm), peso atual (kg), nível de atividade (SEDENTARY, LIGHT, MODERATE, HIGH, ATHLETE), peso-meta (kg), data-meta.
- RF-11 Alterar peso-meta ou data-meta recalcula as metas diárias imediatamente.

## Peso e IMC
- RF-12 Um registro de peso por usuário por dia (upsert por data). Datas futuras proibidas. Faixa válida 20 a 400 kg.
- RF-13 IMC = peso / altura². Classificações e cores em `docs/03-dominio-e-calculos.md`.
- RF-14 Peso perdido = peso inicial (primeiro registro) menos peso atual. Se o objetivo for ganho de peso, exibir "peso ganho" com a mesma lógica invertida.
- RF-15 O peso atual no perfil é sincronizado com o último registro de peso.

## Refeições e água
- RF-16 Refeição: data, tipo (BREAKFAST, LUNCH, DINNER, SNACK), itens (alimento do catálogo ou manual, quantidade, nutrientes calculados) e totais.
- RF-17 Registro manual de nutrientes sem catálogo é permitido.
- RF-18 Copiar refeições de um dia para outro.
- RF-19 Registro de água em ml (incrementos rápidos de 200 e 500 ml).

## Metas e alertas
- RF-20 Metas diárias calculadas conforme `docs/03`.
- RF-21 Ao registrar ou editar refeição/água, a resposta da API inclui os alertas atuais do dia (calculados de forma síncrona) para feedback imediato na UI.
- RF-22 Eventos Kafka alimentam notificações persistentes: no máximo 1 notificação por nutriente por nível (WARNING, EXCEEDED) por dia.
- RF-23 Dashboard conforme `docs/04` (endpoint de dashboard).

## Não funcionais
- RNF-01 `docker compose up --build` sobe tudo na ordem correta sem passos manuais.
- RNF-02 Todas as respostas de erro em Problem Details.
- RNF-03 Resposta do dashboard em menos de 500 ms com 1 ano de dados de um usuário.
- RNF-04 Índices MongoDB: `weights(userId, date)` único, `meals(userId, date)`, `users(email)` único, `notifications(userId, createdAt)`.
- RNF-05 Cobertura mínima de 80% em domain e application.