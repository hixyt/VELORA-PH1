# VELORA — Phase 2 Roadmap

Planned features and enhancements for the next iteration of the lead intelligence system.

---

## 🎯 Goals

- Increase lead data richness
- Automate outreach
- Support batch and scheduled runs
- Improve scoring accuracy

---

## Planned Features

### 1. Email & Contact Enrichment
- Scrape or look up business email addresses from websites
- Extract phone numbers and social media links
- Integrate enrichment APIs (e.g., Hunter.io, Apollo)

### 2. Multi-City Batch Processing
- Accept a list of cities in a single request
- Process cities in parallel using n8n's split-in-batches node
- Aggregate results into a single report

### 3. Scheduled Runs
- Configure cron-based triggers to run the pipeline on a schedule (e.g., weekly)
- Track new vs. previously seen leads to avoid duplicates

### 4. Advanced Lead Scoring
- Factor in number of Google reviews
- Detect social media presence
- Industry/category-based weighting
- Configurable scoring rules via a settings sheet

### 5. CRM Integration
- Push scored leads to a CRM (e.g., HubSpot, Salesforce, Notion)
- Map lead fields to CRM properties automatically
- Sync lead status back to the sheet

### 6. Automated Email Outreach
- Generate personalized outreach emails using an LLM (e.g., OpenAI)
- Send emails via Gmail or SMTP node
- Track open/reply status

### 7. Dashboard & Analytics
- Build a simple dashboard (e.g., Google Data Studio or Retool)
- Visualize leads by city, score, and category
- Track pipeline performance over time

### 8. Improved Telegram UX
- Inline keyboard buttons for city selection
- Real-time progress updates during processing
- Command menu (`/search`, `/status`, `/report`)

---

## Timeline (Tentative)

| Phase | Features | Target |
|-------|----------|--------|
| 2A | Email enrichment, multi-city batch | TBD |
| 2B | Scheduled runs, advanced scoring | TBD |
| 2C | CRM integration, outreach automation | TBD |
| 2D | Dashboard, Telegram UX improvements | TBD |

---

## Contributing

Ideas and suggestions are welcome — open an issue or reach out via Telegram.
