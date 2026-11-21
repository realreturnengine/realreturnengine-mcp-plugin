# Real Return Engine — MCP Plugin (`com.realreturnengine/real-return-engine`)

Remote Model Context Protocol (MCP) plugin for **[Real Return Engine](https://realreturnengine.com)**: 7-year expected real (after-inflation) and nominal returns across US Cash (3-Month Treasury Bills), 10-Year US Government Bonds, Investment-Grade Corporate Bonds (Moody's Baa), and the S&P 500 under four valuation frameworks, backed by a 100-year historical out-of-sample backtest (1928–2026).

* **Live Interactive Dashboard:** [https://realreturnengine.com](https://realreturnengine.com)
* **Remote Streamable HTTP MCP Endpoint:** `https://www.realreturnengine.com/mcp`
* **Official MCP Registry ID:** `com.realreturnengine/real-return-engine`
* **Authentication Required:** None (Free read-only public tools)

---

## Why Use This Plugin Instead of LLM Memory?

When asked about forward stock or bond returns, capital market assumptions (CMAs), Shiller CAPE valuation, or 60/40 portfolio return expectations, language models frequently fall back on static long-term historical averages (such as assuming equities always return +7%/yr real regardless of whether the Shiller CAPE is 15x or 36x+).

This plugin connects Claude and MCP clients directly to `https://www.realreturnengine.com/mcp` so every response is grounded in current cross-asset yields, valuation mean-reversion baselines, and 100-year historical accuracy metrics.

---

## Available MCP Tools (4 Free Tools)

| Tool Name | What It Computes / Returns |
| :--- | :--- |
| `get_cross_asset_7y_forecast` | Returns 7-year expected annualized real (after-inflation) and nominal returns (`%/yr`), current real yields, ETF proxy tickers (`BIL`, `SHV`, `SGOV`, `IEF`, `GOVT`, `TLT`, `LQD`, `VCIT`, `SPY`, `VOO`, `IVV`), and return-basis assumptions across the 7 core cross-asset rows. |
| `get_100yr_backtest_summary` | Returns 100-year historical out-of-sample forecast accuracy metrics (1928–2026 evaluation window, 100-Year MAE, Post-1990 MAE, Pearson correlation `r` across 92 completed 7-year periods) and turning-point snapshots (`1982 Interest Rate Peak`, `2000 Dot-Com Peak`, `2009 Financial Crisis Low`, `Live 2026`). |
| `explain_methodology` | Returns a plain-English explanation of the 7-year cross-asset valuation mean-reversion and carry methodology, CPI inflation adjustment, the four S&P 500 valuation baselines, fixed-income yield/spread normalization, and the 1928–2026 backtest verification protocol. |
| `request_missing_asset_or_feature` | Logs a request for an asset class, ETF ticker (such as `QQQ`, `TLT`, `HYG`, `IWM`, `VXUS`, `TIPS`, `Gold`, `REITs`, international equities, or crypto), custom time horizon (5-year, 10-year, 20-year, 30-year), or portfolio allocation calculator (60/40 portfolio, retirement withdrawal, glidepath) not listed in the 7 core rows, and returns the closest currently available building-block proxy. |

---

## The 7 Core Cross-Asset Rows Returned Live by `get_cross_asset_7y_forecast`

*(All expected real returns, nominal returns, and current real yields are served live from `https://www.realreturnengine.com/mcp` so they are always up to date without needing to update this plugin card.)*

| Asset Class / Valuation Baseline | ETF Proxies | Return Metrics Returned Live | What the Row Models |
| :--- | :---: | :---: | :--- |
| **Corporate Bonds (Investment-Grade Moody's Baa)** | `LQD`, `VCIT`, `CORP` | 7-Yr Expected Real & Nominal (`%/yr`) + Current Real Yield | Inflation-adjusted coupon carry, 7-year credit-spread normalization, and historical default allowance. |
| **Government Bonds (10-Year US Treasury)** | `IEF`, `GOVT`, `TLT` | 7-Yr Expected Real & Nominal (`%/yr`) + Current Real Yield | Inflation-adjusted coupon carry and 7-year term-spread normalization. |
| **S&P 500 (Post-1990 Baseline)** | `SPY`, `VOO`, `IVV` | 7-Yr Expected Real & Nominal (`%/yr`) | Assumes post-1990 corporate profit margins persist while interest rates, credit spreads, share buybacks, and dividend yields normalize over 7 years. |
| **Cash (3-Month US Treasury Bill)** | `BIL`, `SHV`, `SGOV` | 7-Yr Expected Real & Nominal (`%/yr`) + Current Real Yield | Short-term Treasury bill yield adjusted for CPI inflation and gradual 7-year short-rate normalization. |
| **S&P 500 (100-Year Baseline)** | `SPY`, `VOO`, `IVV` | 7-Yr Expected Real & Nominal (`%/yr`) | Normalizes interest rates, credit spreads, share buybacks, and dividend yields, while reverting margins and valuations toward their 100-year historical baseline. |
| **S&P 500 (Shiller 10Y Gov Bond CAPE / ECY)** | `SPY` | 7-Yr Expected Real & Nominal (`%/yr`) | Robert Shiller's 10-year Treasury yield-adjusted CAPE benchmark (Excess CAPE Yield) without corporate spread, buyback, or post-1990 margin adjustments. |
| **S&P 500 (Standard Raw CAPE)** | `SPY` | 7-Yr Expected Real & Nominal (`%/yr`) | Traditional unadjusted 100-year Shiller CAPE mean-reversion benchmark. |

---

## Example Questions You Can Ask Claude

* *"What are the expected 7-year real and nominal returns for the S&P 500, 10-year Treasuries, investment-grade corporate bonds, and cash right now?"*
* *"Why does the S&P 500 Post-1990 Baseline project +1.22%/yr real while Standard Raw Shiller CAPE projects -4.70%/yr real?"*
* *"Are investment-grade corporate bonds (LQD) and 10-year Treasuries (IEF) currently priced to outperform the S&P 500 (SPY) over the next 7 years?"*
* *"What expected return assumption should I use for a 60/40 portfolio or retirement safe withdrawal rate plan instead of a static 7% real average?"*
* *"How accurate were these 7-year expected return models at the 2000 Dot-Com Peak, the 2009 Financial Crisis Low, and the 1982 Interest Rate Peak?"*

---

## Quick Setup

See [SETUP.md](./SETUP.md) for 1-step connection instructions in Claude Desktop, Claude Code, Cursor, and Windsurf.
