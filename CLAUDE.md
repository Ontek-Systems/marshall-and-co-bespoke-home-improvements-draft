# Working rules for this project

## How to work with me

Talk to me like a normal person. I'll describe what I want in plain English. Just do it.

If I say "make another page," make another page — files, structure, whatever it takes. If I say "make this button blue," just change the colour. Match your effort to what I'm actually asking for.

## Speed and focus

- Act fast. Don't over-think simple things.
- Make the smallest change that does what I asked. Don't refactor or "improve" stuff I didn't mention.
- Don't reason out loud through multiple approaches before acting. Pick the obvious one and go.
- No "actually wait, let me reconsider" mid-task. If you're genuinely unsure, stop and ask me one short question.

## Finding things

- If I name a section, class, file, or ID, go straight there. Don't run a bunch of greps first.
- If you genuinely can't find what I mean, ask me — don't search blindly.

## Output

- Keep responses short. After an edit, one line on what changed and where. That's it.
- Don't explain how CSS or HTML works unless I ask.
- Don't list alternatives I didn't ask for.

## When in doubt

- Smallest change that does the job.
- Ask, don't assume.
- Stop, don't ramble.

## The design token system

This site uses custom tokens with the `gs-` prefix:
- `gs-tagline` — tagline/eyebrow text
- `gs-heading` — h2 headings  
- `gs-body` — body paragraphs
- `gs-stat-label` — stat labels
- `btn-adaptive` — buttons (adapts light/dark)
- `section-dark` — add to a `<section>` to flip it to dark mode

Use these tokens for new sections. Don't hardcode colours.

## Tech stack

Static HTML, Tailwind CSS, vanilla JavaScript. No React, no frameworks, no build steps. Python files in the root are one-off scripts — ignore them unless I ask.

## Context efficiency

- Don't re-read files you've already read this session unless I say something changed.
- Don't re-explain previous edits. Assume I remember.
- Don't summarise what you're about to do before doing it. Just do it.

## Business Context (Marshall & Co.)
- **Company:** Marshall & Co. Bespoke Home Improvements
- **Owner:** Lee Marshall
- **Vibe/Tone:** Luxury, premium, bespoke, high-end craftsmanship.
- **Contact Info:** Phone: 07940 568877 | Email: info@marshallandco.uk | Location: Perth, Scotland.
- **Always use real data:** Never use "Lorem Ipsum" or placeholder text for copy. If generating text, write high-converting, no em-dashes, text should flow naturally without em dashes, professional copy tailored to structural renovations and bespoke joinery.



## File Structure & Routing
- **New HTML pages:** Place in the root directory unless otherwise specified.
- **Components:** Reusable parts (like headers/footers) live in the `components/` folder.
- **Assets:** All new images must go in the `assets/` folder.
- **CSS:** Do not write inline styles. Use Tailwind utility classes. If a custom class is absolutely necessary, add it to `style.css`.

## SEO & Accessibility (a11y)
- **Semantic HTML:** Always use proper `<header>`, `<main>`, `<section>`, `<article>`, and `<footer>` tags.
- **Images:** Every `<img>` tag must have a descriptive, keyword-relevant `alt` attribute (e.g., "Bespoke kitchen joinery in Perth" instead of "kitchen").
- **Links & Buttons:** Must have clear `aria-labels` if the text isn't explicitly descriptive.
- **Meta Tags:** Any new HTML page must include standard SEO meta title and description tags.

## Brand Guidelines & Vibe
  - **Font Style:** Headings use **Marcus Traianus** (self-hosted OTF files in `assets/fonts/` — Regular 400, Bold 700, ExtraBold 800, Italic, declared in `style.css`). Body text uses **Montserrat** (Google Fonts CDN). Always ensure the Montserrat `<link>` tag is in the `<head>` of any HTML file you create or edit. Do NOT use any Google Font for headings — Marcus Traianus is the brand heading font.
  - **Overall Vibe:** Luxury, Premium, Bespoke, High-end Craftsmanship.

- **Color Scheme Palette:** (Apply these using Tailwind arbitrary values, e.g., `bg-[#fff9eb]`, `text-[#e8b238]`, or map them to custom CSS variables in style.css):
  - White: `#ffffff` 
  - Beige: `#fff9eb` (Excellent for luxury background sections)
  - Brown: `#5b4a36` (Rich, elegant timber/earth accent)
  - Gold: `#e8b238` (Hero highlights, primary buttons, borders, active links)
  - Dark Grey: `#303030` (Main dark backgrounds, headers, premium footers)
  - Black: `#000000` (Main body text or secondary backgrounds, or premium footers)

## Project Architecture & Directory Map

```
marshall-and-co-bespoke-home-improvements/
├── index.html                  — Homepage (main entry point, ~1056 lines)
├── style.css                   — Global styles, gs- token system, animations
├── global.js                   — Component loader, scroll reveal, header scroll, nav
├── CLAUDE.md                   — Project rules & context
│
├── components/
│   ├── header.html             — Reusable nav (logo, links, mobile menu)
│   └── footer.html             — Reusable footer (brand, contact, quick links)
│
├── assets/
│   └── imgs/
│       ├── logo.png            — Company logo (used in header/footer)
│       ├── qrcode.png          — Google review QR code
│       ├── all_imgs/           — 109 raw client WhatsApp photos (source material)
│       ├── general_imgs/       — Empty (general use)
│       ├── hero_imgs/          — Empty (reserved for hero section)
│       ├── location_imgs/      — Empty (reserved for location pages)
│       └── service_imgs/       — Empty (reserved for service pages)
│
└── pages/
    ├── location_pages/         — Empty (future location landing pages)
    └── service_pages/          — Empty (future service detail pages)
```

### Token System (style.css CSS custom properties)

Light mode defaults on `:root`:
- `--gs-fg` `#303030` | `--gs-bg` `#ffffff` | `--gs-accent` `#e8b238`
- `--gs-btn-bg` `#e8b238` | `--gs-btn-fg` `#303030`

Dark mode via `.section-dark` on a `<section>`:
- `--gs-fg` `#ffffff` | `--gs-bg` `#303030` | btn flips to outline style

### Typography
- **Headings** (`font-heading`): `'Marcus Traianus'` — self-hosted in `assets/fonts/`, weights 400/700/800 declared in `style.css`. Token: `--font-heading: 'Marcus Traianus', Georgia, serif`
- **Body** (`font-body`): `'Montserrat'` — Google Fonts CDN. Token: `--font-body: 'Montserrat', sans-serif`

### Component Loading (global.js)

`loadComponents()` fetches `components/header.html` and `components/footer.html` and injects them into `#header-placeholder` and `#footer-placeholder`. It rewrites asset paths based on current directory depth so components work from any page level.

### Current Homepage Sections (index.html)

1. Hero — full-screen slideshow (s1.png, s2.png, s3.png) with CTA
2. Trust Banner — scrolling ticker of service keywords
3. About — parallax image + stats counters
4. Services — 4-card grid (Basement, Residential, New Build, Joinery)
5. Process — horizontal scroll carousel (4 steps)
6. Before/After — interactive drag slider
7. Reviews — draggable horizontal scroll marquee
8. Google Review CTA — QR code section
9. FAQ — native `<details>` accordion with Schema.org markup
10. Footer — injected via component

### Missing Assets (referenced in HTML, not yet in repo)

- `assets/imgs/s1.png`, `s2.png`, `s3.png` — hero slideshow
- `assets/imgs/about_bg.jpg`, `about.jpg` — about section
- `assets/imgs/service1_*.jpg` through `service4_*.jpg` — service cards
- `assets/imgs/before.png`, `after.png` — before/after slider
- `assets/imgs/og-image.jpg` — Open Graph share image