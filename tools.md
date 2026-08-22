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

### Tools Blueprint

Best practices for writing LLM Tools.

</details>

