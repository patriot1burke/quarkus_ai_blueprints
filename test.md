## Test AI Apps

Quarkus has a great [test harness](https://quarkus.io/guides/getting-started-testing) for testing any Quarkus-based application, but
testing interactions with the LLM can be a little tricky.
Since the output of your code's interactions with the LLM is non-deterministic, you will probably
get a different output even if you send in the same input every time.  So, how can you test your [AI Services](ai_services.md)?
Quarkus provides an [evaluation test harness](https://docs.quarkiverse.io/quarkus-langchain4j/dev/testing.html) you can use.

What you do is provide a set of sample inputs and expected outputs.  Quarkus then scores the output of your LLM
against the expected output.  If the score is above a certain threshold, Quarkus passes the test.

Here's a very simple example:

```java
@QuarkusTest
@Evaluate
public class WeathermanTest {

    @Inject
    Weatherman weatherman;

    @Test
    void repliesAreCloseEnoughToExpected(
            @ScorerConfiguration(concurrency = 3) Scorer scorer,
            @SampleLocation("src/test/resources/samples.yaml") Samples<String> samples) {

        EvaluationReport<String> report = scorer.evaluate(
                samples,
                params -> weatherman.ask(params.get(0)),
                new SemanticSimilarityStrategy(0.8));

        assertThat(report).hasScoreGreaterThan(70.0);
    }
}
```

`samples.yaml`:

```yaml
- name: Current Weather
  parameters:
    - "What is the current weather in San Diego?"
  expected-output: "It is sunny and the temperature is 72 degrees."
```
