# lgspyware.com

Independent consumer-information site tracking the LG monitor auto-install adware issue on Windows.

## What this covers

Plugging an affected LG monitor into a Windows PC causes Windows (via the Device
Setup Manager / device-metadata feature) to silently install the **LG Monitor App**
with no consent prompt. That app surfaces **McAfee pop-up ads**. The app is normal
installed software, so it **persists after the monitor is disconnected** — including
on machines that had an affected display attached months earlier.

Publicly documented by Gamers Nexus in mid-July 2026 and covered by Tom's Hardware,
TechSpot, and PC Gamer. No official response from LG or Microsoft as of 2026-07-17.

## Recommended fix

Let the app install, then uninstall it via **Settings → Apps → Installed apps**
(remove **LG Monitor App** and any unexpected **McAfee** entry), then reboot. In
testing so far it does not reinstall. We do **not** recommend registry or Group
Policy device-metadata edits, which can affect driver/utility delivery for other
devices.

## Editorial standard

- Claims labeled **"what we tested"** are firsthand findings.
- Claims labeled **"confirmed by the press"** link to third-party reporting.
- Unverified items (e.g. other brands) are marked **not confirmed** rather than stated as fact.

## Tech

Static site served from the repository root via **GitHub Pages**.

- `index.html` — the page
- `styles.css` — styles
- `CNAME` — custom domain (`lgspyware.com`)
- `.nojekyll` — serve files as-is

## Contact

Tips: lgspyware.com@gmail.com
