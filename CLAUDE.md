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
  - **Heading font (`font-heading`):** **Cormorant** — self-hosted OTF in `assets/fonts/Cormorant/`. Weights declared in `style.css`: 400 Regular, 400 Italic, 600 Semi, 700 Bold, 700 Bold Italic, 800 (mapped to Bold file). Token: `--font-heading: 'Cormorant', Georgia, serif`.
  - **Body font (`font-body`):** **Montserrat** — Google Fonts CDN, weights 300–800. Token: `--font-body: 'Montserrat', sans-serif`. Always include the Montserrat CDN `<link>` in the `<head>` of any new HTML file.
  - **Accent/script font (`font-script`):** **Elicit Script** — self-hosted `assets/fonts/ElicitScript-SemiBold.otf`. Used ONLY for section kickers and the Lee Marshall signature. Never apply to body text or headings. Token: `--font-script: 'Elicit Script', cursive`.
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
├── index.html                  — Homepage (~1891 lines)
├── style.css                   — Global styles, gs- token system, animations (~638 lines)
├── global.js                   — Component loader, scroll reveal, header scroll, nav (~194 lines)
├── CLAUDE.md                   — Project rules & context
│
├── components/
│   ├── header.html             — Fixed nav: top info banner + logo + links + mobile menu
│   └── footer.html             — Brand, contact details, quick links, copyright
│
├── assets/
│   ├── fonts/
│   │   ├── ElicitScript-SemiBold.otf   — Accent/script font (kickers, signature)
│   │   └── Cormorant/                  — Heading font (Regular, RegularItalic, Semi, Bold, BoldItalic + subfamilies)
│   └── imgs/
│       ├── logo.png                    — Company logo
│       ├── qrcode.png                  — Google review QR code
│       ├── og-image.jpg                — Open Graph / social share image
│       ├── all_imgs/                   — 109 raw client WhatsApp photos (source material)
│       ├── general_imgs/               — about.jpg, about_bg.jpg, before.jpg, after.jpg
│       ├── hero_imgs/                  — hero1.jpg, hero2.jpg, hero3.jpg
│       ├── location_imgs/              — Empty (future location pages)
│       └── service_imgs/               — service1.jpg – service4.jpg
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
- **Headings** (`font-heading`): `'Cormorant'` — self-hosted in `assets/fonts/Cormorant/`. Token: `--font-heading: 'Cormorant', Georgia, serif`
- **Body** (`font-body`): `'Montserrat'` — Google Fonts CDN, weights 300–800. Token: `--font-body: 'Montserrat', sans-serif`
- **Script/Accent** (`font-script`): `'Elicit Script'` — self-hosted in `assets/fonts/`. Token: `--font-script: 'Elicit Script', cursive`. Use only for kickers and the Lee Marshall signature.

### Component Loading (global.js)

`loadComponents()` fetches `components/header.html` and `components/footer.html` and injects them into `#header-placeholder` and `#footer-placeholder`. It rewrites asset paths based on current directory depth so components work from any page level.

### Current Homepage Sections (index.html)

1. **Hero** — 3-slide content carousel (lerp-free CSS transitions). Slides: Welcome / Craftsmanship / Conversion (form). Background images cycle independently. Animated mouse scroll indicator + slide dots. Timer stops permanently on slide 3 or form focus.
2. **Trust Banner** — scrolling ticker of service keywords (marquee animation)
3. **About** — parallax background image, two-column text + floating portrait image (desktop), stat counters (20+ years, 5-Star, 100% personally led), Lee Marshall script signature with underline
4. **Gallery** (`#gallery-snippet`) — sticky lerp-scroll card carousel, mirrors Process section layout. Dark bg, fade gradients, dots, "View Full Gallery" button. Cards reference `all_imgs/` WhatsApp photos.
5. **Services** (`#services-section`) — 4 alternating full-width rows (image + text), parallax on images, section number 03, sub-cards numbered 01–04 internally
6. **Inspiration** (`#inspiration-banner-section`) — full-bleed bg image with parallax, frosted glass card anchored right, section number 04
7. **Process** (`#process-section`) — sticky card stack ("How We Work"), 4 cards reveal on scroll, lerp JS, dots, "Scroll to explore" hint anchored at bottom. Section number 05.
8. **Testimonials** (`#testimonials`) — review cards + Google QR code CTA. Section number 06/07.
9. **FAQ** (`#faq`) — native `<details>` accordion, Schema.org FAQ markup. Section number 08.
10. **Footer** — injected via component

### Known Outstanding Issues

- **Before/After slider JS exists** (`ba-slider`) but the HTML section was never built — dead code at bottom of file
- **Unused Cormorant subfamilies** still in `assets/fonts/Cormorant/` (CormorantInfant, CormorantSC, CormorantUnicase, CormorantUpright + undeclared weights) — ~25 files, ~3.5MB unused
- **Gallery scroll-wrapper height hardcoded** — `style="height: 420vh;"` inline on `#gallery-scroll-wrapper`