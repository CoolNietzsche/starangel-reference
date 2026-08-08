# CLAUDE.md

Guidance for AI assistants (and humans) working in this repository.

## What this repository is

This is a **static mirror of a Framer-exported website** — the "BrightEdge"
creative-studio / agency marketing template. It is kept as a **reference for
structure and animation**, not as an actively hand-authored codebase. The only
commit to date is literally: _"Mirror of Framer template for
structural/animation reference."_

There is **no build system, no package manager, no framework source, and no
test suite**. Every `.html` file is a self-hosting page emitted by
[Framer](https://www.framer.com/); the markup is machine-generated and
effectively minified.

Treat the repo as **read-mostly reference material**. See
[Editing conventions](#editing-conventions) before changing any HTML.

## Layout

```
.
├── index.html          # Home / landing page (largest, ~2.5 MB)
├── about.html          # About page
├── services.html       # Services page
├── pricing.html        # Pricing page
├── projects.html       # Projects index / listing
├── blogs.html          # Blog index / listing
├── contact.html        # Contact page (embeds Google Maps)
├── projects/           # Individual project case-study pages
│   ├── built-to-last.html
│   ├── fresh-beginnings.html
│   ├── glow-theory.html
│   ├── kindred-space.html
│   ├── spreading-the-word.html
│   ├── the-perfect-frame.html
│   ├── velocity.html
│   └── vistahaven.html
├── blogs/              # Individual blog-article pages
│   ├── building-a-resilient-business-model-in-uncertain-times.html
│   ├── building-a-resilient-startup-key-strategies-for-success.html
│   ├── the-future-of-ai-in-digital-marketing.html
│   ├── the-impact-of-artificial-intelligence-on-digital-marketing-strategies.html
│   ├── the-importance-of-user-centered-design.html
│   ├── the-role-of-artificial-intelligence-in-modern-digital-marketing.html
│   └── top-digital-marketing-trends-for-2025.html
└── my_archive.zip      # Snapshot of the whole site (all pages + robots.txt)
```

### `my_archive.zip`

A packaged copy of the site — the same 7 top-level pages, `projects/`,
`blogs/`, plus a `robots.txt` that is **not** present as a loose file in the
repo. It's a self-contained backup/export snapshot. Don't treat it as a second
source of truth; if the loose files and the archive diverge, the loose files
are what's checked in.

## How a page is built (Framer output)

Each page is a complete standalone HTML document. Understanding the anatomy
matters far more than reading the minified body:

- **Generator**: `<meta name="generator" content="Framer ...">`. The site ID
  is `3jWqxJAnu2sNOCaF3DWpBH`, which appears throughout asset URLs.
- **Runtime**: React + Framer Motion, loaded as **ES modules from the Framer
  CDN** (`https://framerusercontent.com/sites/3jWqxJAnu2sNOCaF3DWpBH/*.mjs`) —
  e.g. `react.*.mjs`, `rolldown-runtime.*.mjs`, `motion.*.mjs`. Animations
  (scroll effects, transitions, reveals) are driven by Framer Motion; this is
  the primary reason the repo exists as an "animation reference."
- **Styling**: Inline `<style>` blocks. Framer emits utility/generated class
  names and `data-framer-*` attributes (e.g. `data-framer-name`,
  `data-framer-component-type`) that map to design-tool layers. Fonts are
  **Geist** (Google Fonts + framerusercontent).
- **Assets**: Images and media are hot-linked from
  `framerusercontent.com/images/...` and `.../assets/...` — they are **not**
  vendored into the repo. Rendering offline will show missing images and no
  animation runtime.
- **Navigation**: Internal links are **relative `.html` paths**
  (`href="contact.html"`, `href="projects/velocity.html"`,
  `href="blogs/...html"`). There is no client-side router or clean-URL
  rewriting in the repo itself.

## Running / previewing

No build step. Serve the directory statically and open a page:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/index.html
```

Because the JS runtime, fonts, and images come from the Framer CDN, an
**online** preview looks correct while an **offline** one renders as unstyled /
image-less HTML. Relative links only resolve correctly when served from the
repo root (so `projects/*.html` and `blogs/*.html` sit under their folders).

## Editing conventions

- **Prefer not to hand-edit the generated HTML.** These files are large
  machine output; manual edits are brittle, easy to break, and will be lost the
  next time the site is re-exported from Framer. The canonical source is the
  Framer project, not this repo.
- If a change is genuinely required, **make the smallest possible targeted
  edit** (e.g. a specific meta tag, a specific link, a text string) rather than
  reformatting or "cleaning up" the document. Do not reflow or prettify — it
  produces enormous, meaningless diffs.
- **Do not read a whole page into context to make a small change.** Files run
  from ~0.5 MB to ~2.5 MB. Use `grep`/`ripgrep` to locate the exact string,
  then edit that spot. Reading an entire `index.html` is rarely necessary and
  wastes budget.
- Keep the **relative-link scheme** intact when moving or renaming pages —
  top-level pages link to `projects/*.html` and `blogs/*.html`, and those
  subpages link back up with plain filenames.
- If you re-export from Framer, replace files wholesale rather than merging by
  hand, and update `my_archive.zip` to match if you rely on it as a snapshot.

## Git workflow

- Active development branch for this work: **`claude/claude-md-docs-w65r6v`**.
  Develop, commit, and push there; create it from the latest default branch if
  needed. Do not push to `master` without explicit permission.
- Default branch: `master`. Remote: `origin`
  (`github.com/CoolNietzsche/starangel-reference`).
- Use clear, descriptive commit messages. Push with
  `git push -u origin <branch>`.
- Do **not** open a pull request unless explicitly asked.

## Quick reference for common requests

- **"How does animation X work?"** — Find the relevant page, grep for the
  section (`data-framer-name="..."`), and inspect the inline styles plus the
  Framer Motion module references. The behavior is defined by Framer Motion at
  runtime, not by static CSS keyframes alone.
- **"Change page text / a link / a meta tag."** — Grep for the exact string in
  the target file and make a minimal edit.
- **"Add a new page."** — Realistically this should be done in Framer and
  re-exported. If mocking one by hand, copy an existing page as a skeleton and
  keep the relative-link and asset-URL conventions.
- **"Why do images/fonts not load offline?"** — Everything is hot-linked to the
  Framer CDN; there are no local asset copies. This is expected.
