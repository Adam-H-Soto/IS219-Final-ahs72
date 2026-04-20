# Design Document — Adam Soto Portfolio

## 1. Visual System

### Color Palette
| Token          | Hex       | Usage                              |
|----------------|-----------|------------------------------------|
| --cream        | #f5f0e8   | Section backgrounds                |
| --warm-white   | #faf8f4   | Page background                    |
| --ink          | #1a1612   | Primary text, dark backgrounds     |
| --ink-soft     | #3d3530   | Body text                          |
| --ink-muted    | #7a6f66   | Secondary text, labels             |
| --amber        | #c8823a   | Primary accent, CTAs, highlights   |
| --amber-light  | #e8a85a   | Accent on dark backgrounds         |
| --amber-pale   | #f5e6d0   | Tinted backgrounds, card shadows   |
| --teal         | #2a6b6e   | Secondary accent, links            |
| --teal-light   | #3d8a8e   | Hover states on teal elements      |
| --teal-pale    | #d4eaeb   | Tinted backgrounds                 |
| --border       | #ddd5c8   | All borders and dividers           |

### Typography
| Role          | Font             | Weight / Style          |
|---------------|------------------|-------------------------|
| Display/Hero  | Lora (serif)     | 600 regular, 400 italic |
| Body          | DM Sans          | 300, 400, 500, 600      |
| Monospace     | DM Mono          | 400, 500                |

All loaded via Google Fonts.

### Spacing Scale
Base unit: 0.25rem (4px). Major section padding: 6rem vertical, 5rem horizontal.

## 2. Layout Architecture

### Page Structure
```
<nav>              — Fixed, full width, blur backdrop
<section#hero>     — Two-column grid (text left, visual right)
<section#about>    — Two-column grid (label left, content right) on cream bg
<section#projects> — Two-column card grid
<section#skills>   — Three-column skill groups on ink (dark) bg
<section#contact>  — Centered, single column on cream bg
<footer>           — Two-column flex (name left, tagline right) on ink bg
```

### Hero Layout
- Left column (1fr): eyebrow label → name → subtitle → statement → CTAs
- Right column (1fr): decorative data visualization card

### Responsive Breakpoints
| Breakpoint | Width    | Change                                      |
|------------|----------|---------------------------------------------|
| Desktop    | > 900px  | Two-column layouts active                   |
| Tablet     | ≤ 900px  | All grids collapse to single column         |
| Mobile     | ≤ 600px  | Font sizes reduce, hero visual hidden       |

## 3. Component Inventory

| Component       | Description                                              |
|-----------------|----------------------------------------------------------|
| Nav             | Fixed bar with logo left, links right                   |
| Hero            | Two-column with animated text reveal and viz card       |
| Section Label   | Monospace eyebrow with amber color and trailing line    |
| Section Heading | Lora serif, large, ink color                            |
| About Grid      | Two-column with stat tiles                              |
| Stat Tile       | White card with large amber number + small label        |
| Project Card    | Border card with colored visual header + body content  |
| Project Tag     | Small monospace pill with border                        |
| Skill Group     | Dark-bg column with amber title + arrow list            |
| Contact Links   | Two pill buttons: GitHub (dark) and LinkedIn (outlined) |
| Footer          | Dark bar with name and tagline                          |

## 4. Animation Decisions
- Hero text elements: staggered `fadeUp` keyframe, 0.7s ease, 0.2s delay increments
- Hero visual card: `fadeIn` keyframe, 1s ease, 0.8s delay
- All hovers: `transform: translateY(-2px)` + color transitions, 0.2s ease
- Pulse dot: `scale` + `opacity` infinite loop, 2s ease-in-out
- No scroll-triggered animations (keeps JS dependency minimal)

## 5. Accessibility Decisions
- All links have descriptive text (no bare "click here")
- Color contrast meets WCAG AA on all text/background combinations
- Semantic HTML5 elements: `<nav>`, `<section>`, `<footer>`, `<h1>`–`<h3>`
- All decorative visuals are `aria-hidden` or have empty alt text
