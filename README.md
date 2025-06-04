# 🌤️ Telegram Weather Alert Bot

A comprehensive weather bot for Telegram built with n8n that provides real-time weather updates, forecasts, severe weather alerts, and daily weather summaries.

![Bot Demo](assets/demo-screenshots/bot-demo.gif)

## 🚀 Features

- **Real-time Weather Updates** - Current conditions with detailed information
- **3-Day Forecasts** - Plan ahead with accurate weather predictions
- **Severe Weather Alerts** - Automatic notifications for dangerous conditions
- **Daily Weather Summaries** - Morning weather updates delivered to subscribers
- **Smart Recommendations** - Contextual advice (umbrella, jacket, sunscreen)
- **Multi-location Support** - Track weather for multiple cities
- **User-friendly Commands** - Simple and intuitive bot interactions

## 🛠️ Tech Stack

- **n8n** - Workflow automation platform
- **Telegram Bot API** - Bot interface and messaging
- **OpenWeatherMap API** - Weather data source
- **Google Sheets** - User data and preferences storage

## 📱 Bot Commands

| Command | Description |
|---------|-------------|
| `/start` | Register and start using the bot |
| `/location [city]` | Set your location |
| `/weather` | Get current weather conditions |
| `/forecast` | Get 3-day weather forecast |
| `/subscribe` | Enable daily weather updates |
| `/unsubscribe` | Disable daily updates |
| `/alerts` | Check active weather warnings |
| `/help` | Show all available commands |

## 🏃‍♂️ Quick Start

1. **Prerequisites**
   - n8n instance (self-hosted or cloud)
   - Telegram Bot Token
   - OpenWeatherMap API Key
   - Google Sheets access

2. **Setup**
   ```bash
   git clone https://github.com/yourusername/telegram-weather-alert-bot.git
   cd telegram-weather-alert-bot
