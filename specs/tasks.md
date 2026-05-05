# Implementation Tasks — Adam Soto Portfolio (v2)
**Phase 3 of 4 — Approved before any code is written**
*Depends on: specs/requirements.md v2 (approved), specs/design.md v2 (approved)*
*Updated to reflect v2 redesign: new sections, personality layer, asymmetric layout*

Check off each task as completed. Every task references the requirement or design section it satisfies.

---

## Group 1: Project Setup

- [x] **T-01** — Create `index.html` with HTML5 boilerplate, correct lang/charset/viewport → NFR-05
- [x] **T-02** — Create `style.css` and link in `<head>` → NFR-07
- [x] **T-03** — Update page `<title>` to include the parenthetical: "(who'd rather be outside)" → Design §5
- [x] **T-04** — Update `<meta name="description">` to include chocolate reference → Design §5
- [x] **T-05** — Add Google Fonts `<link>` for Instrument Serif, Epilogue, Azeret Mono → NFR-03
- [x] **T-06** — Define all CSS custom properties on `:root` (color tokens from Design §1.1) → NFR-07
- [x] **T-07** — Set `html { scroll-behavior: smooth; }` and `body` base styles → FR-08
- [x] **T-08** — Add grain overlay via `body::before` with inline SVG `feTurbulence` filter → NFR-08, Design §1.4

---

## Group 2: HTML Easter Eggs

- [x] **T-09** — Add HTML comment at top of `<body>` greeting source readers, referencing /specs → FR-15, Design §5
- [x] **T-10** — Add `<script>` at bottom of body with 5 styled `console.log` lines, ending with chocolate opinion → FR-14, CR-16, Design §5

---

## Group 3: Navigation

- [x] **T-11** — Write `<nav>` HTML with `.nav-logo` and `.nav-links` ul → FR-07
- [x] **T-12** — Style nav: fixed, z-index 99, backdrop blur, border-bottom → FR-07, Design §2.1
- [x] **T-13** — Style nav logo in Instrument Serif, add `::after` pseudo-element for "(please hire me)" hover reveal → FR-12, Design §5
- [x] **T-14** — Style nav links: Azeret Mono 0.8rem uppercase, jade on hover → Design §3
- [x] **T-15** — Add "Opinions" link to nav alongside About, Projects, Skills, Contact → FR-05

---

## Group 4: Hero Section

- [x] **T-16** — Write `<section id="top" class="hero">` with hero-left and hero-right structure → FR-01, Design §2.2
- [x] **T-17** — Style hero as two-column CSS grid (`1.1fr / 0.9fr`), min-height 100vh → Design §2.2
- [x] **T-18** — Add `hero::before` ghost "01" numeral in Instrument Serif, absolute position, right edge → Design §1.4
- [x] **T-19** — Add `.hero-tag` pill: Azeret Mono, jade border, "Applied AI Engineering" → CR-01
- [x] **T-20** — Add `<h1 class="hero-name">` with "Adam" line break "Soto." — `<em>` on "Soto" in jade italic → CR-01
- [x] **T-21** — Add `.hero-headline` paragraph in Epilogue 300 with `<strong>` on key phrase → CR-01
- [x] **T-22** — Add `.hero-kicker` in Azeret Mono with jade `<span>` on the ironic half → CR-02
- [x] **T-23** — Add two CTA buttons: "See the work" (btn-dark → #projects) and "GitHub →" (btn-ghost → GitHub, new tab) → FR-09
- [x] **T-24** — Apply staggered `slideIn` animations to all hero-left elements using CSS `--delay` custom property → Design §4.1
- [x] **T-25** — Build three `.hero-card` elements in hero-right: current project (dot-live), in dev (dot-wip), open to roles → CR-03
- [x] **T-26** — Apply individual CSS rotations to each card (`-1.3deg`, `0.9deg`, `-0.4deg`) with margin-left offsets → Design §2.3
- [x] **T-27** — Style hero card hover: `rotate(0)`, `translateY(-3px)`, shadow shifts to pale jade → Design §4.2
- [x] **T-28** — Apply `fadeIn` animation to `.hero-right` (0.9s, 0.7s delay) → Design §4.1
- [x] **T-29** — Add `.dot-live` (forest, pulse animation) and `.dot-wip` (gold) status dots → Design §3

---

## Group 5: About Section

- [x] **T-30** — Write `<section id="about" class="about">` with paper-dark background → FR-02, Design §2.1
- [x] **T-31** — Style two-column about grid (`1fr / 1.5fr`), gap 5rem → Design §2.2
- [x] **T-32** — Add section number "02 — About" and `<h2>` heading: "Human first. Engineer second." → CR-04, Design §3
- [x] **T-33** — Build 2×2 `.stat-cluster` grid with four stat tiles → FR-02, CR-05
- [x] **T-34** — Stat tile content: "50 States analyzed", "0 AI projects started without a spec", "∞ Opinions on chocolate", "0 Willingness to be nonchalant" → CR-05, Design §5
- [x] **T-35** — Apply intentional margin-top offsets to stat tiles #2 (`1.5rem`) and #4 (`-0.75rem`) → Design §2.3
- [x] **T-36** — Write four about body paragraphs: NJIT education + Dean's Scholar, spec-driven methodology with /specs reference, outside/leadership/internship, role aspiration → CR-06

---

## Group 6: Projects Section

- [x] **T-37** — Write `<section id="projects" class="projects">` with section number "03 — Projects" → FR-03
- [x] **T-38** — Style projects grid as `1.2fr / 0.8fr` (intentionally unequal) → Design §2.3
- [x] **T-39** — Apply `margin-top: 3rem` to second project card for cascade effect → Design §2.3
- [x] **T-40** — Build project card structure: `.project-visual` (top) + `.project-body` (bottom) + `.project-quip` (overlay) → Design §3
- [x] **T-41** — Style `.project-quip`: absolute bottom, ink bg, slides up from `translateY(100%)` on card hover → FR-13, Design §4.2
- [x] **T-42** — **Project 1:** forest gradient visual, mini state-labeled bars visualization → CR-07
- [x] **T-43** — **Project 1:** wrap in `<a>` linking to Vercel URL, target="_blank" → CR-07, FR-11
- [x] **T-44** — **Project 1:** hover quip: `// 50 states. 0 spreadsheets required.` → CR-08
- [x] **T-45** — **Project 1:** "Live ↗" badge, tags (Python, Data Viz, Interactive, Vercel) → FR-03
- [x] **T-46** — **Project 2:** dark gradient visual, mini network node visualization → CR-09
- [x] **T-47** — **Project 2:** use `<div>` (not `<a>`), "In dev" badge, "Coming soon" muted link → CR-09
- [x] **T-48** — **Project 2:** hover quip: `// 4 seasons. 1 board. 0 mercy.` → CR-10
- [x] **T-49** — **Project 2:** tags (Unity, C#, 2D, Board Game) → FR-03

---

## Group 7: Opinions Section

- [x] **T-50** — Write `<section id="opinions" class="opinions">` with ink (dark) background → FR-05, Design §2.1
- [x] **T-51** — Add section number "04 — Unprompted" and heading "Things I believe strongly." → FR-05
- [x] **T-52** — Add `.opinions-intro` in Azeret Mono: `// not on my resume. very much on my mind.` → Design §5
- [x] **T-53** — Build opinion list with CSS grid layout (`3rem / 1fr`) for number + content columns → Design §3
- [x] **T-54** — **Opinion 01:** "Being nonchalant is a waste of a perfectly good emotion." → CR-11
  - Aside: `// we have so many of them. why suppress them.` → CR-12
- [x] **T-55** — **Opinion 02:** "One piece of chocolate a day is a health decision, not a treat." → CR-11
  - Aside: `// Polish proverb from my region. this is non-negotiable.` → CR-12
- [x] **T-56** — **Opinion 03:** "I love technology. I also love not being near it. The world is large and a screen is very small." → CR-11
  - Aside: `// yes, I'm aware this is on an AI engineer's portfolio. I contain multitudes.` → CR-12
- [x] **T-57** — Style opinion items: border-bottom dividers, jade opinion number, Instrument Serif text, Azeret Mono aside at 30% opacity → Design §3

---

## Group 8: Skills Section

- [x] **T-58** — Write `<section id="skills" class="skills">` with paper-dark background → FR-04, Design §2.1
- [x] **T-59** — Add section number "05 — Skills" and heading → FR-04
- [x] **T-60** — Build three-column `.skills-grid` → CR-13, Design §2.3
- [x] **T-61** — Apply cascading margin-top to columns: #2 gets `1.5rem`, #3 gets `3rem` → Design §2.3
- [x] **T-62** — **Column 1:** "Languages & Data" — Python, pandas/NumPy, SQL, JavaScript, HTML/CSS → CR-13
- [x] **T-63** — **Column 2:** "AI & ML" — Claude API, OpenAI API, Prompt Engineering, RAG Pipelines, LangChain → CR-13
- [x] **T-64** — **Column 3:** "Tools & Deployment" — GitHub/Git, Vercel, GitHub Pages, VS Code + Claude Code, REST APIs → CR-13
- [x] **T-65** — Style skill group titles: Azeret Mono, jade, border-bottom → Design §3
- [x] **T-66** — Style skill list items: em dash prefix in `--border` color → Design §3

---

## Group 9: Contact Section & Footer

- [x] **T-67** — Write `<section id="contact" class="contact">` with paper background → FR-06, Design §2.1
- [x] **T-68** — Add section number "06 — Contact" and heading "Let's build something." → FR-06
- [x] **T-69** — Add Instrument Serif italic contact statement → CR-14
- [x] **T-70** — Add GitHub button (btn-dark, new tab) → FR-09
- [x] **T-71** — Add LinkedIn button (btn-ghost, new tab) → FR-10
- [x] **T-72** — Add `.contact-irony` block in Azeret Mono with left border, jade `<span>` on punchline → CR-14, Design §5
- [x] **T-73** — Write `<footer>` with ink bg: name (Instrument Serif) left, tagline (Azeret Mono) right → CR-15

---

## Group 10: Responsive Styles

- [x] **T-74** — Add `@media (max-width: 900px)` breakpoint → NFR-02, Design §2.4
  - [x] Hero collapses to single column, `::before` ghost hidden
  - [x] Hero right becomes horizontal scroll row, cards lose rotation
  - [x] About grid collapses, stat offsets removed
  - [x] Projects grid collapses, card #2 margin-top removed
  - [x] Skills grid collapses to 1fr, staircase offsets removed
  - [x] Section padding reduces to `4rem 1.5rem`
  - [x] Footer stacks vertically
- [x] **T-75** — Add `@media (max-width: 600px)` breakpoint → NFR-02, Design §2.4
  - [x] Hero right hidden entirely
  - [x] Hero name reduces to 3rem
  - [x] Nav link gap reduces
  - [x] Opinion grid tightens to `2rem / 1fr`

---

## Group 11: Scrollytelling

- [x] **T-90** — Add `.scroll-progress` CSS: `position: fixed; top: 0; height: 2px; background: var(--rust); z-index: 200` → SR-01
- [x] **T-91** — Add `#scroll-progress` element inside `<nav>` → SR-01
- [x] **T-92** — Add scroll event listener to drive progress bar width from `scrollY / scrollHeight` → SR-01
- [x] **T-93** — Add `.reveal` CSS class: `opacity: 0; translateY(28px)`, transition `0.65s cubic-bezier(0.16,1,0.3,1)` → SR-02
- [x] **T-94** — Add `.reveal.revealed` CSS: `opacity: 1; translateY(0)` → SR-02
- [x] **T-95** — Set up `IntersectionObserver` (threshold 0.12) to add `.revealed` class on scroll entry, unobserve after firing → SR-02, SR-06
- [x] **T-96** — Apply `.reveal` + staggered `data-delay` to: section labels, section headings, stat tiles, about body paragraphs, project cards, opinion items, skill groups, contact blocks → SR-02, SR-03
- [x] **T-97** — Add stat countup: second `IntersectionObserver` (threshold 0.5) animates numeric stat values > 0 over 1400ms with cubic ease-out → SR-04

---

## Group 13: Final QA

- [ ] **T-76** — Open in Chrome: verify all sections render, all links work → NFR-06
- [ ] **T-77** — Open in Firefox: verify layout consistency → NFR-06
- [ ] **T-78** — Test mobile viewport (375px) in DevTools: no overflow, text readable → NFR-02
- [ ] **T-79** — Hover nav logo: confirm "(please hire me)" appears → FR-12
- [ ] **T-80** — Hover both project cards: confirm quip slides up → FR-13
- [ ] **T-81** — Open Chrome DevTools console: confirm all 5 easter egg lines appear → FR-14
- [ ] **T-82** — View page source: confirm HTML comment is present → FR-15
- [ ] **T-83** — Verify GitHub link opens correct profile in new tab → FR-09
- [ ] **T-84** — Verify LinkedIn link opens correct profile in new tab → FR-10
- [ ] **T-85** — Verify Project 1 opens Vercel URL in new tab → FR-11
- [ ] **T-86** — Confirm GitHub and LinkedIn findable within 5 seconds from top → Success Criteria
- [ ] **T-87** — Confirm personality is noticeable within 30 seconds → Success Criteria
- [ ] **T-88** — Validate HTML at validator.w3.org — zero errors → NFR-05
- [ ] **T-89** — Check grain overlay renders without external network request → NFR-08

---

## Commit Milestones

```bash
git commit -m "build: setup, CSS variables, grain overlay, base styles"
git commit -m "build: html easter egg comment and console easter egg"
git commit -m "build: navigation with logo hover reveal"
git commit -m "build: hero section with tilted cards and animations"
git commit -m "build: about section with offset stat tiles"
git commit -m "build: projects section with hover quips"
git commit -m "build: opinions section"
git commit -m "build: skills section with staircase layout"
git commit -m "build: contact section and footer"
git commit -m "build: responsive breakpoints"
git commit -m "fix: QA pass, all easter eggs and links verified"
```

---

*Document status: Approved — v2 implementation complete*
