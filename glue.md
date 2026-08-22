# Glued Together with CDI

Every AI component — AI Services, Tools, RAG, agents — is a CDI bean, so the rest of Quarkus Core is never more than an @Inject away.

* Chat Memory lifecycle managed by bean scope
* Agentic context lifecycle managed by bean scope
* Plain CDI injection wires it all together
* Two new CDI scopes purpose-built for AI
  * `@ChatScope` to manage different LLM conversations
  * `@InvocationScope` for a single LLM interaction

