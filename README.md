# Synter MCP Server

**Give your AI agent the power to manage ad campaigns across Google, Meta, LinkedIn, Microsoft, Reddit, TikTok, and more.**

The Synter MCP Server connects Claude, Cursor, Amp, and any [MCP-compatible](https://modelcontextprotocol.io/) AI client to Synter's unified advertising platform. Your agent can create campaigns, adjust budgets, add keywords, generate creatives, and pull performance metrics—all through natural conversation.

---

## Quick Start

### 1. Get Your API Key

Sign up at [syntermedia.ai](https://syntermedia.ai) and create an API key in the [Developer Settings](https://syntermedia.ai/developer).

### 2. Configure Your AI Client

**For Claude Desktop** — Add to `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "synter": {
      "command": "npx",
      "args": ["@syntermedia/mcp-server"],
      "env": {
        "SYNTER_API_KEY": "syn_your_api_key_here"
      }
    }
  }
}
```

**For Cursor** — Add to `.cursor/mcp.json` in your project:

```json
{
  "mcpServers": {
    "synter": {
      "command": "npx",
      "args": ["@syntermedia/mcp-server"],
      "env": {
        "SYNTER_API_KEY": "syn_your_api_key_here"
      }
    }
  }
}
```

**For Amp** — Add to `.amp/settings.json`:

```json
{
  "mcpServers": {
    "synter": {
      "command": "npx",
      "args": ["@syntermedia/mcp-server"],
      "env": {
        "SYNTER_API_KEY": "syn_your_api_key_here"
      }
    }
  }
}
```

### 3. Start Using It

Restart your AI client and start chatting:

> "Show me all my Google Ads campaigns"

> "Create a search campaign for 'project management software' with a $50/day budget"

> "Pause the campaign that's overspending"

---

## What Can Your Agent Do?

### 📊 Campaign Management

| Tool | Description |
|------|-------------|
| `list_campaigns` | List campaigns across all connected platforms |
| `create_search_campaign` | Create a Google Search campaign with keywords and ads |
| `create_display_campaign` | Create a Google Display campaign with images |
| `create_pmax_campaign` | Create a Performance Max campaign |
| `create_meta_campaign` | Create a Facebook/Instagram campaign |
| `create_linkedin_campaign` | Create a LinkedIn campaign for B2B |
| `create_reddit_campaign` | Create a Reddit campaign |
| `pause_campaign` | Pause any campaign |
| `update_campaign_budget` | Change daily budget |

### 📈 Performance & Analytics

| Tool | Description |
|------|-------------|
| `get_performance` | Get impressions, clicks, spend, conversions, ROAS |
| `get_daily_spend` | Daily spend breakdown by platform |

### 🎯 Keywords & Targeting

| Tool | Description |
|------|-------------|
| `add_keywords` | Add keywords to a campaign or ad group |
| `add_negative_keywords` | Block unwanted search terms |

### 🔄 Conversion Tracking

| Tool | Description |
|------|-------------|
| `create_conversion` | Set up a conversion action |
| `list_conversions` | List existing conversion actions |
| `diagnose_tracking` | Check if tracking is installed correctly |

### 🎨 Creative Generation

| Tool | Description |
|------|-------------|
| `generate_image` | AI-generate ad images (Imagen 4, Flux, SDXL) |
| `generate_video` | AI-generate video ads (Veo, Runway, Luma) |
| `upload_image` | Upload images as ad assets |

### 🔧 Utility

| Tool | Description |
|------|-------------|
| `list_ad_accounts` | List all connected ad accounts |
| `run_tool` | Run any of 140+ Synter tools directly |

---

## No Ads Experience? No Problem.

If you've never run ads before, here's what you need to know:

### What is a Campaign?

A **campaign** is like a project folder. It contains your ads, who sees them, and how much you spend.

```
Campaign: "Q1 Lead Generation"
├── Budget: $50/day
├── Targeting: USA, people searching "project management"
└── Ads: Headlines, descriptions, images
```

### What Platforms Can I Use?

| Platform | Best For | Min Budget |
|----------|----------|------------|
| **Google Ads** | People actively searching for your product | $10/day |
| **Meta (Facebook/Instagram)** | Visual products, broad audiences | $5/day |
| **LinkedIn** | B2B, enterprise, job seekers | $25/day |
| **Reddit** | Niche communities, tech-savvy users | $5/day |
| **Microsoft (Bing)** | Older demographics, B2B | $10/day |
| **TikTok** | Gen Z, entertainment, e-commerce | $20/day |

### Campaign Types Explained

**Search Campaigns** — Your ad shows when someone Googles specific keywords.
- *Example:* Someone searches "best CRM software" → Your ad appears

**Display Campaigns** — Image ads shown across websites and apps.
- *Example:* Banner ad on a news site

**Performance Max (PMax)** — Google's AI shows your ads everywhere (Search, YouTube, Display, Gmail, Maps).
- *Example:* Google figures out the best placements for you

**Video Campaigns** — Video ads on YouTube and partner sites.
- *Example:* 15-second ad before a YouTube video

### Common Terms

| Term | What It Means |
|------|---------------|
| **Impressions** | How many times your ad was shown |
| **Clicks** | How many people clicked your ad |
| **CTR** | Click-through rate (clicks ÷ impressions × 100) |
| **CPC** | Cost per click |
| **Conversions** | Desired actions (signups, purchases, etc.) |
| **ROAS** | Return on ad spend (revenue ÷ spend) |

### First Campaign Checklist

Before creating your first campaign, you'll need:

1. ✅ A landing page URL where people will go when they click
2. ✅ An idea of who you want to reach (location, interests)
3. ✅ A daily budget you're comfortable with ($10-50 to start)
4. ✅ Some headlines and descriptions for your ad

**Pro tip:** Start with a Search campaign on Google. It's the easiest to understand and shows ads to people already looking for what you offer.

---

## Example Conversations

### Create Your First Campaign

> **You:** Create a Google Search campaign for my SaaS product. Target people searching for "team collaboration software" and "project management tools". Budget is $25/day. Landing page is https://myapp.com/signup

> **Agent:** I'll create a Search campaign with those keywords. What headlines should I use? Here are some suggestions:
> - "Team Collaboration Made Simple"
> - "Project Management for Modern Teams"
> - "Start Free - No Credit Card"

### Check Performance

> **You:** How are my campaigns doing this week?

> **Agent:** Here's your performance for the last 7 days:
> 
> | Campaign | Spend | Clicks | Conversions | ROAS |
> |----------|-------|--------|-------------|------|
> | Brand Search | $142 | 89 | 12 | 4.2x |
> | Competitor Keywords | $98 | 45 | 3 | 1.5x |
> | Display Retargeting | $67 | 234 | 8 | 2.8x |
>
> The "Competitor Keywords" campaign is underperforming. Want me to pause it or adjust the targeting?

### Add Negative Keywords

> **You:** I'm getting clicks for "free project management" but we don't have a free tier. Block those.

> **Agent:** Added "free" as a negative keyword to your campaign. This will stop your ads from showing for any search containing "free".

### Generate Ad Creative

> **You:** I need a display ad image for a marketing automation product. Dark theme, professional, 1200x628.

> **Agent:** Generating your image with Imagen 4...
> 
> Created: "Marketing automation dashboard with data visualization on dark background"
> Asset saved and ready to use in your next Display campaign.

---

## Connect Your Ad Accounts

To manage ads on each platform, you'll need to connect your accounts in Synter:

1. Go to [syntermedia.ai/credentials](https://syntermedia.ai/credentials)
2. Click "Connect" next to each platform
3. Complete the OAuth flow
4. Your agent can now manage that platform

**Supported Platforms:**
- Google Ads ✅
- Meta (Facebook/Instagram) ✅
- LinkedIn Ads ✅
- Microsoft Ads (Bing) ✅
- Reddit Ads ✅
- TikTok Ads ✅
- X (Twitter) Ads ✅
- Amazon Ads ✅
- The Trade Desk ✅
- Amazon DSP ✅

---

## Advanced: Direct Tool Access

For power users, you can call any of 140+ Synter tools directly:

```
> Use run_tool to call google_ads_list_audiences
```

See the full tool list at [docs.syntermedia.ai/tools](https://docs.syntermedia.ai/tools) or ask your agent:

```
> What tools are available for LinkedIn Ads?
```

---

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `SYNTER_API_KEY` | Yes | Your Synter API key |
| `SYNTER_API_URL` | No | API URL override (default: https://syntermedia.ai) |

---

## Local Development

```bash
# Clone and install
git clone https://github.com/syntermedia/mcp-server.git
cd mcp-server
npm install

# Build
npm run build

# Run locally
SYNTER_API_KEY=syn_xxx node dist/index.js
```

---

## Troubleshooting

### "SYNTER_API_KEY not set"

Make sure your API key is in the `env` section of your MCP config. The key should start with `syn_`.

### "Invalid or expired API key"

1. Check that you copied the full key (they're long!)
2. Verify the key is active at [syntermedia.ai/developer](https://syntermedia.ai/developer)
3. Make sure the key has `tools:write` scope

### "No ad accounts connected"

You need to connect at least one ad platform:
1. Go to [syntermedia.ai/credentials](https://syntermedia.ai/credentials)
2. Click "Connect" next to Google Ads (or another platform)
3. Complete the OAuth authorization

### Tools aren't showing in Claude/Cursor

1. Restart your AI client completely (not just refresh)
2. Check the MCP server logs for errors
3. Verify the config file path and JSON syntax

---

## Resources

- **Synter Manual:** [syntermedia.ai/manual](https://syntermedia.ai/manual)
- **API Documentation:** [docs.syntermedia.ai](https://docs.syntermedia.ai)
- **Tool Reference:** [docs.syntermedia.ai/tools](https://docs.syntermedia.ai/tools)
- **Support:** [hello@syntermedia.ai](mailto:hello@syntermedia.ai)

---

## License

MIT License - see [LICENSE](LICENSE) for details.

---

<p align="center">
  <a href="https://syntermedia.ai">
    <img src="https://syntermedia.ai/logo.svg" alt="Synter" width="120" />
  </a>
  <br />
  <em>Your AI agents. Your ad campaigns. One interface.</em>
</p>
