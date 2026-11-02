---
applyTo: "backend/src/main/**"
---
# Backend Java: regras

- Java 21: records para DTOs/Value Objects/eventos, sealed interfaces quando fizer sentido, pattern matching, `var` com moderação.
- Pacote raiz `com.nutritrack`. Organização feature-first, depois camadas: `<contexto>/domain`, `<contexto>/application/{port/in,port/out,usecase}`, `<contexto>/adapter/{in/rest,in/messaging,out/persistence,out/messaging,out/security}`. Contextos: identity, profile, tracking, nutrition, notification, dashboard. Configuração transversal em `com.nutritrack.bootstrap`.
- Injeção por construtor. Sem `@Autowired` em campos. Sem Lombok.
- Casos de uso: uma interface em `port/in` por caso de uso, implementada em `usecase`. Anotação `@Service` somente no pacote `usecase` ou em classes de bootstrap.
- Controllers só convertem HTTP <-> comando/consulta e chamam portas de entrada. Nada de regra de negócio.
- Documentos MongoDB e DTOs REST são classes distintas do modelo de domínio; mapeie explicitamente (mappers manuais ou MapStruct, escolha um e mantenha).
- Validação de entrada com Jakarta Validation nos DTOs REST. Invariantes de negócio no domínio, lançando exceções de domínio.
- Erros HTTP no formato Problem Details (RFC 9457) com handler global; mensagens em pt-BR.
- Segurança: Spring Security stateless, JWT (access + refresh), BCrypt, autorização por papel e `@PreAuthorize` nas portas de entrada ou controllers.
- Logs com SLF4J, sem dados sensíveis (senha, token).
- Configuração via `application.yml` + variáveis de ambiente. Perfis: `default` (dev), `test`.
- Datas: `java.time`; persistir instantes em UTC; datas de calendário (peso, refeição) como `LocalDate` no fuso `America/Sao_Paulo`.