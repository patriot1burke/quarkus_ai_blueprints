# LLM Tool Support

_Tools_ are functions you provide to the LLM during a chat request that the LLM can use to process a response.
The LLM looks at the user query and the list of functions you provide and decides whether or not it needs to 
pause text generation and call one of the functions to perform an action or to obtain more data.

Consider the _Weatherman_ AI Service example.  The LLM will not have information about the current weather, so what
you can that functionality to the LLM so it can answer queries successfully.

```java
@ApplicationScoped
public class WeatherAPIToolbox {
    // Pretend we have access to a Java weather API library that we can use!
    @Inject
    WeatherAPI weather;
    
    @Tool("Get the current weather for a specific location")
    public String currentWeather(String location) {
        return weather.currentForcast(location); 
    }
    
    @Tool("Get the 10 day weather forecast for a specific location")
    public List<String> tenDayForecast(String location) {
        return weather.tenDayForecast(location);
    }
}
```

Once you have your tools defined, you can just wire them into your AI Service.

```java


@RegisterAiService
public interface Weatherman {

    @SystemMessage("You are a weatherman.  Answer questions about the weather.")
    @Toolbox(WeatherAPIToolbox.class)
    String ask(@UserMessage String query);
}

```





