# 🚀 Crypto Market Intelligence Pipeline

> **Automated News-Driven Trade Opportunity Scanner**
> An end-to-end automated data pipeline that detects active cryptocurrencies, aggregates multi-source news, applies AI sentiment analysis, and produces structured insights for potential daily trading opportunities.

---

## 🖥️ Web Dashboard

A fully interactive web dashboard is included (`crypto-dashboard.html`) that connects directly to the n8n webhook and visualizes the pipeline output in real time.

### Features
- **Top 10 Gainers & Losers** — crypto symbol chips with % change
- **AI Sentiment Panel** — per-coin sentiment score, reasons, and key headlines (powered by Gemini)
- **Top Volume & Top Trades** — bar chart panels from Binance data
- **Pipeline Visualization** — plays the workflow video while data is loading
- **Demo Mode** — preview the dashboard with sample data without needing the webhook live
- **Single HTML file** — no build step, no dependencies, open directly in any browser

### How to Use
1. Open `crypto-dashboard.html` in your browser
2. Paste your n8n production webhook URL:
   ```
   https://your-n8n-instance/webhook/crypto/demo/movers
   ```
3. Click **▶ Run Analysis** — the pipeline video plays while data loads (~30s)
4. Dashboard renders with live market intelligence

### n8n Webhook Setup
In your n8n Webhook node, configure:
| Setting | Value |
|---|---|
| HTTP Method | `POST` |
| Allowed Origins (CORS) | `*` |
| Respond | Using 'Respond to Webhook' Node |

Then **activate** the workflow to register the production URL.

---

## 🎯 Project Purpose

This project develops an end-to-end automated data pipeline that identifies potential cryptocurrency trading opportunities for the current day by combining:

- 📈 Market movement data
- 💧 Liquidity indicators
- 📰 Multi-source news aggregation
- 🧠 AI-based sentiment analysis
- 🔌 Structured API output

> **The goal is to answer: "Which coins are moving today — and WHY?"**

---

## ❌ Business Problem Addressed

Crypto traders face information overload:

- Thousands of coins
- Constant price fluctuations
- Fragmented news sources
- Difficulty linking news to price movement
- Lack of real-time decision support

---

## ✅ Solution Overview

The system automatically:

1. Detects active coins based on market data
2. Aggregates relevant news per coin
3. Filters noise and duplicates
4. Applies AI sentiment analysis
5. Produces structured insights for trading decisions

---

## 🛠️ Tools & Technologies

| Layer | Tool | Purpose |
|---|---|---|
| Orchestration | n8n (self-hosted) | ETL + automation engine |
| Market Data | Binance Public API `/api/v3/ticker/24hr` | Gainers, losers, volume, trades |
| News Sources | Google News RSS, CoinDesk RSS, Cointelegraph RSS | Multi-source news aggregation |
| AI Engine | Google Gemini | Sentiment analysis, headline extraction |
| Transformation | JavaScript (n8n Code nodes) | Normalization, grouping, formatting |
| API Layer | n8n Webhook | Structured JSON output |
| Dashboard | HTML/CSS/JS (single file) | Interactive visualization |

---

## 🏗️ System Architecture

```
Webhook Trigger
      │
      ▼
┌─────────────────────────────────┐
│  Active Crypto Detection        │
│  Binance API → Top Gainers,     │
│  Losers, Volume, Trades         │
└──────────────┬──────────────────┘
               │
               ▼
┌─────────────────────────────────┐
│  Sentiment Pipeline             │
│  Google RSS + CoinDesk +        │
│  Cointelegraph → Normalize →    │
│  Group by Asset                 │
└──────────────┬──────────────────┘
               │
               ▼
┌─────────────────────────────────┐
│  AI Analysis (Gemini)           │
│  Sentiment Score + Reasons +    │
│  Key Headlines per coin         │
└──────────────┬──────────────────┘
               │
               ▼
┌─────────────────────────────────┐
│  Structured JSON Output         │
│  topGainers, topLosers,         │
│  topVolume, topTrades,          │
│  sentiment { gainers, losers }  │
└─────────────────────────────────┘
```

---

## 📦 Repository Contents

| File | Description |
|---|---|
| `crypto-market-intelligence-n8n.json` | n8n workflow — import this into your n8n instance |
| `crypto-dashboard.html` | Interactive web dashboard — open in browser |
| `crypto-pipeline.mp4` | Pipeline visualization video (used in dashboard loading screen) |
| `README.md` | This file |

---

## 🚀 Getting Started

### 1. Import the n8n Workflow
1. Open your n8n instance
2. Go to **Workflows** → **Import from file**
3. Select `crypto-market-intelligence-n8n.json`
4. Configure your credentials (Binance, Google Gemini)
5. Set up the Webhook node (POST, CORS `*`)
6. **Activate** the workflow

### 2. Open the Dashboard
1. Download `crypto-dashboard.html`
2. Open it in Chrome or Edge
3. Enter your production webhook URL
4. Click **▶ Run Analysis**

### 3. API Output Format
```json
{
  "topGainers": [
    { "symbol": "SIGNUSDT", "changePct": 36.09 }
  ],
  "topLosers": [
    { "symbol": "BARDUSDT", "changePct": -27.77 }
  ],
  "topVolume": [
    { "symbol": "USDCUSDT", "quoteVolume": 1308135661 }
  ],
  "topTrades": [
    { "symbol": "ROBOUSDT", "count": 1748579 }
  ],
  "sentiment": {
    "gainers": [
      {
        "symbol": "SIGNUSDT",
        "asset": "SIGN",
        "sentiment": "positive",
        "sentimentScore": 7,
        "reasons": ["Strong buy pressure", "New partnership announced"],
        "keyHeadlines": ["SIGN token surges on major CEX listing news"]
      }
    ],
    "losers": []
  }
}
```

---

## 🔮 Future Enhancements

- [ ] Order book liquidity metrics
- [ ] Funding rate analysis
- [ ] On-chain data integration (whale tracking)
- [ ] Social sentiment (X / Reddit)
- [ ] Predictive modeling
- [ ] Alert system (Telegram / Discord)
- [ ] Scheduled auto-refresh in dashboard

---

## 📝 Conclusion

This system functions as a **real-time crypto market intelligence engine** that transforms raw data into actionable insights — bridging the gap between market movements, news catalysts, and decision-ready analytics.

---

*Built with n8n · Binance API · Google Gemini · Vanilla JS*
