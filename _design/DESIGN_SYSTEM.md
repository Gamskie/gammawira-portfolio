# Ember Design System v2

**Owner:** Gamma Wira Wibowo
**Locked:** 19 Mei 2026 sore
**Scope:** All pages under `gamskie.github.io/gammawira-portfolio/`

This is the single source of truth for visual identity. If a token isn't here, it shouldn't ship.

---

## North star

**Editorial Premium B2B.** Think Stripe, Linear, Vercel — generous whitespace, strong typographic hierarchy, restrained color, magazine-style rhythm. Confident without being corporate.

The system stays warm because the brand is a 14-year manufacturer (PT PSN) shipping a natural commodity to importers in 14 countries. We're not a SaaS, we're not a startup pitch — we're a real operator who happens to ship clean docs and a clean website.

---

## Palette

The product is **coconut charcoal**. The palette honors that.

| Token | Hex | Use |
|---|---|---|
| `--ink` | `#1a1715` | Deep warm charcoal — dark surfaces, body text on cream |
| `--smoke` | `#2a2522` | Elevated card on dark backgrounds |
| `--paper` | `#faf7f0` | Warm ivory — primary cream surface |
| `--paper-2` | `#f3ecdb` | Recessed cream — alternating sections |
| `--paper-3` | `#ece2cc` | Deeper cream tint — emphasis blocks |
| `--ember` | `#c8643a` | Warm ember orange — single accent for CTAs, eyebrows, links |
| `--ember-deep` | `#a14d28` | Hover state |
| `--ember-soft` | `#e9b48f` | Subtle ember tint on dark surfaces |
| `--ember-tint` | `#f7e6d8` | Background wash for ember-marked pills |
| `--ash` | `#5e564f` | Muted text on cream |
| `--ash-soft` | `#8a8077` | Fine print on cream |
| `--cream-muted` | `rgba(250,247,240,0.72)` | Muted text on dark |
| `--line-cream` | `#e6dcc4` | Hairlines on cream |
| `--line-dark` | `rgba(250,247,240,0.10)` | Hairlines on dark |

**Rules:**

- Ember is used SPARINGLY. One accent per screen-fold maximum.
- Never combine `--ember` with cyan/teal/blue accents. Single accent system.
- Status colors (ok/warn/danger) only inside data UI (badges, results) — never decoration.

---

## Type

Three families. Each does one job.

| Family | Role | Why |
|---|---|---|
| **Fraunces** | Display (hero, section heads, pull-quotes, stat values) | Variable serif with optical-size axis — editorial gravitas, distinctive without being precious |
| **Inter** | UI (body, nav, buttons, labels) | The most legible neutral sans. Used everywhere except where Fraunces or mono is specified. |
| **JetBrains Mono** | Mono (eyebrows, labels, code, fineprint) | Crisp ligatures, reads as "engineering" not "code-bro" |

**Load order:**

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght,SOFT,WONK@0,9..144,400;0,9..144,500;1,9..144,400&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

**Type scale (clamped for fluid response):**

| Class | Size | Line | Tracking | Use |
|---|---|---|---|---|
| `.t-hero` | clamp(48px, 7vw, 96px) | 1.0 | -0.03em | Hero h1 |
| `.t-display` | clamp(36px, 5vw, 64px) | 1.05 | -0.025em | Major section h2 |
| `.t-h2` | clamp(28px, 3.6vw, 44px) | 1.1 | -0.02em | Section h2 |
| `.t-h3` | clamp(22px, 2.4vw, 28px) | 1.2 | -0.01em | Sub-section |
| `.t-h4` | 20px | 1.3 | -0.005em | Card title |
| `.t-lead` | clamp(18px, 1.8vw, 22px) | 1.55 | — | Lead paragraph |
| `.t-body` | 17px | 1.65 | — | Body |
| `.t-small` | 14px | 1.55 | — | Tight body |
| `.t-eyebrow` / `.eyebrow` | 11.5px | — | 0.18em (mono) | Section label |

---

## Spacing — 8pt grid

| Token | px | Common use |
|---|---|---|
| `--s-1` | 4 | hairline gap |
| `--s-2` | 8 | inline gap (icon ↔ text) |
| `--s-3` | 12 | input padding |
| `--s-4` | 16 | small stack gap |
| `--s-5` | 24 | section internal |
| `--s-6` | 32 | card padding |
| `--s-7` | 48 | tight section |
| `--s-8` | 64 | section vertical |
| `--s-9` | 96 | major section vertical (default `.section`) |
| `--s-10` | 128 | loose hero / showcase |

**Default section padding = 96px top/bottom on desktop, 48px on mobile.**

---

## Components

### Button

| Variant | When |
|---|---|
| `.btn-primary` | Primary CTA (ember on whatever surface) |
| `.btn-ghost-light` | Secondary on cream (ink outline) |
| `.btn-ghost-dark` | Secondary on dark (cream outline) |
| `.btn-solid-dark` | Secondary on cream that wants more weight |

All buttons are pill-shaped (`--r-full`), 14px Inter 600, with a `.arrow` SVG that translates on hover.

### Card

| Class | Surface |
|---|---|
| `.card` | Cream surface, hairline border, lift on hover |
| `.card-flat` | Recessed cream (paper-2), no lift |
| `.card-dark` | Smoke on ink, hairline white border |

### Stat row

Editorial stat strip — NO boxes, just two hairlines with vertical dividers between stats. Uses Fraunces 40px for the value, mono uppercase 11px for the label. Replaces the old "border-left bar" stat bricks.

### Pill

`.pill` — tiny tag with mono text, hairline border, pill radius. Used for chips, certs, country tags.

`.pill-ember` — ember-tinted variant for emphasis (e.g. "New").

### Nav

`.nav` (cream blur) or `.nav-dark` (ink blur). Sticky, 64px tall, hairline bottom border. Brand mark uses Fraunces with an ember `.dot`.

### Pull-quote

`.pullquote` — Fraunces italic with WONK + SOFT axes engaged. Hairline rules top + bottom. Used for testimonials, key reframings, manifesto lines.

---

## Page surface patterns

**Don't apply colors directly.** Use the surface helpers:

- `.surface-ink` — ink background, cream text, ember accent
- `.surface-paper` — paper background, ink text, ember accent
- `.surface-paper-2` — recessed paper (alternating sections)

The system flips card / pill / button / stat styles based on surface context. You compose pages by alternating surfaces, not by repeatedly setting colors.

**Typical page rhythm:**

```
[nav]
[hero          surface-ink]
[problem       surface-paper]
[solution      surface-paper-2]
[proof         surface-ink]
[pricing       surface-paper]
[faq           surface-paper-2]
[contact       surface-ink]
[footer        surface-ink]
```

---

## Voice — quick rules for copy

(Brand voice docs cover this in detail. Reminders only.)

- Lowercase Bahasa Indonesia opener if writing to ID audience
- First-person ("I build…" / "Saya bangun…") not third-person corporate
- Specifics > superlatives: "12.5 ton/day capacity" beats "high capacity"
- Never "industry-leading", "best-in-class", "world-class"
- Em-dash usage = restrained. One per paragraph max.

---

## What we're NOT

The system is intentionally NOT:

- ❌ Glow effects / neon / cyber — feels 2020-template dev portfolio
- ❌ Multiple radial gradients on hero backgrounds
- ❌ Drop-shadowed cards everywhere (use hairlines)
- ❌ Aurora / mesh gradient hero backdrops
- ❌ Tailwind default palette (slate-200, blue-600, etc.)
- ❌ Emoji decoration in headlines
- ❌ "AI shimmer" / animated gradients on CTAs

---

## Inspiration anchors

When stuck, look at: **Stripe.com** (rhythm), **Linear.app** (precision), **Vercel.com** (clarity), **Aesop.com** (editorial heritage product), **Patagonia.com** (warm trade brand), **The Verge** (display-serif headlines).

---

*Locked 19 Mei 2026 sore by Gamma. Tokens live in `assets/system.css`. Update only when a recurring need surfaces that the existing system can't express.*
