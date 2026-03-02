# Crypto-Market-Intelliggence-Pipeline
Automated News-Driven Trade Opportunity Scanner  An end-to-end automated data pipeline that detects active cryptocurrencies, aggregates multi-source news, applies AI sentiment analysis, and produces structured insights for potential daily trading opportunities.



# Project Purpose
This project develops an end-to-end automated data pipeline that identifies potential cryptocurrency trading opportunities for the current day by combining:
•	Market movement data
•	Liquidity indicators
•	Multi-source news aggregation
•	AI-based sentiment analysis
•	Structured API output
👉 The goal is to answer:
“Which coins are moving today — and WHY?”
________________________________________
## Business Problem Addressed
Crypto traders face information overload:

❌ Thousands of coins

❌ Constant price fluctuations

❌ Fragmented news sources

❌ Difficulty linking news to price movement

❌ Lack of real-time decision support
________________________________________
## Solution Overview

The system automatically:
1.	Detects active coins based on market data
2.	Aggregates relevant news per coin
3.	Filters noise and duplicates
4.	Applies AI sentiment analysis
5.	Produces structured insights for trading decisions
________________________________________
## Tools & Technologies Used
🔹 Workflow Orchestration

n8n (self-hosted)

Used as the core automation engine.

Capabilities leveraged:

•	API orchestration

•	Scheduling / triggering

•	Loop processing

•	Data transformation

•	Error handling

•	Webhook API creation

•	AI integration

👉 Acts as a lightweight ETL + orchestration platform
________________________________________
## 🔹 Market Data Source

Binance Public API

Key endpoint:

/api/v3/ticker/24hr

Used to compute:

•	Top gainers (24h % change)

•	Top losers

•	Highest volume pairs

•	Most traded pairs
________________________________________
## 🔹 News Data Sources

Multi-source ingestion for robustness:

 ### Google News RSS
 
•	Broad coverage

•	Fast updates

•	High recall

### CoinDesk RSS
•	Institutional-grade crypto reporting


### Cointelegraph RSS

•	Retail-focused market news

•	Project updates

•	Ecosystem developments

👉 Combining sources reduces bias and improves coverage.
________________________________________
## 🔹 AI & NLP Engine
Google Gemini Chat Model

Used for:

•	Per-coin sentiment analysis

•	Market impact interpretation

•	Headline extraction

•	Reason generation
________________________________________
## 🔹 Programming / Data Transformation

JavaScript (inside n8n Code nodes)

Used for:

•	Data normalization

•	Filtering

•	Grouping by asset

•	Merging datasets

•	Final API formatting
________________________________________
## 🔹 API Layer

Webhook endpoint (n8n)

Provides structured JSON output for:

•	Dashboards

•	Frontend apps

•	Automation tools

•	Trading assistants
________________________________________
## System Architecture

🔄 High-Level Pipeline Flow

Market Data → Coin Selection → News Retrieval → Normalization → Grouping → AI Analysis → Structured Output
________________________________________
## Detailed Workflow

### 1️⃣ Market Detection Layer

Identifies active coins:

•	Top gainers

•	Top losers

•	High volume

•	High trade activity

👉 Focuses analysis on relevant assets only.
________________________________________
### 2️⃣ News Acquisition Layer

For each selected coin:

•	Query multiple RSS sources

•	Retrieve recent articles

•	Handle rate limits

•	Prevent pipeline overload
________________________________________
### 3️⃣ Data Normalization Layer

Each source has different formats.

Normalized into a unified schema:
```json
{
  "asset": "ATOM",
  "name": "Cosmos",
  "source": "CoinDesk",
  "title": "...",
  "url": "...",
  "publishedAt": "...",
  "summary": "..."
}
```
👉 Critical for downstream processing.
________________________________________
### 4️⃣ News Grouping Layer
Articles are grouped per asset:
```json
{
  "ATOM": [ ...articles... ],
  "DOT": [ ...articles... ]
}
Limits applied to prevent payload explosion.
```
________________________________________
### 5️⃣ AI Analysis Layer
The Gemini model evaluates:

•	Overall sentiment

•	Key drivers

•	Market relevance

•	Representative headlines

Output example:
```json
{
  "symbol": "ATOM",
  "sentiment": "positive",
  "sentimentScore": 6,
  "reasons": [
    "Developer activity reached all-time high",
    "New DeFi launches on Cosmos Hub"
  ]
}
```
________________________________________
### 6️⃣ Aggregation Layer
Combines:

•	Market movers

•	Liquidity indicators

•	Sentiment insights
________________________________________
### 7️⃣ API Output Layer
Final structured response via webhook:
```json
{
  "topGainers": [...],
  "topLosers": [...],
  "topVolume": [...],
  "topTrades": [...],
  "sentiment": {...}
}
```
________________________________________
##  Challenges Faced During Development
 1) Data Heterogeneity

Different news sources provide:

•	Different field names

•	Missing metadata

•	Inconsistent timestamps

•	Various content formats

👉 Solved through normalization layer.
________________________________________
 2) Noise & Irrelevant News

Many articles mention coins casually.

Solution:

•	Coin-specific filtering

•	Grouping by asset

•	AI interpretation
________________________________________
 3) API Rate Limits

Fetching news per coin can overwhelm sources.

Mitigation:

•	Loop control

•	Wait nodes

•	Payload limits

•	Top-N filtering
________________________________________
 4) Linking News to Market Moves

Hardest problem.

Price movements may be caused by:

•	Liquidity

•	Technical factors

•	Whale activity

•	Derivatives markets

👉 AI used to approximate causal signals.
________________________________________
 5) AI Output Consistency

Models sometimes produce:

•	Non-JSON output

•	Hallucinated content

•	Missing fields

Solution:

•	Strict prompt design

•	Schema enforcement

•	Post-processing
________________________________________
 6) Payload Size & Performance

Large news sets can:

•	Slow execution

•	Increase costs

•	Cause timeouts

Mitigation:

•	Limit articles per asset

•	Filter inactive coins

•	Use top movers only
________________________________________
 7) Real-Time Reliability

Crypto markets operate 24/7.

Pipeline must be:

•	Fault tolerant

•	Restartable

•	Deterministic
________________________________________
 Key Achievements

This project demonstrates:

🧠 Data Engineering Skills

•	ETL design

•	API orchestration

•	Data normalization

•	Pipeline reliability

•	Schema design
________________________________________
 Analytics Capability

•	Market intelligence extraction

•	Signal prioritization

•	Multi-factor analysis
________________________________________
 Applied AI Integration

•	Real-world NLP usage

•	Structured output generation

•	Domain-specific prompts
________________________________________
 Production Thinking

•	Rate limiting

•	Payload control

•	Error handling

•	API design
________________________________________
 Use Cases

For Traders

•	Identify actionable coins today

•	Understand movement drivers

•	Reduce research time
________________________________________
For Analysts

•	Market monitoring

•	Event impact analysis

•	Trend detection
________________________________________
For Developers

•	Backend intelligence API

•	Trading dashboards

•	Automation systems
________________________________________
 Future Enhancements

Possible upgrades:

•	Order book liquidity metrics

•	Funding rate analysis

•	On-chain data integration

•	Whale tracking

•	Social sentiment (X/Reddit)

•	Predictive modeling

•	Alert systems
________________________________________
# Conclusion

This system functions as a real-time crypto market intelligence engine that transforms raw data into actionable insights.
It bridges the gap between:

👉 Market movements

👉 News catalysts

👉 Decision-ready analytics

