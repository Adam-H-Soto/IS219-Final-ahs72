# Design Document — Adam Soto Portfolio (v2)
**Phase 2 of 4 — Approved before any code is written**
*Depends on: specs/requirements.md v2 (approved)*
*Updated to reflect v2 redesign: new type system, asymmetric layout, grain overlay, tilted cards*

---

## 1. Visual System

### 1.1 Color Palette

| Token           | Hex                    | Usage                                        |
|-----------------|------------------------|----------------------------------------------|
| `--paper`       | `#f7f3ec`              | Page base background                         |
| `--paper-dark`  | `#ede8df`              | About, Skills section backgrounds            |
| `--ink`         | `#1c1814`              | Primary text, dark backgrounds, footer       |
| `--ink-mid`     | `#4a4038`              | Body copy, card subtitles                    |
| `--ink-faint`   | `#9a8f85`              | Captions, mono asides, muted labels          |
| `--rust`        | `#3aaa6e`              | Primary accent — CTAs, italic names, eyebrows (jade green) |
| `--rust-pale`   | `#c8e8d6`              | Card hover shadow offset (pale jade)         |
| `--forest`      | `#2d5a3d`              | Project 1 visual bg, project links           |
| `--forest-pale` | `#d4e8da`              | Tinted backgrounds                           |
| `--gold`        | `#c9962a`              | WIP status dot on hero card                  |
| `--gold-pale`   | `#f5e9cc`              | Tinted backgrounds                           |
| `--border`      | `#d8d0c4`              | All borders, dividers, ghost elements        |
| `--shadow`      | `rgba(28,24,20,0.07)`  | Card box shadows                             |

### 1.2 Typography

| Role             | Font              | Weights / Styles          | Usage                                  |
|------------------|-------------------|---------------------------|----------------------------------------|
| Display / Serif  | Instrument Serif  | 400 regular, 400 italic   | Hero name, section headings, card values|
| Body / UI        | Epilogue          | 300, 400, 500, 700, 900   | Body copy, nav, buttons, paragraphs    |
| Monospace        | Azeret Mono       | 400, 500                  | Tags, eyebrows, asides, code comments, easter eggs |

Google Fonts import:
```
https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Epilogue:wght@300;400;500;700;900&family=Azeret+Mono:wght@400;500&display=swap
```

### 1.3 Type Scale

| Role              | Size                       | Weight | Font             |
|-------------------|----------------------------|--------|------------------|
| Hero name         | clamp(3.5rem, 7vw, 6rem)   | 400    | Instrument Serif |
| Section heading   | clamp(2rem, 4vw, 3rem)     | 400    | Instrument Serif |
| Hero headline     | clamp(1rem, 1.8vw, 1.15rem)| 300    | Epilogue         |
| Body              | 1rem (16px base)           | 400    | Epilogue         |
| Project title     | 1.3rem                     | 400    | Instrument Serif |
| Card value        | 1.1rem                     | 400    | Instrument Serif |
| Opinion text      | clamp(1.1rem, 2vw, 1.4rem) | 400    | Instrument Serif |
| Eyebrow / label   | 0.65rem                    | 400–500| Azeret Mono      |
| Aside / comment   | 0.68–0.72rem               | 400    | Azeret Mono      |
| Tag / badge       | 0.6rem                     | 400    | Azeret Mono      |
| Button            | 0.85rem                    | 600    | Epilogue         |

### 1.4 Atmosphere

- **Grain overlay:** Fixed-position `::before` on body using inline SVG `feTurbulence` filter, opacity 0.35. Creates tactile paper texture without external file dependency → NFR-08
- **Ghost section numbers:** Large Instrument Serif numerals (`16rem`) in `--border` color behind hero content. `pointer-events: none`, `user-select: none`

---

## 2. Layout Architecture

### 2.1 Page Section Order

```
<nav>                Fixed, blur backdrop, border-bottom
<section#top>        Hero — two-column asymmetric grid
<section#about>      About — two-column grid, paper-dark bg
<section#projects>   Projects — intentionally uneven two-column grid
<section#opinions>   Opinions — full-width dark (ink) bg, numbered list
<section#skills>     Skills — three-column cascading grid, paper-dark bg
<section#contact>    Contact — left-aligned, paper bg
<footer>             Dark footer, flex row
```

### 2.2 Hero Layout

```
[hero] — CSS grid, 1.1fr / 0.9fr, min-height 100vh
  ├── [hero::before]   Ghost "01" numeral, absolute, right edge
  ├── [hero-left]      z-index: 1
  │     ├── .hero-tag       Jade border pill, Azeret Mono
  │     ├── h1.hero-name    Instrument Serif, "Adam / Soto." (em = jade italic)
  │     ├── .hero-headline  Epilogue 300, identity statement
  │     ├── .hero-kicker    Azeret Mono, ink-faint, jade span for ironic half
  │     └── .hero-ctas      Two buttons: btn-dark + btn-ghost
  └── [hero-right]     z-index: 1, flex column, gap 1rem
        ├── .hero-card (1)  rotate(-1.3deg)
        ├── .hero-card (2)  rotate(0.9deg), margin-left: 1.5rem
        └── .hero-card (3)  rotate(-0.4deg), margin-left: 0.5rem
```

### 2.3 Asymmetric Layout Decisions

These are intentional design choices, not bugs:

| Element                          | Offset                                      | Reason                          |
|----------------------------------|---------------------------------------------|---------------------------------|
| Hero cards                       | Each rotated differently, offset left       | Feels placed, not generated     |
| About stat tile #2               | `margin-top: 1.5rem`                        | Breaks the grid rhythm          |
| About stat tile #4               | `margin-top: -0.75rem`                      | Further disrupts alignment      |
| Projects card #2                 | `margin-top: 3rem`                          | Creates visual cascade          |
| Skills column #2                 | `margin-top: 1.5rem`                        | Step-down staircase effect      |
| Skills column #3                 | `margin-top: 3rem`                          | Continues the staircase         |
| Projects grid columns            | `1.2fr / 0.8fr` (unequal)                  | Avoids symmetry                 |

### 2.4 Responsive Breakpoints

| Breakpoint | Width    | Change                                                              |
|------------|----------|---------------------------------------------------------------------|
| Desktop    | > 900px  | All multi-column layouts active, tilted cards visible              |
| Tablet     | ≤ 900px  | Grids collapse to 1fr, hero cards scroll horizontally, section padding reduces |
| Mobile     | ≤ 600px  | Hero right hidden, font sizes reduce, opinion grid tightens        |

---

## 3. Component Inventory

| Component           | Element            | Key Styles / Behavior                                     |
|---------------------|--------------------|-----------------------------------------------------------|
| Nav                 | `<nav>`            | Fixed, z-99, backdrop blur, border-bottom                 |
| Nav logo            | `<a>`              | Instrument Serif, hover reveals `(please hire me)` via `::after` → FR-12 |
| Nav links           | `<ul><li><a>`      | Azeret Mono 0.8rem uppercase, jade on hover               |
| Hero tag            | `<span>`           | Jade border pill, Azeret Mono                             |
| Hero name           | `<h1>`             | Instrument Serif, jade italic `<em>`                      |
| Hero kicker         | `<p>`              | Azeret Mono, ink-faint, jade `<span>` for ironic half     |
| Hero card           | `<div>`            | White bg, border, 4px box-shadow, CSS rotation, hover straightens |
| Card dot            | `<div>`            | 8px circle — forest (pulse) for live, gold for WIP        |
| Section number      | `<p>`              | Azeret Mono 0.65rem, `::after` trailing line              |
| Section heading     | `<h2>`             | Instrument Serif, jade italic `<em>`                      |
| Stat tile           | `<div>`            | Paper bg, border, Instrument Serif number in jade, intentional margin offsets |
| Project card        | `<a>` or `<div>`   | Border, hover: translateY(-5px) + shadow                  |
| Project quip        | `<div>`            | Absolute bottom, ink bg, slides up on card hover → FR-13  |
| Project visual      | `<div>`            | 200px height, gradient bg                                 |
| Mini bars           | `<div>` flex       | State-labeled bars, highlight in amber                    |
| Mini network        | `<div>` relative   | Absolute-positioned nodes, amber tones                    |
| Project badge       | `<span>`           | Absolute top-right, translucent dark bg                   |
| Project tag (ptag)  | `<span>`           | Azeret Mono pill, paper bg, border                        |
| Opinion item        | CSS grid (3rem/1fr)| Number left, text + aside right                           |
| Opinion text        | `<p>`              | Instrument Serif, warm paper color on ink bg              |
| Opinion aside       | `<p>`              | Azeret Mono, 30% opacity, reads as code comment           |
| Skill group         | `<div>`            | Paper bg, border, cascading margin-top offsets            |
| Skill group title   | `<p>`              | Azeret Mono, jade, border-bottom                          |
| Skill list item     | `<li>`             | Em dash prefix in `--border` color                        |
| Contact irony       | `<p>`              | Azeret Mono, left border, jade `<span>` on punchline      |
| Console easter egg  | `<script>`         | `console.log` with styled output, ends with chocolate line → FR-14 |
| HTML comment        | `<!-- -->`         | Greeting at top of body, references /specs → FR-15        |

---

## 4. Animation & Interaction

### 4.1 Page Load (Hero)

| Element       | Class              | Keyframe  | Duration | Delay  |
|---------------|--------------------|-----------|----------|--------|
| Hero tag      | `.animate` inline  | slideIn   | 0.6s     | 0.1s   |
| Hero name     | `.animate` inline  | slideIn   | 0.6s     | 0.2s   |
| Hero headline | `.animate` inline  | slideIn   | 0.6s     | 0.35s  |
| Hero kicker   | `.animate` inline  | slideIn   | 0.6s     | 0.45s  |
| Hero CTAs     | `.animate` inline  | slideIn   | 0.6s     | 0.55s  |
| Hero right    | `.animate` inline  | fadeIn    | 0.9s     | 0.7s   |

Animation uses CSS custom property `--delay` on each element.

```css
@keyframes slideIn {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}
@keyframes pulse {
  0%, 100% { opacity: 1; transform: scale(1); }
  50%       { opacity: 0.5; transform: scale(1.5); }
}
```

### 4.2 Hover States

| Element          | Hover effect                                              | Transition      |
|------------------|-----------------------------------------------------------|-----------------|
| Nav logo         | `::after` fades in with `(please hire me)`               | 0.2s opacity    |
| Nav links        | color → jade                                              | 0.2s            |
| Buttons          | `translateY(-2px)`, bg color shift                        | 0.2s            |
| Hero cards       | rotate(0) + `translateY(-3px)`, shadow shifts to pale jade| 0.25s           |
| Project cards    | `translateY(-5px)`, deeper shadow                         | 0.25s           |
| Project quip     | `translateY(0)` from `translateY(100%)` — slides up       | 0.25s ease      |
| Project link     | gap increases 0.3rem → 0.6rem                             | 0.2s            |

---

## 5. Personality Layer — Design Decisions

| Element              | Location          | Content                                                          |
|----------------------|-------------------|------------------------------------------------------------------|
| Page `<title>`       | `<head>`          | "Adam Soto — Applied AI Engineer (who'd rather be outside)"     |
| Meta description     | `<head>`          | "Data tools. AI pipelines. Strong opinions about chocolate."    |
| HTML comment         | Top of `<body>`   | Greeting for source readers; references /specs                  |
| Nav logo hover       | Nav               | Reveals "(please hire me)" in jade below the logo              |
| Hero kicker          | Hero              | `// currently: at a computer · ideally: not at a computer`      |
| Stat tile #3         | About             | "∞ — Opinions on chocolate"                                     |
| Stat tile #4         | About             | "0 — Willingness to be nonchalant"                              |
| Section 04           | Opinions          | Three personal opinions with deadpan mono asides                |
| Contact irony        | Contact           | Monospaced closing note about going outside                     |
| Footer tagline       | Footer            | `currently: probably outside`                                   |
| Project quip #1      | Project card 1    | `// 50 states. 0 spreadsheets required.`                        |
| Project quip #2      | Project card 2    | `// because charts don't explain themselves.`                   |
| Console easter egg   | `<script>`        | 5 styled `console.log` lines, ends with chocolate opinion       |

---

*Document status: Approved — v2 implementation complete*
