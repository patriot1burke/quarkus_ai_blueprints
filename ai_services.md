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