---
applyTo: "**/Dockerfile,**/docker-compose*.yml,**/nginx*.conf,.env.example"
---
# Docker e infraestrutura

- Dockerfiles multi-stage, imagens base oficiais com tag fixa (nunca `latest`), usuário não-root no runtime.
- Backend: build Maven em um estágio, runtime JRE 21 enxuto. Frontend: build Node em um estágio, Nginx servindo estáticos com fallback SPA e proxy reverso de `/api` para o backend.
- Compose com `healthcheck` em mongodb, kafka e backend; `depends_on` com `condition: service_healthy` garantindo a ordem: mongodb + kafka -> backend -> frontend.
- Kafka em modo KRaft (sem Zookeeper), nó único. Tópicos criados pela aplicação (`NewTopic`) ou por job de init, nunca manualmente.
- Volumes nomeados para dados do MongoDB. Rede interna dedicada.
- Toda configuração por variáveis de ambiente com padrões seguros para dev em `.env.example`. Nunca commitar `.env`.
