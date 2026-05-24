# TradingAgents: A Plain-English Guide

> What this project does, how it works, and how to use it — no coding experience required.

---

## What Is This?

**TradingAgents** is a computer program that acts like a small investment firm — but instead of human employees, it uses **AI assistants** (called "agents") to research stocks and decide whether to buy, hold, or sell them.

Think of it like this:

> You ask: *"Should I invest in Apple stock today?"*
> The program sends that question through a team of AI specialists — just like a real hedge fund would — and each one contributes their expertise before a final decision is made.

It is a **research and learning tool**, not a real trading platform. It does not move any money.

---

## The Team of AI Agents

The system is organized exactly like a real investment firm with clear departments and a chain of command.

### Department 1: The Analyst Team

These agents are the "researchers." They each look at a different angle of the stock:

| Agent | What They Look At |
|-------|------------------|
| **Market Analyst** | Price charts and technical signals (e.g., is the stock trending up or down?) |
| **Social Media Analyst** | News sentiment and public opinion about the company |
| **News Analyst** | Big-picture world events that could affect the stock (interest rates, economy, etc.) |
| **Fundamentals Analyst** | The company's actual financial health (profits, debt, revenue growth) |

You can choose which analysts to use. Using all four gives the most thorough picture.

---

### Department 2: The Research Team

After the analysts finish their reports, two debaters take the stage:

- **Bull Researcher** — argues *why the stock is a good investment* (optimistic side)
- **Bear Researcher** — argues *why the stock is risky or overvalued* (pessimistic side)

They go back and forth in a structured debate (you can control how many rounds). Then a **Research Manager** reads both arguments and writes a balanced investment recommendation — rated on a 5-point scale:

> **Buy → Overweight → Hold → Underweight → Sell**

---

### Department 3: The Trader

The **Trader** receives the Research Manager's recommendation and translates it into a concrete action:

> *"Based on the analysis, I recommend buying 200 shares of NVDA at market open."*

---

### Department 4: Risk Management Team

Before the trade is approved, three more debaters evaluate the risk:

- **Aggressive Risk Advisor** — pushes to take on more risk for bigger potential gains
- **Conservative Risk Advisor** — urges caution and protection of capital
- **Neutral Risk Advisor** — balances both sides

---

### Department 5: The Portfolio Manager

The **Portfolio Manager** is the final decision-maker. They read the risk debate and make the ultimate call:

- Approve the trade as proposed
- Approve with adjustments (e.g., buy fewer shares)
- Reject the trade entirely

Their decision is the program's final output.

---

## How It All Flows Together

```
You type a stock ticker (e.g., "NVDA") and a date
                    ↓
Analyst Team gathers data and writes reports
(market, social, news, fundamentals)
                    ↓
Bull and Bear Researchers debate the investment
                    ↓
Research Manager summarizes: Buy / Hold / Sell
                    ↓
Trader proposes a specific transaction
                    ↓
Risk Team debates the risk level
                    ↓
Portfolio Manager makes the final decision
                    ↓
Full report saved to your computer
```

The whole process takes a few minutes and produces a detailed written report at each stage.

---

## What Data Does It Use?

The program pulls real financial data from the internet:

| Data Source | What It Provides |
|-------------|-----------------|
| **Yahoo Finance** (free) | Stock prices, charts, company financials, news |
| **AlphaVantage** (optional, needs a free API key) | Alternative source for the same data |

It calculates financial indicators automatically — things like RSI (momentum), MACD (trend direction), and Bollinger Bands (price volatility). You don't need to know what these mean; the Market Analyst agent interprets them.

---

## What AI "Brains" Can It Use?

The agents can be powered by different AI providers. You pick one:

| Provider | Example Models |
|----------|---------------|
| **OpenAI** | GPT-4, GPT-4-mini |
| **Anthropic** | Claude Sonnet, Claude Opus |
| **Google** | Gemini Pro, Gemini Flash |
| **DeepSeek** | DeepSeek-V3, R1 (with reasoning) |
| **xAI** | Grok models |
| **Ollama** | Run AI locally on your own computer (no internet needed) |

You need an API key (like a password) for whichever provider you choose. Most have free tiers.

---

## What You Get at the End

After a run, the program saves a detailed report to your computer organized into folders:

```
results/
  NVDA/
    2026-01-15/
      1_analysts/       ← All four analyst reports
      2_research/       ← Bull vs. Bear debate + manager summary
      3_trading/        ← Trader's proposed transaction
      4_risk/           ← Risk debate transcript
      5_portfolio/      ← Final Portfolio Manager decision
```

It also keeps a **memory log** — a running history of every past decision. On future runs for the same stock, the AI can learn from its past calls (e.g., "Last time I was bullish on NVDA, it dropped 8% — let me be more cautious this time").

---

## How to Run It

### Option A: Interactive Mode (Easiest)

Type this in your terminal:

```
tradingagents
```

The program will ask you a series of questions:
1. Which stock ticker? (e.g., `AAPL`, `NVDA`, `TSLA`)
2. Which date to analyze?
3. Which analysts to include?
4. Which AI provider to use?
5. How deep should the analysis be?

Then it runs and shows you live progress as each agent works.

---

### Option B: Python Script

```python
from tradingagents.graph.trading_graph import TradingAgentsGraph
from tradingagents.default_config import DEFAULT_CONFIG

config = DEFAULT_CONFIG.copy()
config["llm_provider"] = "openai"

ta = TradingAgentsGraph(config=config)
state, decision = ta.propagate("NVDA", "2026-01-15")

print(decision)
```

---

## Key Settings You Can Change

| Setting | What It Does | Example Values |
|---------|-------------|---------------|
| `llm_provider` | Which AI company to use | `"openai"`, `"anthropic"`, `"google"` |
| `deep_think_llm` | Model for complex reasoning | `"gpt-4o"`, `"claude-sonnet-4-6"` |
| `max_debate_rounds` | How many Bull vs. Bear rounds | `1` (fast) to `3` (thorough) |
| `max_risk_discuss_rounds` | How many Risk debate rounds | `1` to `3` |
| `output_language` | Language for final report | `"English"`, `"Spanish"`, `"Chinese"` |
| `checkpoint_enabled` | Resume if program crashes | `True` or `False` |

---

## Crash Recovery

If the program stops in the middle of a run (power cut, internet issue, etc.), it can **pick up where it left off** — no need to start over. This is called "checkpointing." Just re-run with `--checkpoint` enabled.

---

## Important Disclaimer

> This program is a **research and educational tool**. It does not connect to any brokerage account, does not execute real trades, and its output is **not financial advice**. Always consult a licensed financial advisor before making investment decisions.

---

## Glossary

| Term | Plain-English Meaning |
|------|----------------------|
| **Agent** | An AI assistant with a specific role (e.g., Analyst, Trader) |
| **LLM** | Large Language Model — the AI "brain" powering each agent |
| **Ticker** | A stock's short code (e.g., AAPL = Apple, NVDA = Nvidia) |
| **Bull / Bullish** | Optimistic outlook — expecting the price to go up |
| **Bear / Bearish** | Pessimistic outlook — expecting the price to go down |
| **API Key** | A password that lets the program access a paid AI service |
| **Technical Indicators** | Math formulas applied to price data to spot trends (RSI, MACD, etc.) |
| **Fundamentals** | A company's real financial numbers (revenue, profit, debt) |
| **Portfolio Manager** | The final decision-maker agent — approves or rejects trades |
| **Checkpoint** | A saved snapshot so the program can resume after a crash |
| **Memory Log** | A file recording all past decisions so the AI can learn over time |
