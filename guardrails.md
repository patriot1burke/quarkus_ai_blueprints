# Guardrails

AI guardrails are safety controls, filters, and rules that sit between a user and an artificial intelligence model.
They intercept inputs and outputs in real time to ensure the system behaves safely, stays on topic, and complies with legal or brand standards
without changing the core model.

Quarkus AI supports both input and output guardrails.  Input guardrails are used to catch things like prompt injection attacks
or out-of-scope questions.  Output Guardrails can be used to anonymize or redact sensitive information returned from an LLM response.

![Guardrails architecture](https://docs.langchain4j.dev/img/guardrails-light-bg.png)


## A Simple Example

Here's a minimal input guardrail that rejects blank messages before they ever reach the model:

```java
public class NotBlankGuardrail implements InputGuardrail {

    @Override
    public InputGuardrailResult validate(UserMessage userMessage) {
        if (userMessage.singleText().isBlank()) {
            return failure("Message cannot be blank");
        }
        return success();
    }
}
```

Wire it into an AI Service with the `@InputGuardrails` annotation:

```java
public interface Weatherman {

    @SystemMessage("You are a weatherman.  Answer questions about the weather.")
    @InputGuardrails(NotBlankGuardrail.class)
    String ask(@UserMessage String query);
}
```





