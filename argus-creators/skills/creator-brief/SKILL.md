---
name: creator-brief
description: Read and edit the Argus creator brief for a search. Use when the user asks for the creator brief, talking points, dos and don'ts, the brief link to send creators, or wants to change or rewrite the brief.
---

# Argus creator brief

For one search (`runId`):

1. **Read it:** `get_brief` returns the problem, solution, proof, facts, who it is for, talking points, dos and don'ts,
   the public link (`publicUrl`, safe to send to creators) and the state of its two example videos.
2. **Edit one part:** `edit_brief` with `field` and `value`:
   - `problem`, `solution`, `whoFor`: text;
   - `proof`: `{ "text": ..., "sourceUrl": ... }`;
   - `facts`, `talkingPoints`, `dos`, `donts`: a list of short lines (send the whole list, not one item).
3. **Rewrite it from the research:** `regenerate_brief`. This replaces the user's edits to the brief, so confirm first.

Rules:
- Keep the brand's facts as Argus has them; do not add claims the research does not support.
- Show the public link after edits so the user can check the page.
