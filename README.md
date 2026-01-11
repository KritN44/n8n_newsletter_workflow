# n8n_newsletter_workflow
Created a newsletter workflow that works through a bot prompt on Slack


# AI Newsletter Workflow for n8n

An automated newsletter system that fetches the latest news on any topic and distributes it via email and Slack.

## Features

- 🤖 **Slack Integration** - Mention the bot to trigger newsletter generation
- 📰 **News Fetching** - Pulls top 10 articles from GNews API
- ✨ **AI-Powered** - Uses GPT-4 to generate beautiful HTML newsletters
- 📧 **Email Distribution** - Sends formatted newsletters to recipients
- 💬 **Slack Updates** - Posts article summaries back to Slack channel

## How It Works

1. **Trigger**: Mention the bot in Slack with a topic
```
   @newsletter_bot Alert: Get the latest news about Donald Trump
```

2. **Fetch**: Retrieves latest news articles from GNews API

3. **Generate**: GPT-4 creates a professional HTML newsletter

4. **Distribute**: 
   - Sends email to configured recipients
   - Posts summary to Slack channel

## Setup Instructions

### Prerequisites
- n8n instance (self-hosted or cloud)
- GNews API key ([Get it here](https://gnews.io))
- OpenAI API key
- Slack workspace with bot permissions
- Gmail account with OAuth2

### Installation

1. **Import Workflow**
   - Download `Slack_AI_Newsletter_FIXED_v2.json`
   - In n8n, click "Import from File"
   - Select the downloaded file

2. **Configure Credentials**
   - **Slack API**: Connect your Slack workspace
   - **OpenAI API**: Add your API key
   - **Gmail OAuth2**: Authenticate your Gmail account

3. **Update Settings**
   - Change email recipients in "Email Newsletter" node
   - Update Slack channel ID if needed
   - Replace GNews API key with your own

4. **Activate**
   - Toggle the workflow to "Active"
   - Test by mentioning the bot in Slack

## Workflow Structure
```
Slack Trigger
    ↓
Extract Topic
    ↓
Fetch News from GNews API
    ↓
Extract & Clean Articles
    ↓ ↓
    ↓ └──→ Format Slack Message → Post to Slack
    ↓
Generate HTML with GPT-4
    ↓
Extract HTML
    ↓
Send Email Newsletter
```

## Configuration

### Email Recipients
Update the `sendTo` field in the "Email Newsletter" node:
```
your-email@example.com, another@example.com
```

### API Keys
- **GNews**: Replace in "Fetch News from API" node URL
- **OpenAI**: Configure in n8n credentials

### Slack Channel
Update `channelId` in "Slack Trigger" and "Post to Slack" nodes

## Usage Examples
```
@newsletter_bot Alert: Get the latest news about AI
@newsletter_bot Alert: Get the latest news about Climate Change
@newsletter_bot Alert: Get the latest news about Tesla
```

## Troubleshooting

**No articles appearing in Slack?**
- Check if GNews API key is valid
- Verify topic extraction is working

**Email subject shows "Top News"?**
- Ensure topic is flowing through workflow nodes
- Check "Extract News" and "Extract HTML" nodes

**Workflow not triggering?**
- Verify bot is invited to the Slack channel
- Check webhook is active

## Tech Stack

- **n8n** - Workflow automation
- **GNews API** - News articles
- **OpenAI GPT-4** - Newsletter generation
- **Slack** - Trigger & notifications
- **Gmail** - Email distribution

## License

MIT License - Feel free to modify and use!

## Contributing

Pull requests welcome! Feel free to:
- Add new features
- Improve newsletter design
- Add more news sources
- Enhance error handling

## Author

Created by Krithika Narayanan

---

⭐ If you find this useful, please star the repo!
