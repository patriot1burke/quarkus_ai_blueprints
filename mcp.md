
# Enterprise Tools with MCP

Microservices for AI.

Your organization has spent years writing microservices that analyze and report your company's data and implement the
processes of your organization.  Wouldn't it be cool to leverage these existing systems for use within an LLM?
The MCP specification defines a remote protocol for interacting with AI tools that are deployed remotely.  

Quarkus AI provides a way to define [your own MCP Server](https://docs.quarkiverse.io/quarkus-mcp-server/dev/index.html) to publish tools that can be used in any of your organization's
LLM applications. Think of MCP as microservices for AI.

![Description of the image](https://docs.quarkiverse.io/quarkus-mcp-server/dev/_images/main.png)

Defining your own MCP Server is as easy as this:

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




