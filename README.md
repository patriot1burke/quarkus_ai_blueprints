# Quarkus AI
_Enterprise AI for Java_

Enhance your coding agent experience or create AI-infused applications.
Written for and by developers.  Coding still matters.

Quarkus has long been a great choice for creating any type of Java-based application.  Whether it be microservices, cloud-native, or even command-line 
utilties, Quarkus's ease of use, fast development lifecycle and performance brings nothing but developer joy.
So, what can Quarkus do for you when it comes to AI?

Firstly, Quarkus has top-notch support for coding agents like Claude Code, GitHub Copilot, Cursor, Windsurf, or JetBrains AI.
Quarkus has been remastered so that coding agents can figure out the best way to write a Quarkus-based application.
Quarkus tooling that runs out-of-the-box also enhances the interaction with your coding agents.

Secondly, as organizations move from using coding agents to writing production systems that leverage LLMs at runtime, Quarkus provides
all the libraries, frameworks, APIs, and services you need to make Java a first-class language for developing AI applications.  Furthermore, AI applications
aren't written in a vacuum.  They will need to leverage and integrate with regular systems and services.  Quarkus allows you to fuse
all your favorite Enterprise Java APIs and idioms you and your team have been using for years with these new AI technologies.



## Develop

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

## Write AI-Infused Applications

<details>
<summary> Basic AI Services </summary>
Talk about how Quarkus AI through LC4J provides an abstraction layer for basic LLM interactions.  List the LLM
models that are support (OpenAI, Ollama, Bob, etc.)

Talk about how basic LLM interactions can be defined via Java interfaces which are called AI Services

```java

@RegisterAiService
public interface Weatherman {
    
    @SystemMessage("You are a weatherman.  Answer questions about the weather.")
    String ask(@UserMessage String query);
}
```

### AI Services Blueprint
* Architectural diagram of LC4J->LLM interactions.  Should be simple.
* Link some basic practices for writing prompts with AI Services.
* [Managing Chat Memory](https://bill.burkecentral.com/2025/11/25/managing-chat-memory-in-quarkus-langchain4j/) Expand on this
to include the work done with Chat Scopes.

</details>

<details>
<summary>Create Tools usable with your LLM</summary>

Describe what tools are and how they work with the LLM.  Tell how Quarkus AI thru LC4J makes it
really easy to incorporate LLM tools with your AI-Infused applications.

```java
@ApplicationScoped
public class WeatherToolbox {
    @Inject
    WeatherAPI weather;
    
    @Tool("Get the current weather for a specific city")
    public String currentWeather(String city) {
        return weather.currentEither(city); 
    }
    
    @Tool("Get the 10 day weather forecast for a specific city")
    public List<String> tenDayForecast(String city) {
        return weather.tenDayForecastEither(city);
    }
}


@RegisterAiService
public interface Weatherman {

    @SystemMessage("You are a weatherman.  Answer questions about the weather.")
    @Toolbox(WeatherToolbox.class)
    String ask(@UserMessage String query);
}

```

### LLM Tools Blueprint

Best practices for writing LLM Tools.

</details>

<details>
<summary>Use and Publish Enterprise Toolboxes with MCP</summary>

Your organization has spent years writing microservices that analyze and report your company's data and implements the
processes of your organization.  Wouldn't it be cool to leverage these exisiing systems for use within an LLM?
The MCP specification defines a remote protocol for interacting with AI tools that are deployed remotely.  Quarkus
AI provides a way to define your own MCP Server to publish toolboxes and APIs to use these remote toolboxes in your AI-Infused applications.
Think of MCP as microservices for AI.

Show a simple example.

### Enterprise Toolbox Blueprint

Talk about discovery and all that fun stuff we used to talk about with a registry of microservices.  Its all the same shit over and over again.

</details>

<details>
<summary>Create Rich Chat Applications</summary>

Professional chat applications generally do a lot more than just display plain text to their human users.  The good
ones like to format information that comes from the LLM in a rich way, like what we're used to with traditional UIs.
Quarkus AI provides the architecture for writing Chat UIs via the [Chat Routes](https://docs.quarkiverse.io/quarkus-langchain4j/dev/chat-scopes.html#_chat_invocation_framework_chatroute) framework.
</details>

<details>
<summary>Information Retrieval and Analysis(RAG, and other techniques)</summary>

Talk about basic RAG.  Give brief reason that Quarkus AI is a good fit for RAG.

### RAG Blueprint
Ingestion - basic and docling
Vector DBs

### Advanced Rag Pipeline Blueprint

### LLM Wiki Blueprint

</details>

<details>
<summary>Define Agentic Workflows</summary>

Most of this website has talked about human-LLM interactions.  Once you get beyond chat apps and RAG you'll want to 
truly leverage AI by unleashing agents.  Agentic AI Applications encapsulate complex processes and procedures by using
AI agents that perform the work.

Show basic agents quickly.  Quicker than LC4J docs, or just link to existing docs..
Talk about how these agents leverage AI Services and the rest of the Quarkus ecosystem of enterprise Java.

### Agentic Blueprints

Architectural diagram on Agentic Workflows

* Link to Workflow Plans


</details>

<details>
<summary>Guardrails</summary>

AI guardrails are safety controls, filters, and rules that sit between a user and an artificial intelligence model. 
They intercept inputs and outputs in real time to ensure the system behaves safely, stays on topic, and complies with legal or brand standards
without changing the core model.


Architectural diagram on Guardrails

Talk about how Quarkus AI provides a library of built-in guardrails you can use, and an API for writing and applying your own guardrails.



</details>

<details>
<summary>Glue it together with Quarkus Core</summary>

Every AI component (AI Services, Tools, RAG, etc.) is integrated as a CDI bean with Quarkus Core.  

### CDI Scopes Blueprint

* Chat Memory lifecycle managed by bean scope
* Agentic Context lifecycle managed by bean scope
* CDI injects 
* Easy to wire things in.
* New CDI scopes that cover more AI use cases
** `@ChatScope` defines a conversation scope.
** `@InvocationScope` defines a per invocation scope.

</details>

<details>
<summary>Leverage Enterprise Java</summary>

You're building AI Services, Tools, and Agents as CDI Beans.  This means you have access to the entire Quarkus ecosystem.
Quarkus has extensions for everything:  Hibernate, Kaftka, REST, etc.)

</details>

## Test

<details>
<summary>Test your AI-Infused Apps</summary>

Show evaluation APIs Quarkus has for testing purposes.

</details>

## Secure

<details>
<summary>Secure your AI-Infused Applications</summary>

Talk about how core Quarkus has mature security integration and how just writing a Quarkus AI-infused application inherits
security from the core.

### Security Blueprint
Architectural diagram on how various components are secured.

Show how chat apps and MCP are secured.

</details>

## Deploy

<details>
<summary>Deploy your AI-Infused Apps</summary>

Talk about how Quarkus has always been a cloud-native framework and that it has out-of-the-box support
for deploying to Kubernetes, OpenShift, AWS, and Azure.

</details>

## Evaluate and Score

<details>
<summary>Top-knotch evaluation and scoring with LangFuse</summary>

</details>

## Monitor

<details>
<summary>Top-knotch telemetry with LangFuse</summary>

</details>



















