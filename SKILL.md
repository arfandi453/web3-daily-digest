---
name: web3-daily-digest
description: "Generate a daily Web3/Crypto news digest from 60+ top crypto blogs, research firms, and DeFi protocols. Trigger with /web3digest. Fetches RSS feeds, scores articles by relevance/quality, and produces a structured Chinese/English summary. No external API keys needed."
---

# Web3 Daily Digest

Generate a structured daily digest from 60+ top Web3/Crypto sources including CoinDesk, Decrypt, Bankless, Vitalik, a16z crypto, Paradigm, and major DeFi protocols.

## Trigger

User says `/web3digest` or asks for Web3/crypto news digest.

## Parameters (ask user if not specified)

| Param | Options | Default |
|-------|---------|---------|
| Time range | 24h / 48h / 72h | 24h |
| Top N articles | 10 / 15 / 20 | 15 |
| Language | zh / en | zh |

## Workflow

### Step 1: Fetch RSS feeds

```bash
node <skill_dir>/scripts/fetch-rss.mjs --hours <HOURS> --sources <skill_dir>/references/sources.json
```

### Step 2: Score and classify

Score each article (1-10) on:
1. **Relevance** — DeFi, L1/L2, security, regulation, market structure
2. **Quality** — Original research, data-driven, technical depth
3. **Timeliness** — Breaking news, new launches, exploit alerts

Classify into categories:
- 📈 Market / Trading
- 🏗️ Infrastructure / L1 / L2
- 💰 DeFi / Yield
- 🔒 Security / Exploits
- 📜 Regulation / Policy
- 🛠 Tools / Developer
- 💡 Research / Opinion

Select top N by total score.

### Step 3: Generate summaries

For each selected article:
1. If RSS summary is sufficient (>100 chars), use it
2. If not, use `web_fetch` to read full article
3. Generate: Chinese title + 2-3 sentence summary + keywords

### Step 4: Market context

Add brief market context if available:
- BTC/ETH price trend (from articles or web_search)
- Notable on-chain events
- Upcoming catalysts

### Step 5: Format output

```
🌐 Web3 Daily Digest — {date}
来自 60+ 顶级 Crypto/DeFi 信息源

📝 今日看点
{2-3 sentence macro trend summary}

💰 市场概况
{BTC/ETH brief + notable moves}

🏆 今日必读 (Top 3)
1. {Chinese title}
   {source} · {relative time}
   {summary}
   🏷️ {keywords}

📋 更多精选
4-N. {title} — {source} · {one-line summary}

📊 统计：{N} 源 → {M} 篇 → {K} 篇精选
```

## Notes

- Sources cover: major news (CoinDesk, Decrypt, Blockworks), research (Paradigm, a16z, Delphi), DeFi protocols (Uniswap, Aave, Lido), L2s (Optimism, Arbitrum, Base, Starknet), security (Trail of Bits, Rekt, Immunefi), and top crypto writers (Vitalik, Arthur Hayes, Cobie).
- Includes Jupiter and ether.fi — aligned with user's DeFi interests.
- No external API key needed.
