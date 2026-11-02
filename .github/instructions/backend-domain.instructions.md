---
applyTo: "backend/src/main/java/**/domain/**"
---
# Camada de domínio: regras estritas

- Java puro. Proibido importar `org.springframework.*`, `jakarta.*`, `com.mongodb.*`, `org.apache.kafka.*`, `com.fasterxml.*`, `tools.jackson.*`.
- Modelos imutáveis sempre que possível (records). Entidades com identidade e comportamento (não anêmicas).
- Cálculos nutricionais e de IMC vivem em serviços de domínio puros, definidos em `docs/03-dominio-e-calculos.md`. Não altere fórmulas sem atualizar o documento.
- Exceções de domínio estendem uma `DomainException` própria (sem dependência de framework).
- Todo comportamento do domínio precisa de teste unitário sem Spring.