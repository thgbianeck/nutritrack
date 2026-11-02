# NutriTrack: instruções globais

App de acompanhamento de peso, IMC, refeições e metas nutricionais. Idioma da UI e das mensagens: pt-BR. Código, commits e nomes técnicos: inglês.

## Stack
- Backend: Java 21, Spring Boot 4 (Spring Framework 7), Maven (wrapper), MongoDB, Kafka. Pasta `backend/`.
- Frontend: Angular (última versão estável), standalone components, Signals, Angular Material, Chart.js. Pasta `frontend/`.
- Infra: Docker Compose. Ordem de subida: mongodb + kafka (healthy) -> backend (healthy) -> frontend.
- Testes: JUnit 5, Mockito, AssertJ, ArchUnit, Testcontainers (MongoDB, Kafka); frontend com o test runner padrão do Angular; E2E com Playwright.

## Arquitetura
Hexagonal (Ports and Adapters). Dependências apontam sempre para dentro: adapter -> application -> domain. O domínio não importa Spring, Mongo, Kafka nem Jackson.

## Regras de trabalho
- Fontes da verdade: `docs/`. Leia só o documento relevante à tarefa. Não duplique o conteúdo deles no código ou no chat.
- Antes de usar API de biblioteca do ecossistema Spring Boot 4, Testcontainers ou Angular, confirme a assinatura atual via Context7 (MCP). Não assuma APIs do Spring Boot 3.
- Trabalhe por fases (`docs/08-plano-de-execucao.md`). Ao concluir uma fase: compile, rode os testes, atualize `docs/PROGRESS.md`.
- Não crie arquivos fora do escopo da fase. Não instale dependências sem necessidade.
- Segredos nunca no código: use variáveis de ambiente (`.env.example` documenta).
- Se faltar informação, faça a escolha mais simples e coerente com `docs/` e registre em `docs/PROGRESS.md` na seção "Decisões".
- Respostas no chat: curtas. Sem repetir código gerado; informe apenas arquivos criados e resultado dos testes.