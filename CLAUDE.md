# CLAUDE.md

Guidance for AI assistants (and humans) working in this repository.

## What this repository is

This is the **marketing website for Star Angels** — a construction *finishing*
specialist based in Addis Ababa, Ethiopia (founded 2015): high-rise painting,
glass solutions, building decoration, structural cleaning, facade renovation,
and consultancy.

The site exists to build the brand, tell the owner's story, act as a 24/7
salesperson, showcase services and completed work, and **support frequent
tender / procurement submissions**. It is a marketing site, **not a software
product**.

### History (important context)

The repo began as a **static mirror of a Framer agency template** ("BrightEdge").
Mirroring captured the HTML and inline CSS but **killed the animation/
interaction layer** — Framer sites run on a React + Framer Motion runtime
(loaded as ES modules from `framerusercontent.com`) that does not survive static
export. The site has since been **re-authored in place** into Star Angels:

- All agency content (BrightEdge branding, fake team, fake testimonials,
  digital-agency copy, pricing plans, blog posts, unrelated case studies) was
  replaced with Star Angels' real content.
- The dead Framer runtime was **neutralized** (hydration bundle + analytics
  beacon removed) so the static DOM is authoritative.
- The motion/interaction layer was **rebuilt with GSAP + ScrollTrigger** (see
  [Motion layer](#motion-layer)).

The canonical content source is **`starangel-website-content.md`** (kept by the
company, not always committed here). It marks each section as **[CONFIRMED]**,
**[DRAFT — NEEDS REVIEW]**, or **[GAP]**. Honor those markers — see
[Content rules](#content-rules).

## Layout

It is now a **single-page site**: everything lives in `index.html`.
The old multi-page files (`about.html`, `services.html`, `projects.html`,
`blogs.html`, `pricing.html`, `contact.html`, the `projects/` and `blogs/`
folders, and `my_archive.zip`) were **removed** — their content was folded into
sections of `index.html`. They remain in git history if ever needed.

## How `index.html` is structured

It is still Framer-emitted markup: ~2.5 MB, machine-generated, effectively
minified, with **inline `<style>` blocks** (layout CSS is self-contained) and
`data-framer-*` attributes. Images and the Geist font are **hot-linked** from
`framerusercontent.com` (nothing is vendored), so an **offline** preview shows
missing images while an **online** one looks correct.

### Responsive variants (read this before editing)

Framer emits **three breakpoint copies** of most content — Desktop (≥1200px),
Tablet (810–1199px), Phone (≤809px) — toggled by `.hidden-*{display:none}`
media queries. Within a breakpoint, many components are further duplicated for
hover/state or ticker-loop reasons. **A single visible string typically exists
3, 9, or more times in the file.** When you swap text, expect to hit every
copy (use a global replace on a unique string, or scope by byte-range), and
**verify the count** afterward.

### Anchors / navigation

Nav and CTA links are **in-page anchors** (`#home`, `#about`, `#services`,
`#portfolio`, `#process`, `#team`, `#tenders`, `#faq`, `#contact`). Because
duplicate `id`s across breakpoints are invalid, each section variant is tagged
`data-section="…"` instead, and the JS smooth-scroll targets the **visible**
one. Don't reintroduce raw `id` anchors.

### Section order (single page)

Hero → service marquee → Services (6 cards) → About / story + animated stats →
Portfolio → How We Work (5 steps) → Team → **Tenders & Credentials** →
Testimonials → FAQ → Insights → Contact → Footer.

Note the two business-model changes from the template: the pricing page became
**Tenders & Credentials** (procurement-focused), and the marketing blog became a
placeholder **Insights** section.

### Motion layer

At the end of `<body>`: GSAP + ScrollTrigger from a CDN, plus one init script.
It provides scroll-reveal (staggered per section), count-up stat counters,
auto-scrolling marquees (pause on hover), a sticky navbar that goes
transparent→solid, smooth anchor scrolling, and the FAQ accordion. A dedicated
`<style data-starangels-custom>` block in `<head>` holds Star Angels overrides
(the `.sa-hidden` helper, nav-solid state, hover states, accordion panel).

Key conventions the motion script depends on — **preserve these**:

- `.sa-count` + `data-count` (+ optional `data-suffix`) → count-up stat.
- `.sa-hidden` → hidden element (surplus team cards, pricing toggle, dropped
  FAQ items, the dead Framer badge).
- `data-faq-answer="…"` on a FAQ question → the accordion renders that answer
  (the original answers were runtime-injected and lost, so they live in this
  attribute now).
- `data-section="…"` → smooth-scroll / nav target.

Everything is **progressive enhancement**: with no JS, all content stays
visible and counters show their final values. Never move content into a state
that is only revealed by JS without a fallback.

## Content rules

- Follow `starangel-website-content.md`'s status markers. **[CONFIRMED]** and
  **[DRAFT — NEEDS REVIEW]** text may be used; **[GAP]** sections must be built
  structurally but left as **clear placeholders** — e.g. `[Client testimonial
  to be added]`, `[to be provided]`, `Case study coming soon`.
- **Never invent** realistic-sounding fake content for gap sections: no fake
  client names, quotes, project names/details, registration numbers, or
  certifications. This is a hard rule (the site is used for tenders).
- A second source, **`Starangel.pdf`** (company profile, kept in this repo),
  provided real project names, the full leadership roster, and corrected
  figures. Where it conflicts with earlier assumptions, it wins — it's the
  company's own profile document.
- Sections currently on placeholders: **Portfolio** (now has real project
  names; still needs project-specific photos + case-study write-ups),
  **Testimonials** (needs real quotes), **Tenders & Credentials** (has a real
  notable-projects list now; still needs registration/licensing/insurance
  numbers), and photos for the two newest leadership members (see below).
- Confirmed facts safe to use: founded **2016**; **Bole Road, Addis Ababa**;
  phone **+251 913790984** / **+251 924451560** (both General Manager);
  email **starangelsconstructionplc@gmail.com**; **50+** projects; **98%**
  client satisfaction; the **6** services above; leadership — Yared Kebede
  (GM), Hibst Kebede (Vice Manager), Henok Kebede (Auditor), Birhanu Abate
  (Quality Manager), Meskerem Kebede (Marketing Manager, no photo yet), Meron
  Yeshiwond (Architect, no photo yet). Real project names: La'Gahare, Eagle
  Hills, East African Holding, Piassa, PPP Project, Tor-Hailoch, Anbessa.

## Editing conventions

- **Don't hand-reflow or prettify** the minified HTML — it produces enormous,
  meaningless diffs and risks breaking layout. Make the **smallest targeted
  edit**.
- **Don't read the whole 2.5 MB file into context** for a small change. Grep
  for the exact string, edit that spot. To understand structure, grep
  `data-framer-name="…"` and work in byte-ranges.
- Watch the **responsive-variant multiplicity** (above) — swap all copies and
  verify counts.
- **Avoid substring collisions.** e.g. replacing `Professional` also hits
  `Professionals`; replacing a role globally can bleed into testimonials.
  Prefer text-node form (`>Word<`) or section-scoped byte-range edits.
- Prefer a script (Python) for multi-site-wide swaps so you can print and
  verify occurrence counts before/after.

## Previewing & testing

```bash
python3 -m http.server 8000    # then open http://localhost:8000/index.html
```

Online it renders correctly; offline, images/fonts and the GSAP CDN won't load
(the page still shows all content — that's the intended fallback).

Headless smoke test (Chromium/Playwright is available) is worth running after
motion changes: load the page, check for console/page errors, confirm **no
reveal target is stuck at opacity 0**, and that counters, the FAQ accordion,
the marquees, and the sticky nav behave.

## Git workflow

- Active branch for this work: **`claude/claude-md-docs-w65r6v`**. Develop,
  commit, and push there; create from the latest default branch if needed. Do
  not push to `master` without explicit permission.
- Commit in **small, incremental** steps with clear messages. Do **not** open a
  pull request unless explicitly asked.
