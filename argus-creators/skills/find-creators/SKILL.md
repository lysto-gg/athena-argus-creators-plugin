---
name: find-creators
description: Find YouTube and Twitch creators for a brand or product with Argus. Use when the user wants creators, influencers or a creator shortlist for a website, brand or product, asks to start or check an Argus search, or wants to correct the brand research, products or budget a search is based on.
arguments: [website]
---

# Find creators for a brand with Argus

The user gave a brand website ($website), or one is in the conversation. Use the Argus tools.

1. **Check for an existing search first.** Call `list_searches`. If this brand's website already has a recent search,
   use its `runId` instead of starting a new one (a new search uses one of the workspace's daily searches).
2. **No search yet:** call `start_search` with the website. It returns a `runId`. Tell the user a full search takes a
   few minutes (brand research, then finding and scoring creators, then plans and a brief).
   - If the user only wants a quick look, or is not signed in, use `glimpse_brand` instead: the company, its products
     and prices, and how many creators Argus can match, in under a minute.
3. **Follow the search** with `get_search` and its `runId`. While `status.phase` is `running`, say which step it is on
   and check again; do not invent results. If it is `failed`, say which step and offer `retry_step` for it.
4. **When it is done**, show the top creators from `creators.recommended` (then `more`): name, platform, followers,
   fit, the one-line reason, and the price range. Give the `link` so the user can open the search in Argus.
5. Offer next steps: look closer at a creator (`get_creator`), rate or remove creators (the review-shortlist skill),
   the campaign plans (`get_plans`), or the creator brief (`get_brief`).

## Refine the search

If the user says the brand research is wrong or wants a different focus, change what the search is based on with
`edit_search` (`entity` and `field`), then run it again:
- `brand`: `name`, `market` (US or IN), `hq`, `summary`;
- `product` (`id` from `get_search`): `name`, `url`, `priceMinor`, `inFocus` (value true to make it the product in
  focus), `delete`; no `id` with field `add` and value `{name, url, priceMinor}` adds one;
- `fact` or `keyword` (`id` from the research lists): `value` (new text) or `delete`; no `id` with field `add` adds one;
- `budget`: `brandSetMinor` (the user's budget in cents or paise; null clears it).

When the answer says `updateNeeded`, call `update_search` with the `runId`: it starts a new run with the edits and
returns its `runId`; follow that one with `get_search` as above.

Rules:
- Never claim a creator is a good fit beyond what Argus returned; quote its reason line.
- Prices are ranges from Argus (open to ceiling); say they are estimates.
- If a tool answers that sign-in is needed, ask the user to connect Argus, then retry the same call when they say so.
