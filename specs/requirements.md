# Requirements — Adam Soto Portfolio

## 1. Project Overview
A single-page professional portfolio website for Adam Soto, an Applied AI
Engineering student, targeting hiring managers at medium-to-large tech companies.

## 2. Target Audience
- Primary: Hiring manager at a tech company filling a junior AI/data engineering role
- Secondary: Technical recruiters and startup founders in the AI space
- Assumed context: Will scan quickly — must communicate value in under 10 seconds

## 3. Functional Requirements
- FR-01: Site must display a hero section with name, title, and identity statement
- FR-02: Site must include an About section with personal background and stats
- FR-03: Site must display two project cards with descriptions and links
- FR-04: Site must include a Skills section listing languages, AI tools, and deployment tools
- FR-05: Site must include a Contact section with visible GitHub and LinkedIn links
- FR-06: Site must include a sticky navigation bar linking to all major sections
- FR-07: All internal nav links must scroll smoothly to their target sections
- FR-08: GitHub profile link must open in a new tab
- FR-09: LinkedIn profile link must open in a new tab
- FR-10: Live project link (Vercel) must open in a new tab

## 4. Content Requirements
- CR-01: Hero headline must state professional identity clearly
- CR-02: About section must use a forward-looking, warm tone
- CR-03: Project 1 must link to https://student-reality-lab-soto.vercel.app/
- CR-04: Project 2 (EconLens) must be marked "In Development"
- CR-05: Skills section must be organized into three categories
- CR-06: Footer must display name and role/year

## 5. Non-Functional Requirements
- NFR-01: Site must load in under 2 seconds on a standard connection
- NFR-02: Site must be fully responsive (mobile, tablet, desktop)
- NFR-03: Site must use only Google Fonts — no local font files
- NFR-04: No JavaScript frameworks — vanilla JS only
- NFR-05: Must deploy to GitHub Pages with no build step required
- NFR-06: Must pass basic accessibility checks (alt text, contrast, semantic HTML)

## 6. Success Criteria
- A reviewer can find GitHub and LinkedIn links within 5 seconds of landing
- The professional direction is clear without reading the About section
- All project links work correctly
- Site renders correctly on Chrome, Firefox, and mobile Safari
