# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file portfolio site for Heni Bhungalia, AI Product Manager. The design is a deliberate 1920s letterpress newspaper aesthetic — the ironic contrast between old-world typesetting and cutting-edge AI metrics is intentional and central to the identity.

**Only `index.html` should be edited.** All content, styles, and JavaScript live in this one file. No build step, no framework.

## Tech Stack

- Pure HTML / CSS / JS — no build tools, no dependencies, no package.json
- Fonts via Google Fonts: Playfair Display (headlines, masthead name), Inter (body)
- Deployed via GitHub Pages at `heniheni.github.io/my-portfolio-pm`; Cloudflare proxies the live URL and handles email obfuscation

## Viewing the Site

Open `index.html` directly in a browser. No server required.

```bash
open index.html
```

Note: Cloudflare email obfuscation will not work locally — email addresses will display as `[email protected]`. This is expected behavior; it works correctly on the live URL.

## Pushing Changes

```bash
git add index.html
git commit -m "your message"
git push
```

## Architecture of index.html

The file is ~1,250 lines structured in order:

1. **`<head>`** — meta tags, Google Fonts link, all CSS (~700 lines)
2. **`<body>`** — HTML sections then inline `<script>` at the bottom

### CSS Design Token System

All spacing and rule weights use tokens defined in `:root`:

```css
--sp-xs: 4px  --sp-sm: 8px  --sp-md: 16px  --sp-lg: 24px  --sp-xl: 40px
--r-hair: 0.5px  --r-thin: 1px  --r-mid: 2px  --r-thick: 3px
```

Color palette: `--ink` (dark brown), `--paper` (cream), `--sepia` (gold), `--rule` (brown), `--accent` (dark red).

### HTML Section Order

| Section | ID/Class | Description |
|---|---|---|
| Ticker | `.ticker-wrap` | Scrolling breaking-news bar; pauses on hover |
| Nav | `.nav-strip` | Sticky navigation (Work, Projects, Skills, Timeline, Contact) |
| Masthead | `.masthead` | Name, HB logo, tagline, contact info, resume download |
| Featured Story | `#work` | 3-col layout: main article + stats sidebar |
| Projects | `#projects` | ZeroGPU and secondary project cards |
| Skills | `#skills` | Classifieds-style skills grid |
| Timeline | `#chronicle` | Career history |
| Testimonials | implicit | Expandable testimonial quotes |
| Contact | `#contact` | Contact form area |
| Chatbot | `#chat-panel` | Floating chatbot widget |

### Chatbot Architecture

- No API key — pure keyword matching against a pre-crafted knowledge base
- 17 KB entries: `{ keys: [...keywords], ans: "..." }`
- Opens with a welcome flow (`showWelcome()`) offering 6 hire-type buttons (0-to-1, retention, enterprise, execution, technical depth, AI/LLM)
- `hireAnswers` is stored as a JS object (not Python dict) — quote escaping is handled via DOM manipulation, not innerHTML, to avoid bugs
- Quick chips always visible above the input

## Content Accuracy

All metrics are sourced from real data. Never alter these numbers without Heni's confirmation:

| Metric | Value |
|---|---|
| DreamCRM Month-1 Retention | 57–60% (vs 20–30% industry avg) |
| Onboarding | 17% → 50% |
| Unirac Solar BOM workflow | 22 steps → 8 inputs, 55% reduction, 90 days |
| ZeroGPU | Pre-seed & seed funding secured |
| Research downloads | 1,241+ in year one |
| Mobile app | 100K+ downloads, 4.5★ |
| Peapod conversion | 30% lift (search/discovery components, A/B tests) |
| Northeastern platform | WCAG-compliant, cleared accessibility and brand audits |

## Key Design Rules

- No em dashes anywhere in copy
- Portfolio copy is written in first person ("I built..."), never third person ("Heni built..." / "She..."). Exceptions: testimonials (others' words) and the chatbot, which speaks as Heni's assistant
- Work authorization line: "Authorized to work in the United States · No Sponsorship Required" — never mention H4 EAD
- Unirac Solar framing: Heni is leveraging existing product data and aligning stakeholders — she is NOT doing user research with field installers
- Responsive: single-column stacking on mobile via `@media (max-width: 700px)`
