# lgspyware.com

A developing-story consumer alert tracking the LG monitor auto-install adware
issue on Windows. **Published by [Critical Error Computing](https://www.criticalerrorcomputing.com/)**
(CEC), a custom PC builder in Humble, TX, and themed to the CEC house style.

## The story

Connecting an affected LG monitor to a Windows PC causes Windows Update to deliver
two LG packages that are signed as drivers but contain no driver code. One instructs
Windows to fetch the **LG Monitor App** (`LGElectronics.LGMonitorApp`) from the
Microsoft Store, which the **SYSTEM** account installs within seconds, with no prompt
and no consent. The app pushes **McAfee pop-up ads**. Because it is normal installed
software delivered through a resident driver-store package, it **persists after the
monitor is disconnected**: on our own machine the install landed at connection time
(2025-09-30) and Windows was still updating the app as SYSTEM nine months later
(2026-07-09), long after the panel was unplugged.

Broken by **Gamers Nexus** ("DO NOT BUY: LG's Spyware TVs, Monitors, and Wiretapping
Concerns") and covered by TechRadar, Tom's Hardware, TechSpot, PC Gamer, and others.
No official response from LG or Microsoft as of 2026-07-17. The full minute-by-minute
install chain is published at **`/forensics`**.

## Recommended fix (two layers)

1. **Remove the app.** Settings → Apps → Installed apps → uninstall *LG Monitor App*,
   or `Get-AppxPackage -AllUsers LGElectronics.LGMonitorApp | Remove-AppxPackage -AllUsers`.
2. **Remove LG's two delivery packages** so the machine can't re-arm: find
   `lgmonitorappextension.inf` and `lgmonitorappsoftwarecomponent.inf` in
   `pnputil /enum-drivers`, then `pnputil /delete-driver oemXX.inf /uninstall` each.

This is surgical and leaves every other device's drivers and companion software
intact. We do **not** recommend the Group Policy device-metadata edits as a primary
fix (the documented delivery rode the Windows Update driver channel, which those
policies don't gate); a tested Windows Home registry method is in progress.

## Editorial standard

- **Not independent, and disclosed as such:** published by CEC, a PC builder; not
  affiliated with LG/Microsoft/McAfee, and not a competitor in the monitor/TV market.
- Firsthand observations are labeled as **our findings**; the forensic report backs them.
- Contested characterizations (e.g. "spyware") are attributed; limits of evidence
  (no screen-capture evidence) are stated.
- Corrections are made on the record: an earlier "installed ten months after the panel
  was disconnected" reading was superseded by full log analysis showing the install
  happened at connection in Sep 2025, with the July 2026 activity being SYSTEM
  self-update and Store servicing. The persistence finding stands and is stronger.

## Theme

Styled to the Critical Error Computing brand: Saira / Saira Condensed type, magenta
`#ed2398` accent, dark surfaces, a faint grid backdrop, and a subtle glitch on accent
words. **Red is reserved for the breaking banner and warning callouts.**

## Tech

Static site served from the repository root via **GitHub Pages**.

- `index.html` — the alert (GN video, by-the-numbers, "am I affected?", "the switch,"
  two-layer fix, 19-model trigger list, developing timeline, sources, CEC credit)
- `forensics.html` — the forensic install report, served at `/forensics`
- `og-image.png` — social share card (branded stopgap; swap for the redacted
  two-timestamp screenshot when captured)
- `styles.css` — CEC-themed responsive dark stylesheet
- `CNAME` — custom domain (`lgspyware.com`)
- `.nojekyll` — serve files as-is

## Contact

Tips: lgspyware.com@gmail.com
