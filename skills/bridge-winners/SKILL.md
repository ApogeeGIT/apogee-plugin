---
name: bridge-winners
description: Relaunch the best Meta ads on TikTok or Snapchat (or copy them to another Meta ad account) with Apogee's Bridge, after the user approves the recap. Use when the user asks to test winners on another platform, "move this ad to TikTok", or to do it every week.
---

# Bridge winning ads to another platform (Apogee)

Nothing is transferred until the user says yes to the recap. The copies are created paused by default.

1. Winners: `get_top_performers` on the Meta account (the user's metric and period). Show them and let the user pick.
2. Already bridged? `list_bridge_transfers`: say which ones already have a copy on the destination.
3. Destination: `list_ad_accounts` (platform "tiktok" or "snapchat"), `list_campaigns`, then an existing ad group / ad squad or a new one.
4. `prepare_bridge_transfer(source { platform: "meta", ad_account_id, ad_ids }, destination { platform, ad_account_id, campaign_id, adset_id | new_adset })`. `ready: false` → ask what it lists (`extra_fields`: identity, profile, URL, call to action…) and call it again.
5. Show the WHOLE recap (source ads, destination, status, identity, incompatibilities, adapted texts). Wait for the yes.
6. `bridge_transfer(plan_id, confirm: true)`, then `bridge_transfer_status` until it is finished.
7. Later: `get_bridge_stats` compares each original with its copies, each platform in its own currency.

Platform rules to tell the user before preparing: TikTok and Snapchat need a 9:16 video; Snapchat needs a public profile; TikTok texts are 100 characters without emoji; Snapchat headlines 34 characters.
