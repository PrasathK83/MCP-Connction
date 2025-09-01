# MCP-Connction
I have connected my weather bot with claude through the MCP Connection

## Install Claude desktop and sign in

## MCP Weather Bot – Claude Desktop Integration

This repository demonstrates how to connect a custom **Model Context Protocol (MCP)** server with **Claude Desktop** using Python. It provides a simple **Weather Bot** tool that fetches real-time weather information from the **OpenWeather API** and makes it accessible to Claude through MCP.

### How It Works

* **MCP (Model Context Protocol):** An open standard that allows external tools, data sources, and APIs to integrate with AI models like Claude.
* **Claude Desktop:** Anthropic’s desktop client for Claude that supports MCP tool integration.
* **FastMCP:** A Python framework used to quickly build and run MCP servers with minimal boilerplate.

This project defines a weather tool that Claude can call through MCP. Users can ask Claude for current weather conditions in any city, and the tool will return:

* Weather condition (e.g., cloudy, sunny, rain)
* Temperature (°C, with “feels like” value)
* Humidity percentage

### Setup Instructions

1. Clone this repository.

2. Install dependencies:

   ```bash
   pip install requests python-dotenv fastmcp
   ```

3. Create a `.env` file in the project root:

   ```
   OPENWEATHER_API_KEY=your_api_key_here
   ```

   You can obtain an API key from [OpenWeather](https://openweathermap.org/api).

4. Run the MCP server:

   ```bash
   python weather_bot.py
   ```

5. Configure Claude Desktop to load this MCP server by editing `claude_desktop_config.json` (usually found in Claude’s settings directory). Example entry:

   ```json
   {
     "mcpServers": {
       "weather-bot": {
         "command": "python",
         "args": ["path/to/weather_bot.py"]
       }
     }
   }
   ```

6. Restart Claude Desktop. Now you can query Claude:

   > “What’s the weather in London?”

Claude will call the MCP tool and return live weather information.

### File Structure

```
├── weather_bot.py     # Main MCP server script
├── .env               # Environment variables (API key)
├── requirements.txt   # Dependencies
└── README.md          # Project documentation
```

### Key Technologies

* **Python 3.8+**
* **FastMCP** for MCP server creation
* **Requests** for API calls
* **dotenv** for environment configuration
* **Claude Desktop** for MCP client integration

### Extending the Project

You can extend this MCP server to:

* Support **forecast data** (5-day or hourly forecast).
* Fetch **air quality index (AQI)**.
* Add **geolocation-based weather lookup**.
* Integrate **multiple APIs** (e.g., AccuWeather, WeatherAPI).
