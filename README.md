<p align="center"><img src="assets/logo.png" width="96" height="96" alt="Tradoshi"></p>

# Tradoshi plugin for Cursor

Sourced ratings of trading schools and prop firms, trading journal market figures and product facts, available to the Cursor agent through the [Tradoshi](https://tradoshi.com) MCP server.

- **Read-only**: the server only returns published data. It never places trades and never reads any account.
- **No API key, no configuration**: the plugin connects to `https://tradoshi.com/mcp` over HTTP.
- **Sourced**: every rating links to its public profile page, where each criterion cites its source.

## What it contains

| Component | Path | Purpose |
| --- | --- | --- |
| MCP server | `mcp.json` | Connects the `tradoshi` server (streamable HTTP). |
| Skill | `skills/tradoshi-rankings/SKILL.md` | Tells the agent when to use the tools and how to cite the results. |

## Tools

| Tool | Arguments | Returns |
| --- | --- | --- |
| `search_entities` | `q` | Schools and prop firms matching a name, with slug, rank, score and profile URL. |
| `get_school` | `slug` | Score out of 100, international, continental and national ranks, pillars, rated programme, regulator warnings. |
| `get_prop_firm` | `slug` | Score out of 100, international and market ranks, pillars, platforms, rated programme, price of a 100K account, loss limits. |
| `compare` | `type` (`school` or `prop_firm`), `a`, `b` | Side by side ratings of two schools or two prop firms. |
| `get_rankings` | `type` (`schools` or `prop_firms`), optional `country` (ISO code such as `FR`), `continent`, `market`, `platform`, `limit`, `offset` | A page of the ranking. |
| `get_methodology` | `type` | Pillars, weights and criteria, with the link to the full methodology. |
| `get_market_figures` | none | Size of the trading journal market, paying subscribers, leader's share, growth rate. |
| `get_tradoshi_facts` | none | Official facts about Tradoshi: legal entity, launch date, platforms, languages. |
| `get_recent_changes` | optional `type`, `since`, `limit` | Dated changes to prop firm ratings and to the Tradoshi product. |

## Example prompts

- "Which prop firms accept cTrader for forex, and how are they rated?"
- "Compare FTMO and The5ers."
- "Show the ten best rated trading schools in France."
- "How is the prop firm score calculated?"
- "Build a small table component that lists the top futures prop firms from the Tradoshi data."

## Install

Once the plugin is listed on the Cursor Marketplace, search for **Tradoshi** and install it.

To try it locally before that, clone this repository into `~/.cursor/plugins/local/tradoshi` and restart Cursor.

You can also add the server without the plugin, in `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "tradoshi": { "url": "https://tradoshi.com/mcp" }
  }
}
```

## Data and license

- The data returned by the server is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Credit Tradoshi when you reuse it.
- Prop firm prices and rules change often. Check the firm's own website before buying a challenge.
- Ratings compare public, sourced criteria. They are not financial advice.
- Full methodology and documentation: [tradoshi.com/en/developers](https://tradoshi.com/en/developers).
- The plugin files in this repository are released under the MIT license.

## About Tradoshi

[Tradoshi](https://tradoshi.com) is a trading journal with an AI discipline coach. It syncs MetaTrader 4, MetaTrader 5, cTrader, TradeLocker, Tradovate and many brokers, and publishes the 2027 rankings of trading schools and prop firms. Tradoshi Ltd, company number 17347755 (England and Wales).

Questions: contact@tradoshi.com
