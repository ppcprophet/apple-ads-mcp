# Apple Ads MCP Server

A [Model Context Protocol](https://modelcontextprotocol.io) (MCP) server for managing Apple Search Ads campaigns through AI assistants like Claude. Analyze performance, optimize bids, pause wasted spend, and manage keywords — all through natural conversation.

Built by [PPC Prophet](https://ppcprophet.com).

## What is MCP?

The Model Context Protocol lets AI assistants connect to external tools and data sources. This server gives AI assistants direct access to your Apple Search Ads account, so you can manage campaigns through natural language instead of navigating the Apple Ads UI.

## Features

### Campaign Analytics
- **Performance dashboards** — installs, spend, CPI, taps, impressions, TTR, CPT
- **Campaign-level breakdown** — sort by any metric, filter by status
- **Search term analysis** — see which App Store queries drive installs
- **Supply source comparison** — Search Results vs Search Tab vs Today Tab
- **Period-over-period comparison** — track trends week-over-week or month-over-month
- **Wasted spend detection** — find campaigns, keywords, and search terms spending without converting

### Campaign Management
- **Pause/enable campaigns** — stop wasting budget on underperformers
- **Pause/enable keywords** — control which keywords you bid on
- **Update keyword bids** — raise bids on winners, lower bids on losers
- **Add keywords** — expand targeting with exact or broad match
- **Add negative keywords** — block irrelevant search terms at campaign or ad group level

### Attribution & Revenue
- **Install attribution** — see which campaigns and keywords drove real installs
- **Subscription tracking** — track which ads generate paying subscribers, not just installs
- **True ROAS calculation** — measure revenue per ad dollar spent

### AI-Powered Optimization
- **Performance analysis** — get actionable recommendations for your account
- **Optimization dashboard** — surfaces opportunities to pause, scale, raise, or lower bids

## Available Tools (26)

### Profile Management
| Tool | Description |
|------|-------------|
| `list_apple_profiles` | List all Apple Search Ads profiles (organizations) |
| `list_apple_mcp_profiles` | List profiles with MCP activation status |
| `activate_apple_mcp_profile` | Activate a profile for MCP access |
| `check_apple_mcp_status` | Check data import status for a profile |

### Campaign & App Management
| Tool | Description |
|------|-------------|
| `list_apple_apps` | List all apps (Adam IDs) for a profile |
| `list_apple_campaigns` | List campaigns with optional filters (status, app, supply source) |
| `get_apple_campaign` | Get detailed info about a specific campaign |
| `search_apple_campaigns` | Search campaigns by name |

### Keyword Management
| Tool | Description |
|------|-------------|
| `list_apple_keywords` | List keywords with filters (campaign, ad group, status, match type) |

### Performance & Analytics
| Tool | Description |
|------|-------------|
| `get_apple_performance` | Overall performance metrics for a date range |
| `get_apple_campaign_performance` | Per-campaign metrics with sorting and filtering |
| `get_apple_wasted_spend` | Find campaigns/keywords/search terms wasting money |
| `get_apple_search_term_performance` | Search term metrics with sorting |
| `get_apple_supply_source_performance` | Breakdown by ad placement (Search Results, Search Tab, Today Tab) |
| `compare_apple_periods` | Period-over-period comparison with percent changes |

### Actions
| Tool | Description |
|------|-------------|
| `apple_pause_campaign` | Pause a campaign |
| `apple_enable_campaign` | Enable (unpause) a campaign |
| `apple_update_keyword_bid` | Update a keyword's bid amount ($0.01–$1,000) |
| `apple_pause_keyword` | Pause a keyword |
| `apple_enable_keyword` | Enable (unpause) a keyword |
| `apple_add_keywords` | Add targeting keywords (exact or broad match) |
| `apple_add_negative_keywords` | Add negative keywords at campaign or ad group level |

### Analysis & Optimization
| Tool | Description |
|------|-------------|
| `apple_analyze_performance` | Get actionable recommendations for your account |
| `apple_get_attributions` | Post-install attribution data |
| `apple_get_subscription_conversions` | Subscription conversion attribution |
| `apple_ads_optimizer` | Optimization dashboard with one-click actions |

## Getting Started

### 1. Sign up at [AppleAdsMcp.com](https://AppleAdsMcp.com)

Create an account and connect your Apple Search Ads account.

### 2. Configure Claude Desktop

Add this to your Claude Desktop config (`~/Library/Application Support/Claude/claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "apple-ads": {
      "type": "streamable-http",
      "url": "https://appleadsmcp.com/api/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_TOKEN"
      }
    }
  }
}
```

### 3. Activate your profile

Once connected, tell Claude:

> "List my Apple profiles and activate one for MCP access"

This imports your campaign data. After activation completes, you can start querying.

### 4. Start managing your ads

Ask Claude things like:

- "How are my Apple Search Ads campaigns doing this month?"
- "Which keywords are wasting money?"
- "Show me my top 10 campaigns by installs"
- "Pause keywords with spend over $50 and zero installs"
- "Compare this week's performance to last week"
- "Which search terms have the best CPI?"
- "Add 'fitness tracker' as an exact match keyword to my main ad group"

## Example Conversations

**Analyzing performance:**
> You: "Show me campaign performance for the last 30 days sorted by CPI"
>
> Claude: *Returns a table of campaigns with installs, spend, CPI, taps, impressions, and TTR*

**Finding wasted spend:**
> You: "Which search terms are wasting money?"
>
> Claude: *Shows search terms with spend but zero installs, recommends adding them as negatives*

**Taking action:**
> You: "Pause all keywords that spent over $20 with no installs in the last 14 days"
>
> Claude: *Identifies the keywords, confirms with you, then pauses them one by one*

## Transport

This server uses the **Streamable HTTP** MCP transport. All communication happens over HTTPS with bearer token authentication. No local installation or stdio process required.

## Support

- Issues: [github.com/ppcprophet/apple-ads-mcp/issues](https://github.com/ppcprophet/apple-ads-mcp/issues)
- Website: [AppleAdsMcp.com](https://AppleAdsMcp.com)

## License

MIT
