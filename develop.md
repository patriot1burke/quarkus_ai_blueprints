# Develop

<details>
<summary>Enhancing Your Coding Agent</summary>

Coding agents like Claude Code, GitHub Copilot, and JetBrains AI have created an explosion in developer productivity.  There's a few
powerful features of Quarkus that make development a unique and enjoyable experience in day-to-day interaction with these tools.

* **Live Coding**. Have you ever coded with Node.js and seen code changes you make instantly be executable at runtime?  Quarkus supports
  this with the Java language and has for years.  Add coding agents and see your generated application come to life in real time.
* **Dev Services** Applications don't live on their own and often have to connect to a db or other external service to run.  Quarkus Dev Services
  have traditionally been used to automatically start up these services locally for you when you are developing and testing your applications.
  For AI Development, Quarkus Dev Services can automatically pull in and start up MCP Services, Vector DBs, and tools like LangFuse so you can
  develop, test, observe, evaluate, and play with your application, all locally.
* **Built-in Skills** Coding agents use [Skill files](https://agentskills.io/home) to figure out how to write good code based on a knowledge-base of experienced developers.
  Each Quarkus extension defines and publishes a Skill file that coding agents can use.  These skills define best practices and procedures for making the most
  out of each extension.
* **MCP Coding Agent** Coding agents interact with MCP Services to expand on what they can do.  For instance, Intellijs built-in MCP
  server allows the coding agent to query about the code of your project to find the classes and methods it needs to edit.  Quarkus
  also launches its own developer MCP service that publishes information, documentation, and skills about the extensions your Quarkus project is using.
  It was mentioned above that each extension defines its own Skill file.  The MCP Coding Agent is how Quarkus publises and exposes these
  skills with your favorite coding agent.

### Development Blueprint

Here's a [blueprint](https://quarkus.io/blog/introducing-agent-mcp/) for using Skills and MCP when developing any type of Quarkus application with a coding agent.

</details>
