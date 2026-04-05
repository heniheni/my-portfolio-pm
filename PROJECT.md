# Project Notes — Heni Bhungalia Portfolio

## What This Project Is

This is Heni's primary job-search portfolio, built to land a Senior PM or AI Product Manager role at $120K+. It runs alongside a Word resume (`Heni_Bhungalia_Resume.docx`) and a v2 resume with tighter bullets (`Heni_Bhungalia_Resume_v2.docx`).

## Build History

### Resume (Word .docx)
- Generated via `create_resume.py` using python-docx
- Required XML post-processing: zoom percent attribute fix in `settings.xml`, `pBdr` element ordering fix in `document.xml`
- Summary metrics: 57–60% month-1 retention, 40% delivery cadence gain, 100K+ app downloads
- Title: "AI / Technical Product Manager | Greater Seattle Area"
- V2 (`create_resume_v2.py`) applies ChatGPT suggestions: tighter bullets, stronger verbs ("Owned" instead of "collaborated"), adds "Open to Remote" to title

### Original Portfolio (index.html — dark AI theme)
- Dark-themed portfolio at `/mnt/My Portfolio/index.html`
- Includes the same chatbot widget
- Not under this git repo

### Newspaper Portfolio (this repo)
Built across multiple sessions. Key decisions and changes:

**v1 — initial concept**
- 1920s letterpress newspaper aesthetic
- UnifrakturMaguntia + Playfair Display + EB Garamond font stack
- Paper color palette: `--paper: #f4edd8`, `--ink: #1a1208`, `--sepia: #8b6914`, `--accent: #8b1a1a`
- Masthead originally said "The AI Gazette"

**v2 — readability and content fixes**
- Fixed low-contrast text
- Corrected year 2025 → 2026 throughout
- Removed all em dashes
- Reduced text density
- Made masthead font consistent (all Playfair Display 900 uppercase, no mixed blackletter + italic)
- Chat launcher changed from envelope icon to SVG chat bubble with "Ask" badge
- Ticker pauses on hover: `.ticker-wrap:hover .ticker-content { animation-play-state: paused; }`

**v3.9 (current — index.html)**
Heni's own iteration on top of v2, under git:
- Masthead name changed to "Heni Bhungalia" in UnifrakturMaguntia
- Added CSS design token system (`--sp-xs/sm/md/lg/xl`, `--r-hair/thin/mid/thick`)
- Sticky nav bar (`position: sticky; top: 0`)
- Unirac Solar metrics made specific: 22-step BOM workflow collapsed to 8 inputs, 55% reduction, 90 days
- Ticker updated with Unirac stats
- ZeroGPU given its own project card
- Cloudflare email protection active (file is live-hosted)
- Updated chatbot KB with Unirac-specific answers
- Salary answer changed to open-ended
- Overall cleaner, more consistent code structure

## Chatbot Architecture

- No API key — pre-crafted knowledge base with 17 entries
- Pattern: `{ keys: [...keywords...], ans: "..." }`
- Keyword matching via `indexOf` across all KB entries
- Opens with a "What are you hiring for?" welcome flow (6 hire-type buttons)
- `hireAnswers` stored as proper JSON (not Python dict string) to avoid JS syntax errors
- `showWelcome()` uses DOM manipulation exclusively (no innerHTML) to avoid quote-escaping bugs
- Quick chips always visible above the input area

## Unirac Solar (Key Content Decision)

Heni is NOT doing user research with field installers. She is:
- Leveraging existing product data Unirac already has
- Aligning with Unirac stakeholders to drive the redesign
- Leading a cross-functional team across multiple time zones

All copy in the portfolio and resume reflects this accurately.

## Work Authorization

H4 EAD removed from all materials. Replaced everywhere with:
> "Authorized to work in the United States · No Sponsorship Required"

## Resume Metrics (Current)

All sourced from real data (PostHog, app stores, public academic records):

- 57–60% month-1 retention on DreamCRM vs 20–30% industry average
- Onboarding improved from 17% to 50% via PostHog funnel analysis + A/B testing
- Unirac Solar: 22-step BOM → 8 inputs, 55% reduction, 90-day timeline
- 1,241+ research paper downloads in year one (DRS 2024)
- 100K+ mobile app downloads, 4.5★, 4,790+ reviews
- 40% delivery cadence improvement at AI20 Labs
- ZeroGPU roadmap contributed to pre-seed and seed funding
- 30% order conversion lift at Peapod Digital Labs

## Known Limitations / Future Work

- **Cloudflare email obfuscation**: emails render as `[email protected]` when file is opened locally (not via the live Cloudflare URL). Works correctly when deployed.
- **Photo placeholder**: `[ Portrait of the Subject ]` box exists but no actual photo yet
- **"Heni Bhungalia" in blackletter**: worth confirming the masthead font renders well visually in the browser — Latin name in UnifrakturMaguntia is unconventional
- **index.html** is the only file that should be worked on going forward (per Heni's instruction)

## Git Setup

```
Remote: https://github.com/heniheni/my-portfolio-pm.git
Branch: main
```

To push after local changes:
```bash
cd /Users/henibhungalia/Desktop/portfolio-pm-newspaper/my-portfolio-pm
git add index.html
git commit -m "your message"
git push
```
