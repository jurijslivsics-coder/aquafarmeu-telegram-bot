# Next Steps: Launch AquaFarmEU Bot

## 1. Create a GitHub Repository

1. Open GitHub.
2. Create a new private repository, for example `aquafarmeu-telegram-bot`.
3. Upload all files from this folder.

Do not upload a `.env` file if you create one locally.

## 2. Create a Render Web Service

1. Open Render.
2. Choose New > Web Service.
3. Connect the GitHub repository.
4. Render should detect `render.yaml`.
5. Use Python environment.

## 3. Add Secret Environment Variables in Render

Add these:

```text
TELEGRAM_BOT_TOKEN
OPENAI_API_KEY
```

Add this after Render gives you the public service URL:

```text
WEBHOOK_URL=https://your-render-service-name.onrender.com
```

Optional after first test:

```text
ALLOWED_TELEGRAM_USER_IDS=your_numeric_telegram_id
```

## 4. Deploy

Start the deploy in Render and wait until it says the service is live.

## 5. Test in Telegram

1. Open `t.me/AquaFarmEU_bot`.
2. Send `/start`.
3. Ask one simple question about the project documents.

## 6. Lock Access

After `/start`, the bot shows your numeric Telegram user ID.

Put that ID into `ALLOWED_TELEGRAM_USER_IDS` in Render and redeploy.

Then add other allowed people later by separating IDs with commas.
