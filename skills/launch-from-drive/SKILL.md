---
name: launch-from-drive
description: Launch the new creatives of a Google Drive folder (or a Frame.io / Dropbox link) on Meta, TikTok or Snapchat with Apogee, using the account's naming convention, after the user approves the full recap. Use when the user asks to launch, upload or test new creatives, or to check a "to launch" folder every day.
---

# Launch new creatives from a folder (Apogee)

Nothing is created until the user says yes to the whole recap. Ads are created paused unless the user asks otherwise.

1. `list_ad_accounts` (ask which one if there are several), then the folder: `list_drive_folder` for Drive; `import_link` + `import_status` for Frame.io, Dropbox or a Drive file. TikTok and Snapchat launches need the files imported into Apogee first (`import_link`).
2. Skip what already went out: `list_launches` on that ad account; tell the user which files look already launched and ask before including them.
3. `get_launch_questions(ad_account_id)` and ask its `to_ask` questions ONE TOPIC AT A TIME, with the choices it returns (campaign, structure, naming convention, identity, audience, tracking, destination, budget, launch status). Never answer for the user. For a recurring task, ask once and save the answers in your notes for next time, but still show the recap every time.
4. `get_launch_questions` again with the files: it proposes the ads (ad name ← files). Show them; let the user link, split, rename or group them; then send `grouping_confirmed: true`.
5. Texts: one primary text, headline and description per ad, in the language of the targeted market (from the video's transcript when you can). Get them validated.
6. `prepare_launch` with every answer. `ready: false` → ask what it lists, call it again. Show the WHOLE recap. Wait for an explicit yes.
7. `launch(plan_id, confirm: true)`, then `launch_status` until it is finished. Report what was created (paused).
8. Errors: follow `launch_status`'s `what_to_do`. With `retry: "after_fix"`, never launch again before the user says the cause is fixed.

Limits: a plan is valid 24 hours and runs once; 25 launches per ad account per day; a naming convention is used only when it reads every file, otherwise files are grouped by hand like the app does.
