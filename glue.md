# Glued Together with Quarkus

Every AI component — AI Services, Tools, RAG, agents — is a CDI bean, so the rest of Quarkus Core is never more than an `@Inject` away.
Components are discovered and auto-wired at build time.  All this makes writing AI applications feel like
a completely integrated experience and reviewing agent-generated code becomes much easier.

Some things to note:
* Chat Memory and Agentic Context lifecycle is [managed by CDI bean scope](https://docs.quarkiverse.io/quarkus-langchain4j/dev/messages-and-memory.html#_cdi_scope_and_memory_isolation)
* The LC4J `@MemoryId` concept can be managed by Quarkus so you don't have to do it yourself.
* Two new CDI scopes purpose-built for AI
  * `@ChatScope` to manage different LLM conversations
  * `@InvocationScope` for a single LLM interaction

