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
Concerns") and covered by TechRadar, Tom's Hardware, TechSpot, PC Gamer, The Register,
Engadget, Gizmodo, and others. The full minute-by-minute install chain is published at
**`/forensics`**.

## The response (July 19–24, 2026)

- **Jul 18–19** — Epic CEO Tim Sweeney replies to an existing user thread at 21:47 UTC on
  Jul 18, tagging Microsoft's Windows chief; **Pavan Davuluri** answers at 05:04 UTC on
  Jul 19 ("Thanks, Tim. The team is looking into it").
- **Jul 21** — **Windows Latest** (sole source) reports the app's Store listing carrying
  an **"Additional App – McAfee"** changelog entry added in a recent update, and notes
  that neither Microsoft nor LG had said anything publicly as of that writing.
- **Jul 22** — LG emails a statement to outlets that had sought comment (Windows Latest,
  The Register, TechRadar, PCGamesN): McAfee "is never installed without the user's
  explicit consent," "under no circumstances" automatically, and the installer "does not
  access, collect, or transmit any customer personal data." The same day, Davuluri:
  *"We've connected with the team at LG and as an immediate next step, they have agreed
  to disable the McAfee pop-up from their app."*
- **Jul 23** — Gamers Nexus says a follow-up is coming, with security researchers,
  network experts, and lawyers reading ~40,000 words of LG agreements.
- **Jul 24** — The Register reports McAfee references removed from the Store listing.

**What did not change:** the automatic install. No commitment from either company
covers it. Both delivery packages remain resident and wired to 51 hardware IDs, the
consent gap is untouched, and the mechanism is a Windows feature available to any
vendor. The site's framing follows this distinction — the ad was the symptom, the
delivery is the story.

## Recommended fix (two layers)

1. **Remove the app.** Settings → Apps → Installed apps → uninstall *LG Monitor App*,
   or `Get-AppxPackage -AllUsers LGElectronics.LGMonitorApp | Remove-AppxPackage -AllUsers`.
2. **Remove LG's two delivery packages** so the machine can't re-arm: find
   `lgmonitorappextension.inf` and `lgmonitorappsoftwarecomponent.inf` in
   `pnputil /enum-drivers`, then `pnputil /delete-driver oemXX.inf /uninstall` each.

This is surgical and leaves every other device's drivers and companion software
intact. We do **not** recommend the Group Policy device-metadata edits as a primary
fix (the documented delivery rode the Windows Update driver channel, which those
policies don't gate).

**Windows Home hardening** (published 2026-07-25, explicitly labeled as not yet
verified on our own hardware) — elevated prompt, then reboot:

```
reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\Device Metadata" /v PreventDeviceMetadataFromNetwork /t REG_DWORD /d 1 /f
```

Equivalent UI path on any edition: System → About → Advanced system settings →
Hardware → Device Installation Settings → No. Same cost as the policy (no vendor
companion software arrives automatically anywhere; drivers keep flowing) and the same
limit (it does not gate the driver channel the documented install used).

## Editorial standard

- **Not independent, and disclosed as such:** published by CEC, a PC builder; not
  affiliated with LG/Microsoft/McAfee, and not a competitor in the monitor/TV market.
- Firsthand observations are labeled as **our findings**; the forensic report backs them.
- Contested characterizations (e.g. "spyware") are attributed; limits of evidence
  (no screen-capture evidence, **no network capture**) are stated. LG's denial that
  the app collects personal data is reported and left open, because we have no traffic
  evidence either way — the site says so in both the claim comparison and the
  permissions section rather than letting the permission list imply observed
  collection.
- Company statements get a fair reading before a critical one. LG's denial is
  addressed on its own terms: it is accurate about McAfee and silent about the
  auto-install of LG's own app, and the page says exactly that.
- **Sources are fetched, not summarized.** After a first pass sourced from search
  results, every quote, date and URL was re-verified against the primary pages. That
  pass caught: two 404 source links, a false attribution of the Store changelog to The
  Register (it is a Windows Latest exclusive), LG's statement misdated a day early, an
  omitted LG denial sentence, a Gamers Nexus quote that lives in a different post than
  the one cited, and an overstatement of what the device-metadata policy blocks. Search
  summaries also asserted a "July 13" remediation date that no fetched page supports —
  documented on the page under "claims we checked and did not publish."
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

- `index.html` — the alert (latest-update band, GN video, by-the-numbers, "am I
  affected?", LG's claims vs. our evidence, "the switch," two-layer fix + Windows Home
  registry method, 19-model trigger list, developing timeline, sources, CEC credit)
- `forensics.html` — the forensic install report, served at `/forensics`
- `hero.jpg` — lead photo
- `og-image.jpg` — social share card (branded stopgap; swap for the redacted
  two-timestamp screenshot when captured)
- `styles.css` — CEC-themed responsive dark stylesheet
- `CNAME` — custom domain (`lgspyware.com`)
- `.nojekyll` — serve files as-is

## Contact

Tips: lgspyware.com@gmail.com
