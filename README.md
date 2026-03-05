# Web Scraping Monitor

A **price/availability monitoring system** using web scraping, historical storage, and alerts.

## Goals
- Collect product data with reliable scraping
- Store history for trend analysis
- Trigger alerts (price drop / back in stock)
- Keep scraping resilient (retry, rate limit, parsing)

## Tech Stack
- Python
- HTTPX / BeautifulSoup (or Scrapy)
- PostgreSQL / SQLite
- Docker
- Notifications: Telegram (roadmap)

## Architecture
**Scraper → Raw Storage → Normalization → History DB → Alerts**

## Roadmap
- [ ] Scrape 1 website + 5 products
- [ ] Store price history
- [ ] Alert rules (target price / % drop)
- [ ] Telegram bot notifications
- [ ] Scheduler (cron / Airflow)

## Status
🚧 In development

## Author
Jackson Oliveira
