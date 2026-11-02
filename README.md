# Apogee plugin

Launch and manage Meta, TikTok and Snapchat ads in bulk from your AI assistant, with [Apogee](https://apogee.ad). Nothing is created or changed on your ad accounts until you approve the recap.

## What's inside

- **MCP connector**: `https://app.apogee.ad/mcp` (OAuth: you sign in to Apogee and choose what the assistant may do: read, launch, act).
- **Skills**:
  - `daily-ads-brief`: yesterday's performance per platform, with a CPA drift alert (read-only).
  - `launch-from-drive`: launch the new creatives of a Drive folder or a Frame.io / Dropbox link with your naming convention.
  - `cut-losing-ads`: find the ads that burn budget and prepare their pause.
  - `bridge-winners`: relaunch your best Meta ads on TikTok or Snapchat.
  - `ad-comments-insights`: what customers ask, object to and praise under your ads, turned into angles for new creatives (read-only).

## Requirements

An Apogee account (MCP included from the Pro plan; 7-day trial for €1) with your ad accounts connected.

## Network and credentials

- The only network endpoint is Apogee's MCP server, `https://app.apogee.ad/mcp` (Streamable HTTP), declared in `.mcp.json`.
- Sign-in is OAuth 2.1 with PKCE on Apogee's own consent page: the assistant receives a token for the permissions you approve (read, launch, act), revocable at any time in Apogee, Settings → MCP. The plugin stores no key, reads no local file and ships no hook, script or binary.
- Apogee calls the Meta, TikTok and Snapchat APIs with your own connected ad accounts.

## Safety

Every change is prepared first and runs only after your explicit yes: `prepare_launch` → `launch`, an action tool → `execute_action`, `prepare_bridge_transfer` → `bridge_transfer`. Ads are created paused by default. Apogee caps daily budgets and launches per ad account per day.

Docs: https://apogee.ad/developers/mcp · Privacy: https://apogee.ad/en/legal/privacy · Support: hello@apogee.ad
