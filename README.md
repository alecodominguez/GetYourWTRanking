# GetYourWTRanking — Triathlon Season Planner

![JavaScript](https://img.shields.io/badge/JavaScript-ES6%2B-yellow) ![No backend](https://img.shields.io/badge/backend-none%20(client--side)-lightgrey) ![License](https://img.shields.io/badge/license-MIT-green)

**[Try it live →](#)** *[https://www.alecojdr.us](https://alecojdr.us/)*

A single-file, client-side web app that parses official [World Triathlon](https://www.triathlon.org/) `.xlsx` race-result exports in-browser and computes rolling, multi-year ranking-point projections — replacing the manual spreadsheet lookups triathletes otherwise have to do by hand.

It's evolving from a pure points calculator into a broader triathlon season-planning platform, integrating with the [GetYourWhyPhy](https://github.com/alecodominguez/GetYourWhyPhy) app ecosystem.

## Why

World Triathlon ranking points determine start-list priority, qualification, and seeding across the season, but the official scoring rules — rolling windows, per-position decay, event-tier multipliers, regional strength-of-field adjustments — are genuinely complex to calculate by hand from a raw race-results spreadsheet. This tool does it instantly and consistently.

## Tech stack

Deliberately zero-framework, single-file architecture (`index.html`):

- **Core:** HTML5, CSS3, vanilla JavaScript (ES6+)
- **Spreadsheet parsing:** [SheetJS (xlsx.js)](https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js) via CDN, for parsing `.xlsx`/`.xls` files directly in-browser
- **Styling:** custom CSS properties, Flexbox, and CSS Grid, matching the official World Triathlon brand palette and typography (Inter, via Google Fonts)
- **Persistence:** client-side `LocalStorage` (`wt_ranking_calc_v1`) — no backend, no server calls; everything runs in the browser

## How the scoring engine works

- **Rolling window:** evaluates a 104-week (2-year) window, split into a Current Period (trailing 52 weeks) and a Previous Period (weeks 53–104), with the Previous Period weighted at 33.3%.
- **Top-N selection:** automatically filters and counts the top 6 scoring results per period.
- **Position decay:** applies an exact 7.5% point reduction per finishing position.
- **Event tiers:** auto-classifies across 19 official World Triathlon event tiers, from World Triathlon Championship Finals (1,250 base points) down to National Championships (50 base points).
- **Quality of Field (QFF) & bonuses:** applies fixed regional field-strength percentages across 5 continents (Africa, Americas, Asia, Europe, Oceania), plus Top-5 Continental Championship placement bonuses (25% for 1st down to 5% for 5th).

## Usage

1. Open the [live tool](#) (or `index.html` locally in any modern browser — no install required).
2. Upload your official World Triathlon `.xlsx` race-result export.
3. The tool auto-maps event titles/tiers and calculates your projected net ranking points in seconds.
4. Your data persists locally in your browser between visits (nothing is sent to a server).

## Project stats

- ~900 lines of code, ~42.6 KB, single file.
- Replaces what was previously a manual, error-prone spreadsheet process with an instant, repeatable calculation.

## Roadmap

Evolving into a full season-planning platform:

- Race scheduling across a full season
- Live API integrations for travel and hotel logistics
- Broader athlete season-planning tools, integrated with the WhyPhy app ecosystem

---

*Built by Aleco Dominguez.*
