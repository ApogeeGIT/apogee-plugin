---
name: daily-ads-brief
description: Brief of yesterday's (or any period's) ad performance on Meta, TikTok and Snapchat through Apogee, with an alert when a platform's CPA drifts. Use when the user asks for a daily or weekly ads report, "how are my ads doing", or to watch CPA / ROAS. Read-only.
---

# Daily ads brief (Apogee)

Read-only: never prepare or run a change from this skill. If the user then wants to act, use cut-losing-ads.

1. `list_ad_accounts` for each platform the user runs (`platform`: "meta", "tiktok", "snapchat"). Ask once which accounts to follow, then reuse them.
2. Targets: `get_business_profile` (target_cac, target_roas) on the Meta account. If none, ask the user once and offer to save it with `update_business_profile`.
3. Per platform, over the period (default: yesterday) and the 7 days before it:
   - Meta: `get_account_overview`, `get_daily_breakdown`, `get_top_performers` (best 3 and worst 3 by the user's metric).
   - TikTok / Snapchat: `get_platform_overview`, `get_platform_daily_breakdown`, `get_platform_top_performers`.
4. Write the brief, one block per platform: spend, CPA, ROAS (in that ad account's currency), the change against the 7-day average, the 3 best and 3 worst ads by name.
5. Alert when a platform's CPA is more than 30 % above its 7-day average (or the user's own threshold), and say which ads moved it.

Rules:
- Never add platforms together (each has its own currency, time zone and attribution). No cross-platform total.
- Quote numbers as Apogee returns them; say when a platform had no delivery.
- Keep it short: the user reads it on a phone.
