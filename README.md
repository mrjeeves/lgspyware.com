# lgspyware.com

A developing-story news portal tracking the LG monitor auto-install adware issue on Windows.

## The story

Plugging an affected LG monitor into a Windows PC causes Windows (via the Device
Setup Manager / device-metadata feature) to silently install the **LG Monitor App
Installer** with no consent prompt. The app pushes **McAfee pop-up ads** and requests
a broad permission set (location, contacts, credentials, transactions, online
activity). Being normal installed software, it **persists after the monitor is
disconnected** — it doesn't leave when the monitor does. Guidance: if an affected LG
display was ever connected to a PC, check that machine.

Broken by **Gamers Nexus** (“DO NOT BUY: LG's Spyware TVs, Monitors, and Wiretapping
Concerns”) and covered by TechRadar, Tom's Hardware, TechSpot, PC Gamer, and others.
No official response from LG or Microsoft as of 2026-07-17.

## Recommended fix

Let the app install, then uninstall it via **Settings → Apps → Installed apps**
(remove **LG Monitor App Installer** and any unexpected **McAfee** entry), then
reboot. In our testing, once uninstalled it does not come back. We do **not**
recommend registry or Group Policy device-metadata edits — they can break
driver/utility delivery for other devices.

## Editorial standard

- Firsthand observations are labeled as **our findings**.
- Third-party reporting is linked inline and in **Sources** for verification.
- Contested characterizations (e.g. “spyware”) are attributed to the outlets that
  made them; where evidence is limited (Gamers Nexus reported no evidence of screen
  capture), the page says so.
- Unverified items (e.g. Dell/Alienware) are marked **not confirmed** rather than
  stated as fact.

## Tech

Static site served from the repository root via **GitHub Pages**.

- `index.html` — breaking-news portal (embedded Gamers Nexus video, outlet strip,
  by-the-numbers, "am I affected?", uninstall fix, developing-story timeline, sources)
- `styles.css` — responsive dark news theme
- `CNAME` — custom domain (`lgspyware.com`)
- `.nojekyll` — serve files as-is

## Contact

Tips: lgspyware.com@gmail.com
