<details>
<summary>Define Agentic Workflows</summary>

Agentic Workflows allow you to encapsulate the complex processes and procedures of your business.
To implement your process, you will have a combination of AI Agents, traditional enterprise coding,
and human-in-the-loop interactions.  Agentic Workflows provide the foundation to define and implement
the interactions between all of these components.  These workflows can be long-running, asynchronous,
and can store state as needed.  Quarkus AI provides the means for defining and implementing [Agentic Workflows](https://docs.langchain4j.dev/tutorials/agents).

```java
public interface CreativeWriter {

    @UserMessage("""
            You are a creative writer.
            Generate a draft of a story no more than
            3 sentences long around the given topic.
            Return only the story and nothing else.
            The topic is {{topic}}.
            """)
    @Agent("Generates a story based on the given topic")
    String generateStory(@V("topic") String topic);
}
```

Agents can generate output and except input from both other agents and humans.  Agent workflows have similar
constructs to traditional workflow definition too, such as:
* [Sequential workflows](https://docs.langchain4j.dev/tutorials/agents#sequential-workflow)
* [Loops](https://docs.langchain4j.dev/tutorials/agents#loop-workflow)
* [Conditionals](https://docs.langchain4j.dev/tutorials/agents#conditional-workflow)
* [Parallel execution](https://docs.langchain4j.dev/tutorials/agents#parallel-workflow)
* [Human-in-the-loop interactions](https://docs.langchain4j.dev/tutorials/agents#human-in-the-loop)

The API also supports defining your own custom workflow patterns and steps.  Some pre-defined patterns
also have abstractions you can derive from:
* [Goal oriented](https://docs.langchain4j.dev/tutorials/agents#goal-oriented-agentic-pattern) pattens
* [Peer-to-peer](https://docs.langchain4j.dev/tutorials/agents#peer-to-peer-agentic-pattern)
* [Blackboard](https://docs.langchain4j.dev/tutorials/agents#blackboard-agentic-pattern)
* [Voting](https://docs.langchain4j.dev/tutorials/agents#voting-agentic-pattern)
* [Belief-Desire-Intention](https://docs.langchain4j.dev/tutorials/agents#belief-desire-intention-bdi-agentic-pattern)

Check out the [documentation](https://docs.langchain4j.dev/tutorials/agents) for all the other features supported.


</details>