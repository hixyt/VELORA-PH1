# VELORA Phase 1 — Setup Guide

Step-by-step instructions to get the lead intelligence workflow running.

---

## Prerequisites

- An [n8n](https://n8n.io/) instance (cloud or self-hosted)
- A [Telegram](https://telegram.org/) account
- A [SerpAPI](https://serpapi.com/) account (free tier available)
- A [Google Cloud](https://console.cloud.google.com/) project with Sheets API enabled

---

## 1. Create a Telegram Bot

1. Open Telegram and search for **@BotFather**.
2. Send `/newbot` and follow the prompts to choose a name and username.
3. Copy the **bot token** — you will need it later.
4. Send a message to your new bot, then visit
   `https://api.telegram.org/bot<YOUR_TOKEN>/getUpdates` to find your **chat ID**.

---

## 2. Get a SerpAPI Key

1. Sign up at [serpapi.com](https://serpapi.com/).
2. Navigate to **Dashboard → API Key**.
3. Copy your API key.

---

## 3. Set Up Google Sheets

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project (or select an existing one).
3. Enable the **Google Sheets API**.
4. Create a **Service Account** under IAM & Admin → Service Accounts.
5. Generate a JSON key for the service account and download it.
6. Create a new Google Sheet and share it (Editor access) with the service account email
   (e.g., `velora@your-project.iam.gserviceaccount.com`).
7. Note the **Spreadsheet ID** from the sheet URL:
   `https://docs.google.com/spreadsheets/d/<SPREADSHEET_ID>/edit`

---

## 4. Configure Environment Variables

```bash
cp .env.example .env
```

Fill in every value in `.env`:

| Variable | Where to find it |
|----------|-----------------|
| `TELEGRAM_BOT_TOKEN` | BotFather message |
| `TELEGRAM_CHAT_ID` | getUpdates API call |
| `SERPAPI_API_KEY` | SerpAPI dashboard |
| `GOOGLE_SHEETS_SPREADSHEET_ID` | Google Sheet URL |
| `GOOGLE_SHEETS_SHEET_NAME` | Tab name in your sheet (default: `Leads`) |
| `GOOGLE_SERVICE_ACCOUNT_KEY_PATH` | Path to the downloaded JSON key |

---

## 5. Import the Workflow into n8n

1. Open your n8n instance.
2. Click **⋮ (menu)** → **Import from File**.
3. Select `workflow.json` from this repository.
4. The workflow will appear in the editor.

---

## 6. Add Credentials in n8n

Inside the n8n editor, create the following credentials:

| Credential Type | Values Needed |
|----------------|--------------|
| **Telegram API** | Bot Token |
| **SerpAPI** | API Key |
| **Google Sheets OAuth2 / Service Account** | Service account JSON key |

Assign each credential to its corresponding node in the workflow.

---

## 7. Activate & Test

1. **Activate** the workflow (toggle in the top-right corner of the n8n editor).
2. Open Telegram and send a city name (e.g., `Mumbai`) to your bot.
3. The workflow will:
   - Search Google Maps for local businesses in that city
   - Score each lead
   - Save the results to your Google Sheet
   - Send a summary report back to you on Telegram

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Bot doesn't respond | Make sure the workflow is **active** and the Telegram trigger node is configured correctly |
| No search results | Verify your SerpAPI key is valid and has remaining searches |
| Sheet not updating | Confirm the service account has **Editor** access to the spreadsheet |
| Credential errors in n8n | Re-check that each credential is assigned to the correct node |

---

## Next Steps

Once Phase 1 is running, check out **[PHASE2-roadmap.md](PHASE2-roadmap.md)** for planned enhancements.
