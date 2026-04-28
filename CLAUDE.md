# OYL Website — Project Reference

## Overview

**Own Ya Life (OYL)** is a creative company with three active projects. The website at [ownyalife.com](https://ownyalife.com) is a static HTML/CSS site — no build system, no framework, no dependencies beyond a Typekit font.

**Tagline:** Life isn't something you earn. It's something you own.
**Brand voice:** Born from Frustration. Fuelled by Rebellion.
**Contact:** contact@ownyalife.com

---

## The Three Projects

### Buy Me A Year (BMAY)
- **Type:** Documentary Film
- **URL:** ownyalife.com/bmay/
- **Tagline:** A year of freedom. A lifetime of change.
- **Description:** A documentary-led social experiment providing ordinary people with an extraordinary opportunity — a year of financial freedom to explore what they'd do if survival wasn't the barrier.

### Serbia: Are You Ready for the Future? (SAYRFTF)
- **Type:** Documentary Film
- **URL:** ownyalife.com/sayrftf/
- **Tagline:** At the turn of the millennium, students in Novi Sad used a music festival to challenge a regime. Twenty-five years later, they're back on the streets. What happened to the hope?
- **Folder:** `/sayrftf/`

### RyzeUp
- **Type:** Limited Edition · Wearable Art
- **URL:** ownyalife.com/ryzeup/
- **Tagline:** From the street. Not the system.
- **Description:** Collectible garments created from original street art photography. Each piece tied to a real wall, a real location, a specific moment in time. No restocks. No repeats.
- **Note:** Brand name is always "RyzeUp" — not RYZEUP. The `Up` is accent coloured in the hero.

---

## Brand Guidelines

### Colours
| Token | Hex |
|---|---|
| `--black` | `#000000` |
| `--white` | `#ffffff` |
| `--off-white` | `#f5f5f5` |
| `--light-grey` | `#e0e0e0` |
| `--accent` | `#FF005C` |

The accent colour is `#FF005C` — not `#FF005D`, not `#FF0058`. Exact value matters for brand consistency.

### Typography
- **Main font:** `"akzidenz-grotesk-next"` — loaded via Adobe Typekit (`https://use.typekit.net/wpi8wti.css`)
- **Condensed font:** `"akzidenz-grotesk-next-conden"` — same Typekit kit
- Both fonts must be loaded via the Typekit link; do not use system fallbacks in production.

### Type Scale (CSS variables)
```css
--text-display:  clamp(3.5rem, 9vw, 7rem);   /* hero titles */
--text-headline: clamp(1.6rem, 3.5vw, 2.4rem);
--text-large:    clamp(1rem, 1.8vw, 1.2rem);
--text-base:     1rem;
--text-small:    0.8rem;
```

### Layout
```css
--section-pad: 6rem 2rem;
--container:   720px;
```

### Design Patterns
- **Section labels:** condensed font, `0.3em` letter-spacing, uppercase, accent colour
- **Hook statements:** `border-left: 3px solid var(--accent)` with `padding-left: 1.5rem`
- **Hero eyebrow:** condensed font, accent colour, uppercase
- **Noise texture on hero:** inline SVG `feTurbulence` at `opacity: 0.045`
- **Scroll indicator:** pulsing `↓` arrow in accent colour at bottom of hero
- **Nav:** fixed, black background, `border-bottom: 1px solid #222`
- **Footer:** black background, centred, `#aaaaaa` for legal text

---

## Site Structure

```
oyl_website_master/
├── index.html              — OYL homepage
├── privacy-policy.html     — OYL privacy policy
├── og-image.png            — Shared OG image (OYL logo, used across ALL pages)
├── oyl-logo.svg            — Nav logo (colour: white OWN YA, pink YA)
├── oyl-logo-nav-dark.svg   — Nav logo dark variant (for white nav on policy pages)
├── oyl-logo-footer.svg     — Footer logo
├── oyl-logo-signature.png  — (excluded from git — client asset)
├── favicon.ico
├── favicon-32.png
├── favicon-16.png
├── apple-touch-icon.png
├── robots.txt
├── .gitignore
│
├── bmay/
│   ├── index.html
│   ├── privacy-policy.html
│   └── og-image.png        — Copy of root og-image.png (OYL logo)
│
├── sayrftf/
│   ├── index.html
│   ├── privacy-policy.html
│   └── og-image.png        — Copy of root og-image.png (OYL logo)
│
└── ryzeup/
    ├── index.html
    ├── privacy-policy.html
    └── og-image.png        — Copy of root og-image.png (OYL logo)
```

---

## OG / Social Metadata

All OG image URLs are **absolute** (required for social scrapers). All four pages use the same OYL logo image.

| Page | og:title | og:description | og:image |
|---|---|---|---|
| OYL | Own Ya Life | Life isn't something you earn. It's something you own. | `https://ownyalife.com/og-image.png` |
| BMAY | Buy Me A Year \| Own Ya Life | A year of freedom. A lifetime of change. | `https://ownyalife.com/bmay/og-image.png` |
| SAYRFTF | Serbia: Are You Ready for the Future? \| Own Ya Life | At the turn of the millennium... | `https://ownyalife.com/sayrftf/og-image.png` |
| RyzeUp | RyzeUp \| Own Ya Life | Collectible garments created from original street art photography. From the street. Not the system. | `https://ownyalife.com/ryzeup/og-image.png` |

OG image dimensions: 1200×630px.

To test OG previews on WhatsApp, paste the URL directly into a conversation (add `?v=N` with an incrementing number to bust the cache):
- `https://ownyalife.com?v=N`
- `https://ownyalife.com/bmay/?v=N`
- `https://ownyalife.com/sayrftf/?v=N`
- `https://ownyalife.com/ryzeup/?v=N`

For Facebook use: https://developers.facebook.com/tools/debug

---

## Deployment

### GitHub
- **Repo:** `https://github.com/Ownyalife/oyl-website-v2`
- **Branch:** `main`
- **Auth:** Personal Access Token embedded in remote URL (stored in local git config, not in code)

### Netlify
- **Site:** `gorgeous-trifle-734c94`
- **Domains:** `ownyalife.com` and `www.ownyalife.com`
- **Deploy trigger:** Auto-deploy on push to `main`
- **Build:** None — static site, published directly from root

### Workflow
1. Edit files in the project folder
2. `git add -A && git commit -m "description"` (via Claude's bash tool)
3. `git push` — Netlify auto-deploys within ~30 seconds

### Known Issue: index.lock
The git `index.lock` file sometimes persists between Claude sessions due to sandbox permissions. If a commit fails with "index.lock exists", run this in Terminal:
```
rm /Users/seanalger/Documents/Claude/Projects/oyl_website_master/.git/index.lock
```

---

## .gitignore

```
For Client/
oyl-logo-signature.png
.DS_Store
Thumbs.db
```

---

## robots.txt

```
User-agent: *
Allow: /

User-agent: facebookexternalhit
Allow: /
```

The `facebookexternalhit` entry is required — without it Facebook's scraper was returning 403.

---

## Key Decisions & History

- **No build system** — deliberate. Plain HTML/CSS for simplicity and speed.
- **Typekit fonts** — kit ID `wpi8wti`, loads `akzidenz-grotesk-next` and `akzidenz-grotesk-next-conden`.
- **OG images** — all pages use the OYL logo image (`og-image.png`). Relative paths were previously used but broke social scrapers — always use absolute URLs.
- **WhatsApp caching** — per-conversation, cannot be force-cleared. Use `?v=N` query parameter for fresh previews.
- **Accent colour** — was incorrectly `#FF005D` in early versions, corrected to `#FF005C` across all files.
- **RyzeUp casing** — always `RyzeUp` in display. `text-transform: none` applied to prevent uppercase override from CSS.
- **Deployment** — uses a separate repo `oyl-website-v2` (not `ownyalife`) created during the safe Option B migration.
