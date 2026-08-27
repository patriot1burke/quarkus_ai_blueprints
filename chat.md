## Create Rich Chat Applications

Professional chat applications generally do a lot more than just display plain text to their human users.  The good
ones like to format information that comes from the LLM in a rich way, like what we're used to with traditional UIs.
Quarkus AI provides the architecture for writing Rich Chat UIs via the [Chat Routes](https://docs.quarkiverse.io/quarkus-langchain4j/dev/chat-scopes.html#_chat_invocation_framework_chatroute) framework.

Chat Routes provides a websocket protocol so that your UI clients can interact with your [AI Services](#tile-ai-services)
Simply annotation your AI Service methods with `@ChatRoute` and you're good to go.

```java
@RegisterAiService
public interface Weatherman {
    
    @SystemMessage("You are a weatherman.  Answer questions about the weather.")
    @ChatRoute("weather-man")
    String ask(@UserMessage String query);
}
```

Chat Routes provides a Java and Javascript client API that allows you to send chat messages to your chat-routed AI Services.

```javascript
client = new ChatScopesClient();
await client.open("ws://localhost:8080/_chat/routes");

builder = client.builder();
session = await builder.connect("weather-man");

session.chat("What's the weather like in San Francisco?");
```

The Chat Routes framework also allows your server to send back messages to your clients.  This is really useful from tool
methods when you want to render something specific on the client, or to send thinking messages back to the chat UI.

```java
@ApplicationScoped
public class WeatherAPIToolbox {
    // Pretend we have access to a Java weather API library that we can use!
    @Inject
    WeatherAPI weather;
    
    @Inject
    ChatRouteContext ctx;
    
    @Tool("Get the current weather for a specific location")
    public String currentWeather(String location) {
        // Send back a thinking message for chat UI to render while we wait for the API call to complete
        ctx.thinking("Calling out to the national weather service for current forecast");
        Forecast forecast = weather.currentForcast(location); 
        if (forecast.type == RAIN) {
            // have chat client render a RAIN icon
            ctx.event("weather-alert", RAIN);
        }
        return forecast.text();
    }
 
}
```


