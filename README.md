# VELORA — Phase 1

**AI-Powered Lead Intelligence System**

An n8n automation workflow that turns a simple city name into a scored list of local business leads — powered by Google Maps data, intelligent scoring, and delivered straight to Telegram.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🤖 **Telegram Bot Input** | Send a city name to the bot to kick off lead discovery |
| 🗺️ **Google Maps Scraping** | Fetches local businesses via SerpAPI's Google Maps endpoint |
| 📊 **Lead Scoring** | Each lead is scored based on website presence and Google rating |
| 📋 **Google Sheets Export** | Structured lead data is saved to a Google Sheet automatically |
| 📩 **Telegram Report** | A confirmation summary is sent back to the user via Telegram |

---

## 🛠️ Tech Stack

- **[n8n](https://n8n.io/)** — Workflow automation engine
- **[SerpAPI](https://serpapi.com/)** — Google Maps search results
- **[Telegram Bot API](https://core.telegram.org/bots/api)** — User input & report delivery
- **[Google Sheets API](https://developers.google.com/sheets/api)** — Lead data storage

---

## 🏗️ Architecture

```
Telegram Bot (city input)
        │
        ▼
   n8n Workflow
        │
        ├──▶ SerpAPI (Google Maps search)
        │
        ├──▶ Lead Scoring Logic
        │         • +40 pts if website exists
        │         • +20 pts per rating star
        │
        ├──▶ Google Sheets (save leads)
        │
        └──▶ Telegram Bot (send report)
```

---

## 📸 Screenshots

> _Screenshots will be added after workflow deployment._

<!-- Add screenshots here -->
[Telegram Input](screenshots/telegram-input.png)
[Google Sheet Output](screenshots/sheet-output.png)
[Telegram Report](screenshots/telegram-report.png)

---

## 🚀 Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/hixyt/VELORA-PH1.git
   cd VELORA-PH1
   ```

2. **Copy the environment template**
   ```bash
   cp .env.example .env
   ```

3. **Fill in your API keys** in the `.env` file (see [setup-guide.md](setup-guide.md) for details).

4. **Import the workflow** — Open n8n and import `workflow.json`.

5. **Activate the workflow** and send a city name to your Telegram bot.

For full step-by-step instructions, see the **[Setup Guide](setup-guide.md)**.

---

## 📁 Project Structure

```
VELORA-PH1/
├── README.md            # Project documentation
├── workflow.json        # n8n workflow export (import into n8n)
├── .env.example         # Environment variables template
├── setup-guide.md       # Detailed installation guide
└── PHASE2-roadmap.md    # Planned features for Phase 2
```

---

## 🗺️ Roadmap

Phase 1 (current) focuses on the core lead-discovery pipeline. See **[PHASE2-roadmap.md](PHASE2-roadmap.md)** for planned enhancements including email enrichment, CRM integration, and multi-city batch processing.

---

## 📄 License

This project is provided as-is for educational and personal use.
