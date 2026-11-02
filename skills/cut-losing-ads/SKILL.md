---
name: cut-losing-ads
description: Find the ads or ad sets that burn budget on Meta, TikTok or Snapchat and prepare their pause with Apogee, run only after the user approves. Use when the user asks what to cut, kill, stop or pause, or wants a recurring check of losing ads.
---

# Cut losing ads (Apogee)

The pause is prepared first; it runs only after the user's explicit OK on the exact list.

1. The rule is the user's: ask for it once if it is not given (for example "spent more than 2× the target CPA with no purchase over the last 3 days"). Targets: `get_business_profile`.
2. Find the candidates:
   - Meta: `get_top_performers` (worst, the user's metric and period), `get_ads` / `get_adsets` for spend and results.
   - TikTok / Snapchat: `get_platform_top_performers` (worst), `get_platform_performance`.
3. Show the list: name, platform, spend, result, why it matches the rule. Ask which ones to pause.
4. Prepare only the approved ones:
   - Meta: `pause_ad`, or `pause_adset` when the ad is alone in its ad set.
   - TikTok / Snapchat: `set_platform_status` (status "paused", level ad / adset / campaign).
   Each returns an `action_id` and what will change.
5. Show what will change and wait for the yes, then `execute_action(action_id)` for each. An action is valid 24 hours and runs once.

Never pause anything the user did not approve by name. Never activate or raise a budget from this skill. One platform at a time; never add their numbers together.
