---
name: review-shortlist
description: Review and edit an Argus creator shortlist. Use when the user wants to compare creators on a search, see why a creator was picked or removed, rate creators, remove or restore them, move them between Recommended and More, pick them for outreach, or add a creator by link.
---

# Review an Argus creator shortlist

Work on one search (`runId`, from `list_searches` or the conversation).

- **See the lists:** `list_creators` with `list` = `recommended`, `more`, `saved` or `removed` (removed shows why).
- **Look closer:** `get_creator` gives the last 10 videos with views and engagement, the score parts, past brand deals,
  brand videos, safety checks and, for a removed creator, the evidence. Summarise; do not paste everything.
- **Change a creator** with `change_creator` and its `creatorId`:
  - `rate` with `rating` `good` or `not_a_fit` (optional `reason`: wrong_audience, too_expensive, content_style,
    brand_safety, or the user's words). Good-fit ratings unlock `find_more_creators`.
  - `remove` (a `reason` is required) and `restore`; `move` with `to` = `recommended` or `more`; `reorder` with a
    `position`; `select` / `unselect` for outreach; `save` / `unsave` to the workspace's saved creators.
- **Add a creator** the user knows: `add_creator` with a YouTube or Twitch channel link. It is checked like the others
  and joins More.
- **Find more like the good ones:** `find_more_creators` after at least one Good-fit rating.

Rules:
- Before removing a creator, ask why if the user did not say (for example: too expensive, wrong audience, content
  style, brand safety). The reason is what Argus learns from about what does not fit, so pass the user's own words as
  `reason`. Use a generic reason only if the user declines to give one.
- Confirm with the user before removing several creators at once; one by one is fine when they asked.
- After changes, show the new state with `list_creators` rather than assuming it.
