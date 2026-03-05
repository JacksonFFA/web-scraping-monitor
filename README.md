# Web Scraping Monitor (Production-Ready)

Sistema de **aquisição e monitoramento de dados via web scraping**, com foco em **resiliência operacional**, qualidade e rastreabilidade do dado.

> Inspirado em desafios reais de Data Acquisition: fontes instáveis, mudanças de HTML, indisponibilidade, bloqueios e inconsistências.

---

## ✅ O que este projeto demonstra
- Scraping em **Python** com fundamentos sólidos de **HTTP**
- **Resiliência**: timeout, retry com backoff, rate limit, circuit breaker (roadmap)
- **Qualidade de dados**: validação de schema, normalização e deduplicação
- **Observabilidade**: logs estruturados e métricas básicas (roadmap)
- **Operação**: execução agendada e alertas (Telegram)

---

## 🎯 Objetivos
- Coletar dados (preço/disponibilidade) de forma confiável
- Manter **histórico** para análise de tendências
- Disparar alertas (queda de preço / retorno ao estoque)
- Operar bem em produção: **falha controlada + rápida recuperação**

---

## 🧰 Tech Stack
- Python 3.11+
- HTTPX (requests async-friendly) + BeautifulSoup / Selectolax (parsing)
- PostgreSQL (prod) / SQLite (dev)
- Docker / Docker Compose
- Telegram Bot (alerts)
- (Roadmap) Airflow / Cron + métricas

---

## 🧱 Arquitetura (Bronze → Silver)
**Scraper (HTTP) → Bronze (raw html/json) → Parser/Normalizer (Silver) → DB histórico → Alert Engine → Telegram**

### Camadas
- **Bronze**: resposta bruta (html + headers + status_code) com timestamp
- **Silver**: dados normalizados (preço, moeda, disponibilidade, produto_id)
- **Gold (roadmap)**: KPIs (menor preço 7d/30d, variação %, tendência)

---

## 🧪 Qualidade & Consistência
- Validação de schema (campos obrigatórios)
- Normalização de preço/moeda
- Deduplicação por `hash(source + canonical_url + title)`
- Detecção de mudança de HTML (roadmap: "parser health checks")

---

## ▶️ Como executar (Docker)
```bash
docker compose up --build
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python -m app.cli run --site example --limit 5

🗺️ Roadmap

 ° 1 site + 5 produtos (MVP)

 ° Persistência histórica (PostgreSQL)

 ° Alertas Telegram (preço alvo / % queda / estoque)

 ° Scheduler (cron)

 ° Observabilidade: métricas + alertas de falha

 ° Anti-bloqueio (proxy rotation, fingerprinting) com uso responsável

 📌 Status

🚧 Em desenvolvimento

Author
