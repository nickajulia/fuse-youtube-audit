# Fuse YouTube Channel Audit

A Claude-powered YouTube channel analyst that pulls real data from [Fuse](https://getfused.io) and finds the patterns most creators never see.

**What it finds:**

- Your top 5 vs bottom 5 videos and the packaging pattern separating them
- Your format split and which format is carrying the channel
- The title formula hiding in your best performers
- Where you're spending uploads on content that gets engagement but not reach

## Setup (5 minutes)

### 1. Get a Fuse API key

1. Create a free account at [getfused.io](https://getfused.io)
2. Go to **Account > Developer** tab
3. Click **Create Key** and copy it (you won't see it again)

### 2. Connect Fuse to Claude

**Claude Code (terminal):**

```bash
claude mcp add fuse -- env FUSE_API_KEY=fuse_sk_your_key_here npx -y fuse-mcp
```

**Claude Desktop:**

Open your Claude Desktop config file:
- Mac: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`

Add this to the `mcpServers` section:

```json
{
  "mcpServers": {
    "fuse": {
      "command": "npx",
      "args": ["-y", "fuse-mcp"],
      "env": {
        "FUSE_API_KEY": "fuse_sk_your_key_here"
      }
    }
  }
}
```

Restart Claude Desktop after saving.

### 3. Run your audit

**Claude Code:** Clone this repo and start Claude in the directory. The `.mcp.json` and `youtube-audit.md` are picked up automatically. Just say:

> "Run a YouTube audit on @channelname"

**Claude Desktop / Claude.ai:** Create a new Project. Paste the contents of `youtube-audit.md` into the Project Instructions. Then ask:

> "Run a YouTube audit on @channelname"

## What you get

A structured report covering:

1. **Packaging pattern** between your best and worst performers, with the exact view multiplier
2. **Format breakdown** showing which content type carries your channel vs where you're over-investing uploads
3. **Title formula** extracted from your top 10, with a count of how often you actually use it
4. **Hidden gems** with high engagement but low reach, plus repackaging suggestions

## Going deeper

The free audit uses Fuse's public data layer. [Fuse Pro](https://getfused.io/pricing) adds:

- **Outlier scores** with exact multipliers for every video
- **Topic Intelligence** showing content gaps with proven demand in your category
- **Category Benchmarks** ranking your channel against peers your size
- **AI Video Ideas** generated from your winning formula and topic gaps
- **Audience Demographics** showing who's actually watching

## Built with

- [Claude](https://claude.ai) for analysis
- [Fuse](https://getfused.io) for YouTube creator data
- [Model Context Protocol](https://modelcontextprotocol.io) connecting the two
