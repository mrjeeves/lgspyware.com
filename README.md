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

## The August turn (Aug 3–16, 2026)

- **Aug 3** — **LG publishes its own notice** ("LG Monitor App Installer") on its South
  Africa support site. Two commitments that go past the July agreement: LG "does not plan
  to recommend McAfee or other third-party software through the Installer in future," and
  **"LG is updating the Installer so customers can decide whether they would like to
  install it."** That is the first acknowledgement by either company of the consent gap.
  It carries no ship date, version or mechanism, says nothing about the two resident
  `.inf` packages, and repeats that applications "are only installed if the customer
  chooses to proceed" — true of the apps the Installer offers, not of the Installer,
  which arrived under SYSTEM with nothing to proceed through. The same URL path 404s on
  LG's US, UK, AU, IN, SG and CA sites, and we found no coverage of it anywhere.
  Date taken from the page's structured data (`datePublished: 2026-08-03T03:00:00Z`),
  since the printed `08/03/2026` stamp is regionally ambiguous.
- **Aug 12** — The app's Microsoft Store product is updated (listing data:
  `LastUpdateDateUtc 2026-08-12`). No changelog is published; contents unknown. We have
  not re-run a first-connection test, and the site says so rather than implying otherwise.
- **Aug 16** — Our re-check: Store permissions unchanged ("uses all system resources",
  internet), `runFullTrust`, rating **1.0 across 421 ratings**; Microsoft's Tech Community
  thread quiet since Jul 25; **no press coverage since ~Jul 27**; Gamers Nexus's follow-up
  still unpublished (seven unrelated videos since the Jul 23 post, per the channel feed).

**What still has not changed:** the install, as of anything anyone can observe. LG has now
promised a choice; nobody has shown one on screen. Both delivery packages remain resident
and wired to 51 hardware IDs, Microsoft has said nothing about the device-metadata channel
(its February 2026 consent initiative covers app behaviour, not hardware-triggered
installs), and the mechanism is a Windows feature available to any vendor. The site's
framing follows this distinction — the ad was the symptom, the delivery is the story —
with the July "nobody has said the install will stop" line explicitly marked as superseded
rather than silently edited.

## Related LG record (updated Aug 16)

- **May 11, 2026** — LG's US unit **settled** the Texas AG's smart-TV ACR suit (filed Dec
  2025 against five makers): consent before collecting viewing data, pop-up and website
  disclosure, clear opt-out, no transfers to the CCP; **no admission of liability** (Korea
  Herald; the US outlets covering the settlement don't address the point either way). Cases
  against Sony, Hisense and TCL continue. The site previously presented this as a live
  allegation; it now reports the settlement and notes the remedy Texas extracted was, in
  substance, *ask first*.
- **Jul 21, 2026** — Krebs on Security: Spur found residential-proxy SDKs in **42%+ of LG
  webOS store apps**; LG says non-compliant apps will be suspended.

## September: the televisions (Sep 6–12, 2026)

- **Sep 6** — Gamers Nexus publishes the follow-up promised in July: **"216,000,000 Spy TVs"**,
  135 minutes, made with Level1Techs and independent researchers MrBruh and uturn. Retail LG
  televisions, packet captures, standby bench tests, webOS teardown. Reported findings: local
  network enumeration of devices never paired with the set (phones, watches, routers,
  thermostats, air purifiers, BMCs, PCs); names, signal strengths and channels of neighbouring
  Wi-Fi networks plus public and internal IPs; **plaintext transcripts from audio captured with
  the screen off**; capture continuing while disconnected, stored locally and sent once
  connectivity returns; content recognition sampling across inputs; roughly **4GB of ACR data a
  month** from one set. Separately, **remote code execution flaws in webOS** — TV browser renders
  a malicious page, which forges a device-pairing prompt.
- **Sep 7–11** — Coverage in Malwarebytes, The Register ("egregious invasion of privacy") and
  Tom's Hardware. **LG denies** the audio findings: voice data is processed "only when the voice
  button on the remote control is pressed and held, or when a wake word such as 'Hi LG' is
  recognized," and the TVs "do not collect or record ambient conversations." LG **confirms** the
  local network scanning as standard functionality. The RCE findings remain under responsible
  disclosure — **no CVE published, no firmware fix**, and no public response from LG.
- **Sep 12** — Our re-check of the monitor thread: LG's August 3 promise that the installer would
  ask first is **40 days old and unshipped**. The app's Store product has not been updated since
  **Aug 12** (`LastUpdateDateUtc 2026-08-12`), permissions are unchanged, rating 1.0 from **431**
  ratings. No outlet has covered the August notice, then or since.

**Why the TV material lives on its own page:** it is entirely other people's work, and the site
says so. Our bench work is the monitor; `/tvs` reports the investigation as theirs.

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
- Editing passes are logged too. The 2026-07-29 timeline entry says plainly that the
  update was a rewrite, not new reporting, so a bumped "Updated" date never implies a
  development that didn't happen.
- When the story moves against our own framing, the old line is marked superseded in
  place rather than quietly deleted. The July "nobody at either company has said the app
  will stop installing itself" paragraph now opens **"Updated Aug 16 — this is no longer
  entirely true,"** because on Aug 3 LG said it. Where LG's statement is stronger than we
  expected, it runs verbatim and gets credit before it gets scrutiny.
- Company dates are verified structurally when the printed form is ambiguous: LG's notice
  shows `08/03/2026`, which is Aug 3 in one convention and Mar 8 in another, so the date
  was taken from the page's own `datePublished` metadata rather than guessed.

## Page split (Aug 16, 2026)

The alert had grown into a wall of prose. It is now three pages with distinct jobs:

| Page | Job | Reads like |
| --- | --- | --- |
| `/` | What happened, in what order, and what to do | A dated infographic — diagram, tiles, charts, one-line timeline |
| `/story` | The monitor install: mechanism, claims, caveats, sources | A report in numbered sections |
| `/tvs` | The September TV investigation and LG's answer to it | A report in numbered sections |
| `/forensics` | The evidence off one machine | A lab report |

Every subpage carries the same furniture, so moving between them costs the reader nothing:
a ribbon, the same nav, a lead, **contents chips** (`.pagenav`), then numbered sections built from
a small shared kit — `.facts` key/value rows, `.findings` cards, `.claims` for statement-versus-
evidence, `.limits` for what the evidence doesn't cover, and a `.src` line carrying provenance as
metadata rather than as a paragraph about our process.

Rules that keep it that way:

- **Nothing on `/` runs longer than two lines.** If it needs a paragraph, it belongs on
  `/story` with a one-line pointer from the alert.
- **Numbers and dates are drawn, not described** — SVG diagram, charts, tiles and the
  timeline spine carry the load that prose used to.
- **Image slots are real slots.** `.shot-ph` placeholders mark where redacted captures go;
  dropping an `<img>` in place of the placeholder div needs no other change.
- **Volume is turned down.** The old red flashing banner is a quiet `.ribbon`; the lead
  headline is smaller; red is reserved for the affected/warning callouts.
- Legacy deep links (`/#response`, `/#august`, `/#switch`, `/#record`, `/#permissions`,
  `/#sources`) are forwarded to `/story#…` by a small script at the foot of `index.html`.

## Voice and density

The page is a consumer alert, not an essay. **Fewer words, more structure** — where a
paragraph was doing the work of a table, it became a table. Load-bearing rules:

- Every fact in the long-form version is still on the page. The 2026-07-29 pass cut
  roughly a third of the word count without dropping a claim, a date, a quote or a
  caveat.
- Hedges are stated **once**, in a dedicated `.limits` box, instead of being repeated
  in every section that touches the same limit (we have no packet capture).
- The archive (timeline before Jul 13, sourcing notes) sits behind `<details>`. The
  record stays complete; the reader doesn't pay for it up front.
- Attention-grabbing is earned by the evidence, not by adjectives. The strongest lines
  on the page are the ones that are literally true — "0 consent prompts," "the ad going
  quiet is not the software leaving."

## Theme

Styled to the Critical Error Computing brand: Saira / Saira Condensed type, magenta
`#ed2398` accent, dark surfaces, a faint grid backdrop, and a subtle glitch on accent
words. **Red is reserved for the breaking banner and warning callouts.**

Components carrying the structure (all in `styles.css`):

| Class | Use |
| --- | --- |
| `.ledger` / `.led-yes` / `.led-no` | "What changed / what didn't" split — the core distinction of the story |
| `ol.chain` + `.chain-t` | Timestamped install chain, one card per step |
| `.vchain` | App version chain (year-month build numbering) |
| `.limits` | Amber box: where our evidence stops. Used once per page |
| `.pull` | Pull quote with `<cite>` |
| `details.more` | Progressive disclosure for the timeline archive and sourcing notes |
| `.sendlist` | Two-column checklist of what to send in a tip |
| `.lead-actions` | Am I affected? / Remove it / Forensics buttons under the dek |

Code blocks wrap (`white-space: pre-wrap`) rather than scroll horizontally, so commands
stay copy-pasteable on a phone; soft wraps are not copied.

## Tech

Static site served from the repository root via **GitHub Pages**.

- `index.html` — **the alert, built as an infographic.** Ribbon + lead, the install chain
  drawn as an inline-SVG diagram (with a card fallback under 720px), a three-card state
  board, four number tiles, two small SVG charts (31/32 boots; the nine-month persistence
  bar), three evidence image slots, the scannable one-line timeline, the affected check,
  the two-step fix, the 19-model grid, GN video, outlet strip, tips, CEC credit
- `story.html` — **the monitor report**, served at `/story`: the mechanism, who it reached, LG's
  claims vs. our evidence, the August 3 notice and its status, when the ads switched on,
  permissions and evidence limits, the Windows Home registry method with its caveats, sources
- `tvs.html` — **the TV investigation**, served at `/tvs`: what the September 6 investigation
  documented, what LG denies and confirms, the unpatched webOS disclosure, the record, and the
  settings worth changing
- `forensics.html` — the forensic install report, served at `/forensics`
- `hero.jpg` — lead photo
- `og-image.jpg` — social share card (branded stopgap; swap for the redacted
  two-timestamp screenshot when captured)
- `styles.css` — CEC-themed responsive dark stylesheet
- `CNAME` — custom domain (`lgspyware.com`)
- `.nojekyll` — serve files as-is

## Contact

Tips: lgspyware.com@gmail.com
