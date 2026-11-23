# Argus Creators for Claude

Find YouTube and Twitch creators for your brand from Claude: brand research, a scored creator shortlist, campaign
plans with budgets, and a creator brief, powered by [Argus](https://arguscreators.com).

## Install

**claude.ai, Claude desktop:** Settings → Customize → Plugins → **Add** → **Add marketplace** →
`lysto-gg/athena-argus-creators-plugin`, then add **argus-creators**.

**Claude Code:**

```
/plugin marketplace add lysto-gg/athena-argus-creators-plugin
/plugin install argus-creators@argus-creators
```

The first time Claude needs your Argus data it opens the Argus sign-in: enter your work email, the 6-digit code we
email you, then **Allow**. No API key is needed.

## What you can ask

- "Give me a quick look at https://www.boat-lifestyle.com" (works without signing in)
- "Find creators for https://www.tesla.com" (a full search takes a few minutes)
- "Show the campaign plans" · "Show the creator brief"
- "Remove <creator>, they're too expensive" · "Find more creators like the good ones"

## What's inside

| Part | |
|---|---|
| `argus-creators/.mcp.json` | The Argus MCP server, `https://arguscreators.com/mcp` |
| `skills/find-creators` | Glimpse or start a search, follow it, show the shortlist; refine the research and re-run |
| `skills/review-shortlist` | Compare, rate, remove, restore and select creators; add one by link; find more |
| `skills/campaign-plan` | Read and adjust campaign plans and budgets |
| `skills/creator-brief` | Read, edit or rewrite the creator brief |

## Privacy and support

[Privacy policy](https://arguscreators.com/privacy) · [Terms](https://arguscreators.com/terms) ·
hi@athenagaming.gg. Disconnect any time at arguscreators.com → Settings → Connected apps.

This repository is published from Athena Gaming's Argus codebase; please open issues here or email us.
