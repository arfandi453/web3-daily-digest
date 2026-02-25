# 🌐 Web3 Daily Digest — OpenClaw Skill

From 30+ top Web3/Crypto sources, automatically fetch, score, and summarize the best articles into a daily digest.

Covers: **CoinDesk · Decrypt · Bankless · Vitalik · a16z · Paradigm · Rekt · Arthur Hayes · Uniswap · Aave · Lido · Jupiter · ether.fi** and more.

**No external API keys required.** Uses the OpenClaw agent's own LLM.

## Quick Start

### Install as OpenClaw Skill

```bash
clawhub install web3-daily-digest
```

Then in any OpenClaw chat:

```
/web3digest
```

### Manual Installation

```bash
git clone https://github.com/HarrisHan/web3-daily-digest.git
cp -r web3-daily-digest ~/.openclaw/workspace/skills/
```

## How It Works

```
30+ RSS Feeds → Concurrent Fetch → Time Filter → LLM Scoring → LLM Summary → Digest
```

The agent handles all scoring and summarization natively — no Gemini/OpenAI API keys needed.

## Source Categories

| Category | Sources |
|----------|---------|
| 📰 News | CoinDesk, Decrypt, Blockworks, CoinTelegraph, The Block |
| 🔬 Research | Paradigm, a16z crypto, Delphi Digital, Galaxy, Messari |
| 💰 DeFi | Uniswap, Aave, Lido, MakerDAO, Compound, Jupiter, ether.fi |
| 🏗️ L1/L2 | Ethereum Foundation, Solana, Optimism, Arbitrum, Base, Starknet, Celestia |
| 🔒 Security | Trail of Bits, Rekt News, Immunefi, Slowmist, Certik |
| ✍️ Writers | Vitalik Buterin, Arthur Hayes, Cobie, Nic Carter, Polynya |
| 🏦 Exchanges | Binance Research, Coinbase Blog, Kraken Blog |

## Configuration

### Scheduled Daily Digest

```bash
openclaw cron add \
  --name "web3-daily-digest" \
  --cron "0 9 * * *" \
  --tz "Asia/Shanghai" \
  --message "/web3digest" \
  --announce --exact
```

### Custom Sources

Edit `references/sources.json` to add/remove feeds.

## Project Structure

```
web3-daily-digest/
├── SKILL.md              # OpenClaw skill definition
├── README.md
├── scripts/
│   └── fetch-rss.mjs     # Concurrent RSS fetcher (Node.js, zero deps)
└── references/
    └── sources.json       # 30+ Web3/Crypto RSS sources
```

## License

MIT

## Credits

- Built for [OpenClaw](https://github.com/openclaw/openclaw) 🦞
- Companion to [ai-daily-digest](https://github.com/HarrisHan/ai-daily-digest)
