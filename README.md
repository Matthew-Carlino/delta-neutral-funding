# Delta-Neutral Funding Rate Yield Strategy

Portfolio construction and risk framework for capturing perpetual funding rates across CEX and DEX venues.

## Strategy Overview

Hold spot + short perpetual on the same asset to remain market-neutral, collecting funding payments from long-biased markets. The framework covers:

- **Yield analysis** — Net annualized yield after maker fees, spread costs, and slippage across 5 venues
- **Portfolio allocation** — Coin and venue weighting based on yield, liquidity (OI), and counterparty risk
- **Stress testing** — Margin utilization under price spikes at 5x leverage
- **Rebalance triggers** — Systematic rules for rotation, margin management, and crisis response
- **Yield enhancement** — Liquid staking, cross-exchange arb, covered calls on the spot leg

## Coins & Venues

| Coin | Allocation | OI | Rationale |
|------|-----------|-----|-----------|
| SOL | 35% | $4.8B | Most liquid altcoin perp — portfolio's flexible component |
| AVAX | 40% | $370M | Highest current yield, slower entry via TWAP |
| DOGE | 25% | $900M | BTC correlation, strong retail flow, yield upside on rallies |

**CEX:** Binance, OKX, Bybit | **DEX:** Hyperliquid, Aster

## Quick Start

```bash
pip install pandas matplotlib numpy
jupyter notebook delta-neutral-funding-yield.ipynb
```

## Key Findings

- AVAX leads with 7.5% average net yield, followed by SOL (4.6%) and DOGE (2.9%)
- Bybit consistently offers highest funding across all three coins
- At 5x leverage, a 20% price spike consumes 100% of posted margin — margin management is the primary risk
- Total DEX exposure capped at 14.5% ($1.45M) to limit counterparty risk
