# Cardea Weather MCP Server

The Cardea Weather MCP Server provides weather data from [OpenWeatherMap.org](https://openweathermap.org/) to MCP clients. It supports two transport types: `stream-http` and `sse`.

## Tools

- **get_current_weather**
  - Get the weather for a given city
  - Input parameters:
    - `location`: The city to get the weather for, e.g., "Beijing", "New York", "Tokyo".
    - `unit`: The unit to use for the temperature, e.g., "celsius", "fahrenheit". Default is "celsius".
  - Returns the current weather information for the given city, including temperature, humidity, weather condition, etc.

## Build

```bash
# build mcp server
cargo build --release
```

## Run

> [!IMPORTANT]
>
> The mcp server will use the `OPENWEATHERMAP_API_KEY` environment variable to get the weather data from [OpenWeatherMap.org](https://openweathermap.org/). If you don't have an API key, you **SHOULD** apply one from [OpenWeatherMap.org](https://openweathermap.org/) and set it by running the following command:
>
> ```bash
> export OPENWEATHERMAP_API_KEY=<your-api-key>
> ```

Now, let's start the mcp server. You can choose to start the server with different transport types by specifying the `--transport` CLI option. The default transport type is `stream-http`. In addition, you can also specify the socket address to bind to by specifying the `--socket-addr` CLI option. The default socket address is `127.0.0.1:8002`.

```bash
# run mcp server (stream-http)
./target/release/cardea-weather --transport stream-http

# run mcp server (sse)
./target/release/cardea-weather --transport sse
```

If start successfully, you will see the following output:

```bash
Cardea Weather MCP Server is listening on 127.0.0.1:8002
```
