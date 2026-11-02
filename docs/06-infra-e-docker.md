# Infraestrutura e Docker

## Serviços (docker-compose.yml na raiz)
1. mongodb: imagem oficial com tag fixa; volume nomeado; healthcheck por ping com mongosh.
2. kafka: imagem oficial Apache Kafka em modo KRaft, nó único; healthcheck listando a API do broker; listener interno para os contêineres.
3. backend: build de `backend/Dockerfile`; depende de mongodb e kafka com `condition: service_healthy`; healthcheck em `/actuator/health` com `start_period` generoso.
4. frontend: build de `frontend/Dockerfile`; Nginx; depende do backend `service_healthy`; publica `4200:80`; proxy `/api` -> `http://backend:8080`.

## Ordem garantida
mongodb + kafka (healthy) -> backend (healthy) -> frontend.

## Portas
Frontend 4200 (publicada), backend 8080 (publicada para depuração), mongodb e kafka apenas na rede interna (portas de depuração opcionais comentadas).

## Variáveis (.env.example)
ADMIN_INITIAL_PASSWORD, JWT_SECRET (mínimo 32 caracteres; valor de dev no exemplo), JWT_ACCESS_MINUTES, JWT_REFRESH_DAYS, MONGODB_URI e nome do banco, KAFKA_BOOTSTRAP_SERVERS, TZ=America/Sao_Paulo. Os nomes das propriedades Spring correspondentes devem ser confirmados na documentação do Spring Boot 4 (Context7) e mapeados em `application.yml`.

## Resultado esperado
`cp .env.example .env && docker compose up --build` -> http://localhost:4200 abre o login; admin inicial entra com `admin@nutritrack.local` e a senha de `.env`, e é forçado a trocá-la.
