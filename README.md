# lgspyware.com

A developing-story consumer alert tracking the LG monitor auto-install adware
issue on Windows. **Published by [Critical Error Computing](https://www.criticalerrorcomputing.com/)**
(CEC), a custom PC builder in Humble, TX — themed to the CEC house style.

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
recommend registry or Group Policy device-metadata edits — they can affect
driver/utility delivery for other devices.

## Editorial standard

- **Not independent, and disclosed as such:** published by CEC, a PC builder; not
  affiliated with LG/Microsoft/McAfee, and not a competitor in the monitor/TV market.
- Firsthand observations are labeled as **our findings**.
- Contested characterizations (e.g. “spyware”) are attributed to the outlets that
  made them; limits of evidence (no screen-capture evidence) are stated.
- Unverified items (Dell/Alienware) are marked **not confirmed** rather than fact.

## Theme

Styled to the Critical Error Computing brand: Saira / Saira Condensed type, the
magenta `#ed2398` accent, dark surfaces, a faint grid backdrop, and a subtle glitch
on accent words. **Red is reserved for the breaking banner and warning callouts.**

## Tech

Static site served from the repository root via **GitHub Pages**.

- `index.html` — the alert (embedded Gamers Nexus video, outlet strip, by-the-numbers,
  "am I affected?", uninstall fix, developing-story timeline, sources, CEC credit)
- `styles.css` — CEC-themed responsive dark stylesheet
- `CNAME` — custom domain (`lgspyware.com`)
- `.nojekyll` — serve files as-is

## Contact

Tips: lgspyware.com@gmail.com
