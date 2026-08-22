## Secure your AI Applications

[Quarkus Security](https://quarkus.io/guides/security-overview) has provided the features developers need to secure their Enterprise Java applications.
Securing secrets, authentication protocols like OAuth2 and OIDC, and role-based access control among many other features
have been available and mature for years within Quarkus.

AI-infused applications are generally built on top of the same protocols as traditional web applications and services so
to secure them, just leverage what's there right now.  Here's a few samples:

* [Securing a Chat Bot](https://github.com/quarkiverse/quarkus-langchain4j/tree/main/samples/secure-sql-chatbot)
* [Securing an MCP client and server](https://github.com/quarkiverse/quarkus-langchain4j/tree/main/samples/secure-mcp-client-server)

AI Applications introduce a few more security vulnerabilities you need to be aware of.  The Quarkus team
has put together a [blueprint](https://docs.quarkiverse.io/quarkus-langchain4j/dev/security.html) dealing with these vulnerabilities.

[Guardrails](https://docs.quarkiverse.io/quarkus-langchain4j/dev/guardrails.html) are also an important part of this.
