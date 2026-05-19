# Slate Design System v3

**Owner:** Gamma Wira Wibowo
**Locked:** 19 Mei 2026 sore (v3 — replaces Ember v2)
**Scope:** All pages under `gamskie.github.io/gammawira-portfolio/`

This is the single source of truth for visual identity. If a token isn't here, it shouldn't ship.

---

## Why v3 (and what changed from v2 Ember)

**v2 problem:** Ember warm-cream + orange + serif read like "premium B2B/trade" — the same lane as pet-acc.com, Aesop, Patagonia, half of the warm-trade B2B internet. For an AI/automation specialist portfolio, that visual signal points at the wrong category. Gamma flagged this directly — "kurang kreatif."

**v3 answer:** Engineered Editorial. Cool slate-graphite surfaces, porcelain off-white (cooler than warm cream), acid lime accent (not orange), Spectral display serif (sharper, more contemporary than Fraunces), and mono-prominent UI chrome (nav links, buttons, badges all JetBrains Mono in uppercase).

The result reads as "engineering meets craft" rather than "retail trade." Distinct from pet-acc.com without abandoning the editorial discipline that makes the system work.

---

## North star

**Engineered Editorial.** Cool, sharp, considered. Think Vercel × Spectral × an architect's drafting studio. Generous whitespace, strong typographic hierarchy, restrained color (one accent, used sparingly), mono UI chrome that signals engineering without resorting to terminal/code-bro cliches.

---

## Palette

The product is **AI automation services** (engineering positioning) on the portfolio side. PSN Export is also rolled into the same system so all 4 pages share one identity — buyers/visitors who land on multiple pages get coherence.

| Token | Hex | Use |
|---|---|---|
| `--ink` | `#1c2429` | Deep cool slate-graphite — dark surfaces, body text on porcelain |
| `--ink-elevated` | `#232c33` | Slightly raised dark surface |
| `--smoke` | `#2a343b` | Card on dark backgrounds |
| `--paper` | `#f5f3ee` | Porcelain — primary off-white surface (cooler than cream) |
| `--paper-2` | `#ebe7df` | Recessed porcelain — alternating sections |
| `--paper-3` | `#dfd9cd` | Deeper tint — emphasis blocks |
| `--ember` | `#b3c80a` | Acid lime — single accent. *Token name kept for backwards compat with v2 CSS rules; semantic meaning is "primary accent."* |
| `--ember-deep` | `#8fa008` | Hover state |
| `--ember-soft` | `#d8ec78` | Soft lime on dark surfaces |
| `--ember-tint` | `#eaf4b6` | Background wash for highlighted pills |
| `--ash` | `#525866` | Cool muted text on porcelain |
| `--ash-soft` | `#8e93a0` | Fine print on porcelain |
| `--cream-muted` | `rgba(245,243,238,0.72)` | Muted text on dark |
| `--line-cream` | `#ddd5c4` | Hairlines on porcelain |
| `--line-dark` | `rgba(245,243,238,0.10)` | Hairlines on dark |

**Rules:**

- Lime is used SPARINGLY. One accent per fold maximum. Eyebrows, link underlines, primary CTAs, status dots.
- Never combine `--ember` (lime) with orange/red accents. Single-accent system.
- Status colors (ok green, warn amber, danger red) only inside data UI — never decoration.
- For the favicon and brand mark `.dot`, lime over slate gives the engineered look.

---

## Type

Three families. Each does one job.

| Family | Role | Why |
|---|---|---|
| **Spectral** | Display (hero, section heads, pull-quotes, stat values) | Sharper terminals than Fraunces, more contemporary feel, variable weight, free on Google Fonts. Reads as "design-considered" not "warm-storybook." |
| **Inter** | Body, lead paragraphs, microcopy | Most legible neutral sans. |
| **JetBrains Mono** | UI chrome (nav links, buttons, eyebrows, labels, pills, fineprint) | Promoted vs v2 — now drives the engineered feel through chrome typography, not just code blocks. |

**Load order:**

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Spectral:ital,wght@0,300;0,400;0,500;0,600;1,400;1,500&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

**Type scale (clamped, fluid):**

| Class | Size | Line | Tracking | Use |
|---|---|---|---|---|
| `.t-hero` | clamp(48px, 7vw, 96px) | 1.0 | -0.028em | Hero h1 |
| `.t-display` | clamp(36px, 5vw, 64px) | 1.05 | -0.022em | Major section h2 |
| `.t-h2` | clamp(28px, 3.6vw, 44px) | 1.1 | -0.018em | Section h2 |
| `.t-h3` | clamp(22px, 2.4vw, 28px) | 1.2 | -0.012em | Sub-section |
| `.t-h4` | 20px | 1.3 | -0.005em | Card title |
| `.t-lead` | clamp(18px, 1.8vw, 22px) | 1.55 | — | Lead paragraph |
| `.t-body` | 17px | 1.65 | — | Body |
| `.t-small` | 14px | 1.55 | — | Tight body |
| `.eyebrow` | 11.5px | — | 0.18em (mono) | Section label with `┤` tick prefix |

**Signature moves:**
- Section eyebrows prefixed with mono `┤` tick character — engineering blueprint mark
- Nav links uppercase mono, not lowercase serif
- Buttons uppercase mono with sharp 4px radius (not full pill) — signals built-not-bought

---

## Spacing — 8pt grid

Same as v2. `--s-1` through `--s-10` mapping to 4px → 128px. Default section padding 96px desktop, 48px mobile.

---

## Components

### Button

| Variant | Style |
|---|---|
| `.btn-primary` | Lime fill, ink text, mono uppercase, 4px radius |
| `.btn-ghost-light` | Transparent with ink border on porcelain |
| `.btn-ghost-dark` | Transparent with hairline border on dark |
| `.btn-solid-dark` | Ink fill, porcelain text |

Buttons are sharp-edged (radius `--r-sm` = 4px), mono uppercase text. NOT pill-shaped — pill is too soft for the engineered signal.

### Card / site-card

- `.card` — porcelain surface, hairline border, lift on hover
- `.card-dark` — smoke on ink for nested cards
- `.card-flat` — paper-2 recessed, no lift
- `.site-card` — full website preview card with 16:10 thumbnail + status badge + meta block + arrow-link footer

### Pill

Sharp-radius mono badges. `.pill-ember` for accent variant (lime tint background).

### Nav

`.nav` (porcelain blur) or `.nav-dark` (ink blur). 64px tall, hairline bottom. Brand mark uses Spectral with lime `.dot`.

### Pull-quote

`.pullquote` — Spectral italic, hairline rules top + bottom. Used for testimonials, manifesto lines.

### Dot grid (signature hero motif)

`.dot-grid` — adds an engineered blueprint dot pattern (24px spacing, 1px dots, 10% opacity) behind hero content. Masked with vertical fade so it fades into the section below. Replaces v2's `.paper-grain` for hero use.

---

## Surface patterns

Don't hand-set colors. Use:

- `.surface-ink` — ink background, porcelain text
- `.surface-paper` — porcelain background, ink text
- `.surface-paper-2` — recessed porcelain

The system flips internal colors based on surface context.

**Typical rhythm:**

```
[nav]
[hero          paper + dot-grid]
[work / problem  ink]
[solution        paper]
[sites           paper]
[stack           paper-2]
[about           paper]
[contact         ink]
[footer          ink]
```

---

## Voice — quick rules

(Brand voice docs cover detail; reminders only.)

- Lowercase Bahasa Indonesia opener if writing to ID audience
- First-person ("I build…" / "Saya bangun…")
- Specifics > superlatives: "12.5 ton/day capacity" beats "high capacity"
- Never "industry-leading," "best-in-class," "world-class"
- Em-dash restraint. One per paragraph max.

---

## What we're NOT

The system is intentionally NOT:

- ❌ Warm cream + orange (v2 — too pet-acc adjacent)
- ❌ Glow effects / neon / cyber (2020 dev portfolio vibe)
- ❌ Multiple radial gradients on hero
- ❌ Drop-shadowed cards everywhere (hairlines instead)
- ❌ Aurora / mesh gradient backgrounds
- ❌ Tailwind default palette
- ❌ Emoji decoration in headlines
- ❌ Pill-shaped CTAs (too soft for engineered signal — use 4px radius)
- ❌ `~/gammawira` terminal mono brandmark (looks like a thousand other dev portfolios)

---

## Inspiration anchors

When stuck, look at: **Vercel** (precision), **Replit** (lime accent done tastefully), **Linear** (typographic discipline), **Stripe** (rhythm), **Spectral specimen pages** (display serif treatment), **architecture firm websites** (asymmetric editorial layouts).

---

## Version history

- **v3 (current, 19 Mei 2026 sore)** — Engineered Editorial · Slate + Porcelain + Acid Lime · Spectral · mono UI chrome
- **v2 (19 Mei 2026 sore-earlier)** — Ember · Warm Charcoal + Cream + Orange · Fraunces · pill CTAs *(deprecated — too warm-trade adjacent to pet-acc.com)*
- **v1 (pre-19 Mei)** — Tailwind dark mode + cyan accent · tech-portfolio template

---

*Locked 19 Mei 2026 sore by Gamma. Tokens live in `assets/system.css`. Update only when a recurring need surfaces that the existing system can't express.*
