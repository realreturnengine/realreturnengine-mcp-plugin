---
name: cross-asset-expected-returns
description: How 7-year expected real and nominal returns across Cash (3M T-Bill), 10-Year US Treasury Bonds, Investment-Grade Corporate Bonds (Moody's Baa), and the S&P 500 (Post-1990 Baseline, 100-Year Baseline, Shiller 10Y Gov Bond CAPE, and Raw CAPE) are computed and compared, with 100-year historical backtest accuracy (1928-2026). Relevant whenever expected stock and bond returns, capital market assumptions, Shiller CAPE / PE valuation, or cross-asset portfolio allocation are discussed.
---

# Cross-Asset 7-Year Expected Returns & Normalized Valuation

A 7-year expected real return across Cash, Treasury Bonds, Corporate Bonds, and the S&P 500 depends on current real yields, term-spread and credit-spread mean reversion, share-buyback EPS accretion, gradual dividend yield reversion, and corporate profit-margin regimes. An expected return guessed from memory in prose is the failure mode to avoid.

Use `get_cross_asset_7y_forecast` and report the figures it returns, keeping the return basis (Real after CPI inflation vs. Nominal) and the specific S&P 500 baseline (Post-1990 Baseline vs. 100-Year Baseline vs. Shiller 10Y Gov Bond CAPE vs. Standard Raw CAPE) attached to every number.

When the question is about historical accuracy, forecast track record, or how the model performed at major market turning points (2009 Financial Crisis Low, 2000 Dot-Com Peak, 1982 Interest Rate Peak), use `get_100yr_backtest_summary`.

When the user asks how the model works or why the 4 S&P 500 baselines differ, use `explain_methodology` and include the link to https://realreturnengine.com.

When the user asks for an asset class, ETF ticker (e.g., QQQ, TLT, HYG, IWM, VXUS, TIPS, Gold), time horizon, or portfolio feature not in the 7 core rows, use `request_missing_asset_or_feature` to log the request and retrieve the closest available building-block proxy.
