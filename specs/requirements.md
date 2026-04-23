# Requirements — Adam Soto Portfolio (v2)
**Phase 1 of 4 — Approved before any design or code is written**
*Updated to reflect v2 redesign: deadpan personality, asymmetric layout, opinions section*

---

## 1. Project Overview

A single-page professional portfolio website for Adam Soto, an Applied AI Engineering student. The site presents a believable, forward-looking professional identity to hiring managers at medium-to-large tech companies — with a distinct personality layer that makes it memorable and human. The tone is deadpan and clever: professional enough to be taken seriously, personal enough to be remembered.

---

## 2. Target Audience

- **Primary:** Hiring manager at a medium-to-large tech company filling a junior Applied AI Engineering or data-focused engineering role
- **Secondary:** Technical recruiters and startup founders in the AI/data space
- **Assumed behavior:** Will scan quickly — professional direction must be clear within 10 seconds, personality should land within 30

---

## 3. Functional Requirements

| ID     | Requirement                                                                 |
|--------|-----------------------------------------------------------------------------|
| FR-01  | Site must display a hero section with name, professional title, and identity statement |
| FR-02  | Site must include an About section with personal background and offset stat tiles |
| FR-03  | Site must display two project cards with titles, descriptions, and links    |
| FR-04  | Site must include a Skills section organized into three categories          |
| FR-05  | Site must include an Opinions section with three personal, non-resume statements |
| FR-06  | Site must include a Contact section with GitHub and LinkedIn links          |
| FR-07  | Site must include a sticky navigation bar linking to all major sections     |
| FR-08  | All internal nav links must scroll smoothly to their target sections        |
| FR-09  | GitHub profile link must open in a new tab                                  |
| FR-10  | LinkedIn profile link must open in a new tab                                |
| FR-11  | Live project link (Vercel) must open in a new tab                           |
| FR-12  | Nav logo must reveal a hidden hover tooltip: "(please hire me)"             |
| FR-13  | Project cards must reveal a deadpan one-liner on hover via slide-up overlay |
| FR-14  | A console.log easter egg must appear when DevTools is opened                |
| FR-15  | An HTML comment easter egg must be present in the page source               |

---

## 4. Content Requirements

| ID     | Requirement                                                                 |
|--------|-----------------------------------------------------------------------------|
| CR-01  | Hero must include name, role tag, identity statement, and kicker line       |
| CR-02  | Hero kicker line: `// currently: at a computer · ideally: not at a computer`|
| CR-03  | Hero right column must show three tilted status cards (current project, in dev, open to roles) |
| CR-04  | About section heading: "Human first. Engineer second."                      |
| CR-05  | About stat tiles must include: states analyzed, AI projects without a spec (0), chocolate opinions, nonchalance willingness |
| CR-06  | About body copy must reference NJIT education, spec-driven development methodology, and going outside |
| CR-07  | Project 1 must link to https://student-reality-lab-soto.vercel.app/        |
| CR-08  | Project 1 hover quip: `// 50 states. 0 spreadsheets required.`             |
| CR-09  | Project 2 (Solsticij) must be marked "In dev" with no broken links         |
| CR-10  | Project 2 hover quip: `// 4 seasons. 1 board. 0 mercy.`                    |
| CR-11  | Opinions section must include all three personal opinions verbatim          |
| CR-12  | Each opinion must have a deadpan Azeret Mono aside comment below it        |
| CR-13  | Skills grouped into: Languages & Data, AI & ML, Tools & Deployment         |
| CR-14  | Contact closing must include the ironic outside/chocolate note              |
| CR-15  | Footer tagline: `Applied AI Engineering · 2026 · currently: probably outside` |
| CR-16  | Console easter egg must end with the chocolate opinion line                 |

---

## 5. Non-Functional Requirements

| ID      | Requirement                                                                |
|---------|----------------------------------------------------------------------------|
| NFR-01  | Site must load in under 2 seconds on a standard connection                 |
| NFR-02  | Site must be fully responsive across mobile, tablet, and desktop viewports |
| NFR-03  | Typography must use Google Fonts only: Instrument Serif, Epilogue, Azeret Mono |
| NFR-04  | No JavaScript frameworks — vanilla JS only                                 |
| NFR-05  | Must deploy to GitHub Pages with no build step required                    |
| NFR-06  | Must pass basic accessibility checks: alt text, color contrast, semantic HTML |
| NFR-07  | All CSS values must use custom properties (CSS variables) for consistency  |
| NFR-08  | Grain overlay must use inline SVG filter — no external image file          |
| NFR-09  | All external links must include rel="noopener noreferrer"                  |

---

## 6. Success Criteria

- [ ] Reviewer can locate GitHub and LinkedIn within 5 seconds of landing
- [ ] Professional direction (Applied AI Engineering) is clear from the hero alone
- [ ] Personality is noticeable within 30 seconds without reading every word
- [ ] Nav logo hover easter egg works on desktop
- [ ] Both project card hover quips slide up correctly on hover
- [ ] Console easter egg fires correctly in Chrome DevTools
- [ ] HTML source comment is present and readable
- [ ] Site renders correctly on Chrome, Firefox, and mobile viewport
- [ ] No broken links, layout overflow, or missing fonts on any viewport

---

## 7. Out of Scope

- Contact form or email submission (links only)
- Dark mode toggle
- Any backend, database, or server-side code
- Authentication of any kind
- Blog or writing section

---

*Document status: Approved — v2 implementation complete*
