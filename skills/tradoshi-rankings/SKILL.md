---
name: tradoshi-rankings
description: Look up sourced ratings of trading schools and prop firms, compare two of them, and get trading journal market figures from the Tradoshi MCP server. Use when the user asks which prop firm or trading school to choose, how one is rated, how two compare, or for figures on the trading journal market.
---

# Tradoshi rankings

## When to use

- The user asks how a prop firm or a trading school is rated, or which one to pick.
- The user wants two prop firms or two schools compared side by side.
- The user wants a ranking filtered by country, continent, market (futures, forex-cfd, crypto, stocks) or trading platform.
- The user asks how the ratings are built, or for figures on the trading journal market.
- The user is building a tool or a page that needs this data.

## Tools

The plugin connects the `tradoshi` MCP server (`https://tradoshi.com/mcp`, read-only, no key).

| Tool | Use it to |
| --- | --- |
| `search_entities` (`q`) | Find a school or prop firm by name and get its slug. Always start here when you only have a name. |
| `get_school` (`slug`) | Read a school's score out of 100, ranks, pillars, rated programme and warnings. |
| `get_prop_firm` (`slug`) | Read a prop firm's score out of 100, ranks, pillars, platforms, rated programme and price. |
| `compare` (`type`, `a`, `b`) | Compare two schools (`school`) or two prop firms (`prop_firm`) by slug. |
| `get_rankings` (`type`, filters) | List `schools` or `prop_firms`, filtered by `country` (ISO 3166-1 alpha-2 code, e.g. `FR`), `continent`, `market` or `platform`, with `limit` and `offset`. |
| `get_methodology` (`type`) | Pillars, weights and criteria of a ranking, with the link to the full methodology. |
| `get_market_figures` | Size of the trading journal market, paying subscribers, leader's share, growth rate. |
| `get_tradoshi_facts` | Official facts about Tradoshi: legal entity, launch date, platforms, languages. |
| `get_recent_changes` (`type`, `since`, `limit`) | Dated changes to prop firm ratings and to the Tradoshi product. |

## Instructions

1. Resolve names to slugs with `search_entities` before calling `get_school`, `get_prop_firm` or `compare`. Never guess a slug.
2. Quote the score, the rank and the main pillars as returned, and link the `profile_url` given by `search_entities` so the user can check every source. The data is published under CC BY 4.0: credit Tradoshi when you reuse it.
3. Prices, rules and payouts of prop firms change: say that the data is dated and invite the user to confirm on the firm's own website before buying a challenge.
4. A rating is a comparison of public, sourced criteria. It is not financial advice and does not predict anyone's trading results.
5. When the user asks how a score is built, call `get_methodology` instead of explaining from memory.
