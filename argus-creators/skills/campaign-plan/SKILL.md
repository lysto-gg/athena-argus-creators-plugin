---
name: campaign-plan
description: Read and adjust Argus campaign plans. Use when the user asks about campaign plans, budgets, which creators are in a plan, prices, expected results, Athena's fee, or wants to change a plan's budget, formats, deliverables, success metric, or swap a creator.
---

# Argus campaign plans

For one search (`runId`):

1. **Read the plans:** `get_plans`. For each plan give its name and goal, the creators with format and price, the
   budget (Low, Recommended, High), Athena's fee, the total, the expected results and the past campaigns it is based on.
   If there are no plans, say so; plans are built from the Recommended creators, so a search with none has no plans.
2. **Change a plan** with `edit_plan`:
   - one plan (`planId` from `get_plans`): `formats`, `deliverables`, `successMetric`, `successTarget`, `constraints`;
   - all plans (no `planId`): `budget` (in minor units: cents or paise; null clears it) or `swap` with
     `{ "from": creatorId, "to": creatorId }` (the new creator must be in Recommended or More).
3. **Apply the edits:** `update_plans` rebuilds the plans with them. Then `get_plans` again and show what changed.

Rules:
- Money from Argus is already formatted in the brand's currency; do not convert it.
- A budget the user gives in rupees or dollars must be sent in paise or cents (multiply by 100).
