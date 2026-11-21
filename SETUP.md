# Setup Guide — Real Return Engine MCP (`https://www.realreturnengine.com/mcp`)

The Real Return Engine runs as a remote Streamable HTTP MCP server at `https://www.realreturnengine.com/mcp`. No local installation, Python runtime, or API key is required.

---

## 1. Claude Code CLI

```bash
claude mcp add --transport http realreturnengine https://www.realreturnengine.com/mcp
```

## 2. Claude Desktop / Cursor / Windsurf (`.mcp.json`)

Add the following to your MCP configuration file:

```json
{
  "mcpServers": {
    "realreturnengine": {
      "type": "http",
      "url": "https://www.realreturnengine.com/mcp"
    }
  }
}
```

---

## 3. Verify the Connection With a Test Question

Once connected, ask Claude any of the following:

1. *"Check Real Return Engine for the current 7-year expected real and nominal returns across Cash, 10-Year Treasury Bonds, Corporate Bonds, and the S&P 500."*
2. *"Explain the difference between the four S&P 500 valuation baselines on Real Return Engine (Post-1990 Baseline vs. 100-Year Baseline vs. Shiller 10Y Gov Bond CAPE vs. Standard Raw CAPE)."*
3. *"What was the 100-year and Post-1990 Mean Absolute Error (MAE) of the Real Return Engine backtest from 1928 to 2026, and what did it forecast in 2000 and 2009?"*
