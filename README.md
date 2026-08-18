# Quarkus AI

Quarkus has long been a great choice for creating any type of Java-based application.  Whether it be microservices, cloud-native,
terminal applications, or even command-line utilties Quarkus's ease of use, fast development lifecycle and performance is unmatched when writing.
With AI, Quarkus and Java are the perfect destination for your current and newer projects.  

Firstly, Quarkus has top-notch support for coding agents.
agents.  Writing any application using Claude Code, GitHub Copilot, Cursor, Windsurf, and JetBrains AI is a completely enhanced experience
when using Quarkus.  Out-of-the-box and completely open source, Quarkus dev mode launches dev services that allow these coding agents
to write better code faster.

Secondly, as organizations move from using coding agents to writing production systems that leverage LLMs at runtime, Quarkus provides
all the libraries, frameworks, APIs, and services you need making Java a first-class language for developing AI applications.  AI applications
aren't written in a vacuum.  They will need to leverage and integrate with regular systems and services.  Quarkus allows you to fuse
all your favorite Enterprise Java APIs and idioms you and your team have been using for years with these new AI technologies.


## Development with Coding Agents

Coding agents like Claude Code, GitHub Copilot, and JetBrains AI have created an explosion in developer productivity.  There's a few
powerful features of Quarkus that make development a unique and enjoyable experience in day-to-day coding tasks.

<details>
<summary></summary>

* **Live Coding**. Have you ever coded with Node.js and seen code changes you make instantly be executable at runtime?  Quarkus supports
this with the Java language and has for years.  Add in coding agents and see your generated application come to life in real time.
* **Dev Services** Applications don't live on their own and often have to connect to a db or other external service to run.  Quarkus Dev Services
have traditionally been used to automatically start up these services locally for you when you are developing and testing your applications.
For AI Development, Quarkus Dev Services can automatically pull in and start up MCP Servicers, Vector DBs, and tools like LangFuse so you can
develope, test, observe and play with your application all locally.
* **Skills** Coding agents use [Skill files](https://agentskills.io/home) to figure out how to write good code based on the knowledge-base of experienced developers.
Each Quarkus extension defines and publishes a Skill file that coding agents can use.  They define best practices and procedures for making the most
out of the extension.
* **MCP Coding Agent** Coding agents interact with MCP Services to expand on what they can do.  For instance, Intellijs built-in MCP
server allows the coding agent to query about the code of your project to find the classes and methods it needs to edit.  Quarkus
also launches its own MCP services that publishes information and skills of the extensions your Quarkus project is using.  Here's a great article
describing how [Quarkus uses Skills and MCP](https://quarkus.io/blog/introducing-agent-mcp/) to help coding agents.

</details>

