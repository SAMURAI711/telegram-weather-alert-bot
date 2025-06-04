### docs/setup-guide.md

# 📖 Complete Setup Guide

This guide will walk you through setting up the Telegram Weather Alert Bot step by step.

## Prerequisites

Before you begin, make sure you have:

- [ ] n8n instance (self-hosted or cloud)
- [ ] Telegram account
- [ ] Google account
- [ ] Basic understanding of n8n workflows

## Step 1: Create Telegram Bot

1. **Open Telegram** and search for `@BotFather`
2. **Start conversation** and send `/newbot`
3. **Follow the prompts**:
   - Bot name: "Weather Alert Bot"
   - Username: "your_weather_alert_bot"
4. **Save the bot token** - you'll need it later
5. **Set bot commands** by sending `/setcommands` to BotFather:
   ```
   start - Start the bot
   weather - Get current weather
   forecast - Get 3-day forecast
   location - Set your location
   subscribe - Enable daily updates
   unsubscribe - Disable daily updates
   alerts - Check active weather alerts
   help - Show all commands
   ```

## Step 2: Get Weather API Key

1. **Visit** [OpenWeatherMap](https://openweathermap.org/api)
2. **Sign up** for a free account
3. **Navigate** to the API keys section
4. **Copy your API key** - Free tier includes:
   - 60 calls/minute
   - 1,000,000 calls/month
   - Current weather data
   - 5-day forecast

## Step 3: Setup Google Sheets Database

1. **Create new Google Sheet** named "Weather Bot Database"
2. **Create Sheet 1: "Users"** with columns:
   ```
   A: user_id | B: username | C: first_name | D: location | E: lat | F: lon | G: subscribed | H: timezone | I: last_active
   ```
3. **Create Sheet 2: "Weather_Logs"** with columns:
   ```
   A: timestamp | B: user_id | C: location | D: weather_data | E: alert_type
   ```
4. **Share the sheet** with your Google account
5. **Enable API access** in Google Cloud Console
6. **Get the Sheet ID** from the URL

## Step 4: Import n8n Workflows

1. **Download workflow files** from the `n8n-workflows/` folder
2. **Open your n8n instance**
3. **Import each workflow**:
   - `main-handler.json` - Main bot workflow
   - `daily-broadcast.json` - Daily weather updates
   - `alert-monitor.json` - Severe weather monitoring

## Step 5: Configure Workflows

### Main Handler Workflow

1. **Telegram Trigger Node**:
   - Add your bot token to credentials
   - Set update types to "Message"

2. **Google Sheets Nodes**:
   - Configure Google Sheets credentials
   - Set your Sheet ID in all Google Sheets nodes

3. **HTTP Request Nodes**:
   - Add your OpenWeatherMap API key to all weather API calls

### Daily Broadcast Workflow  

1. **Cron Trigger**:
   - Set to run daily at 7:00 AM
   - Adjust timezone as needed

2. **Configure all API keys and credentials** as above

### Alert Monitor Workflow

1. **Cron Trigger**:
   - Set to run every 30 minutes
   - Adjust frequency based on your needs

2. **Configure all API keys and credentials** as above

## Step 6: Test Your Bot

1. **Start all workflows** in n8n
2. **Test each command**:
   - Send `/start` to your bot
   - Set location with `/location London`
   - Try `/weather` and `/forecast`
   - Test subscription with `/subscribe`

3. **Check data storage**:
   - Verify user data appears in Google Sheets
   - Confirm API calls are working

## Step 7: Deploy and Monitor

1. **Enable all workflows**
2. **Set up monitoring**:
   - Check n8n execution logs
   - Monitor API usage
   - Track user engagement

3. **Configure error handling**:
   - Add error nodes to workflows
   - Set up notifications for failures

## Troubleshooting

### Common Issues

**Bot not responding:**
- Check bot token is correct
- Verify Telegram webhook is active
- Ensure n8n workflow is running

**Weather data not loading:**
- Verify OpenWeatherMap API key
- Check API rate limits
- Confirm internet connectivity

**Database errors:**
- Verify Google Sheets credentials
- Check sheet ID is correct
- Ensure proper permissions

**Daily updates not sending:**
- Check cron trigger settings
- Verify timezone configuration
- Ensure users are subscribed
