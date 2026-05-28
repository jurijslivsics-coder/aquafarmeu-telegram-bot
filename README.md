# AquaFarmEU Telegram Bot

This is a first MVP for a Telegram assistant that answers questions using project documents.

## What It Does

- Reads project files from `knowledge/`
- Finds relevant fragments
- Uses OpenAI to answer based on those fragments
- Replies in Telegram
- Can restrict access to selected Telegram users

## Files You Can Add

Put project files into `knowledge/`.

Supported formats:

- `.txt`
- `.md`
- `.pdf`
- `.docx`
- `.xlsx`

For web pages, create this file:

```text
knowledge/urls.txt
```

Then put one link per line:

```text
https://example.com/page-one
https://example.com/page-two
```

## Local Test

1. Install Python 3.11 or newer.
2. Copy `.env.example` to `.env`.
3. Put your real secrets into `.env`.
4. Install requirements:

```bash
pip install -r requirements.txt
```

5. Start the bot:

```bash
python bot.py
```

6. Open Telegram and send `/start` to your bot.

## Render Setup

1. Create a GitHub repository.
2. Upload these files to the repository.
3. Create a new Render Web Service from that repository.
4. Add these environment variables in Render:

```text
TELEGRAM_BOT_TOKEN
OPENAI_API_KEY
OPENAI_CHAT_MODEL=gpt-4.1-mini
OPENAI_EMBEDDING_MODEL=text-embedding-3-small
```

5. After Render creates your service, copy its public URL.
6. Add one more environment variable:

```text
WEBHOOK_URL=https://your-render-service-name.onrender.com
```

7. Redeploy the service.

## Restrict Access

At first, leave `ALLOWED_TELEGRAM_USER_IDS` empty so you can test easily.

Send `/start` to the bot. It will show your Telegram user ID.

Then set this in Render:

```text
ALLOWED_TELEGRAM_USER_IDS=123456789,987654321
```

Redeploy after changing it.

## Updating Knowledge

Add or replace files in `knowledge/`, then redeploy or restart the service.

You can also send:

```text
/reload
```

The bot will rebuild its knowledge index.
