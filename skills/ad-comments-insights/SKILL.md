---
name: ad-comments-insights
description: Read the comments under Meta ads through Apogee to find what customers ask, object to and praise, in their own words, and turn it into angles for the next creatives. Use when the user asks what people say under their ads, about objections or questions in comments, or for creative ideas from comments. Read-only.
---

# Ad comments insights (Apogee)

Read-only: this skill never replies to, hides or deletes a comment. Replying happens in Meta's tools or in the Apogee app.

1. `fetch_ad_comments(ad_account_id)` for the whole account, or with `ad_ids` / `post_ids` to look at a few ads.
2. If it returns nothing or says the comments are stale, `trigger_comment_sync(ad_account_id)` (it counts credits: only when the user asked about comments), tell the user it takes a few minutes, then read again.
3. Sort what customers say: purchase intent, questions, objections, praise, support issues, spam. Quote their exact words and say under which ads each theme comes back, and how often.
4. Turn the objections and questions into 3 to 5 angles for new creatives (hooks or short scripts in the customers' own words), ready for `launch-from-drive`.

Rules:
- Never invent or reword a comment you quote: quote it as Apogee returns it.
- Leave out names and anything personal when you summarize.
