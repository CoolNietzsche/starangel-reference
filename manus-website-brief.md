# Build Brief for Manus AI — Star Angels Website

## 0. Your task, in one line

Design and build a **brand-new, world-class marketing website** for **Star Angels**, a
high-rise construction *finishing* specialist in Addis Ababa, Ethiopia. **You own the
design.** I am giving you the content, the brand, the quality bar, and a strong motion
brief — but **not** a template, layout, or visual system. Invent something distinctive.

Deliver a modern, blazing-fast, fully responsive site that feels alive with motion
(Framer Motion–style transitions, parallax, scroll-reveals, micro-interactions) without
ever feeling gimmicky or slow.

---

## 1. About the company

**Star Angels** (Star Angels Construction PLC) is a construction **finishing** specialist —
not a general contractor. They make buildings *look finished and stay finished*: the paint,
the glass, the facade, the surfaces you see when you look up at a tower. Based on **Bole
Road, Addis Ababa, Ethiopia**, founded **2016**.

**What the site is for (in priority order):**
1. **Build the brand** — look like the most premium finishing firm in Addis Ababa.
2. **Tell the owner's story** and establish trust and craftsmanship.
3. Act as a **24/7 salesperson** — convert visitors into quote requests / calls / WhatsApp.
4. **Showcase services and completed work.**
5. **Support frequent tender / procurement submissions** — this matters: evaluation teams
   visit the site to vet the company, so it must read as credible, established, and
   documentation-ready.

**Audience:** building owners, developers, property managers, architects/GCs, and
government/institutional **procurement & tender evaluators**. Mostly Ethiopian, viewing on
**mobile first** and often on slower connections — performance is not optional.

**Positioning words:** precision, elegance, height, safety, craftsmanship, trust,
skyline, "the shine on the building."

---

## 2. Creative direction — freedom, with a high bar

**You decide** the layout, whether it's single-page or multi-page, the grid, the type
system, the color palette, the art direction, and the component design. Do not copy a
known template. Take one real aesthetic risk that suits a premium construction-finishing
brand.

**Non-negotiables (the bar, not the look):**
- Feels **premium and modern** — think top-tier studio/agency polish, not a generic
  contractor site or a bootstrap theme.
- **Editorial, confident typography** with a clear hierarchy and a real type scale.
- **Photography-forward** — big, cinematic building/facade imagery is the hero of the
  brand (a strong photo set is provided; see §7).
- **Restraint in color:** likely a calm neutral system with **one** decisive accent. The
  current brand accent is a warm orange-red **`#F55733`** — you may use, refine, or replace
  it; justify whatever you choose.
- **Light and dark both considered**, and both legible.
- **Accessible** (WCAG AA contrast, keyboard-navigable, focus states, alt text).

**Avoid:** cliché "AI-generated" looks (cream + terracotta + serif, purple-blue gradient
hero, everything centered, rounded-everything, emoji section markers), stocky corporate
clip-art, and anything that reads as a cheap template.

---

## 3. Motion & interaction — the part I care most about

This site should feel **alive**. Motion must be **purposeful, smooth (60fps), and
performance-budgeted**, and must **respect `prefers-reduced-motion`** (degrade to instant,
legible states). Progressive enhancement: with JS off, all content is still visible.

Use a real motion system (**Framer Motion** if React, or GSAP + ScrollTrigger + Lenis if
not). Include, at minimum:

- **Orchestrated page-load reveal** — a considered entrance sequence, not everything at once.
- **Scroll-triggered reveals** — staggered fade/slide/scale as sections enter the viewport
  (per-element stagger, not whole-section pop-in).
- **Parallax** — layered depth on the hero and on section imagery; subtle, not seasick.
- **Sticky navbar** that transforms on scroll (transparent → solid/blur, size/shadow shift).
- **Smooth momentum scrolling** (e.g. Lenis) and **smooth in-page anchor navigation**.
- **Animated number counters** for the stats, triggered on scroll into view.
- **Auto-scrolling marquee / ticker** (e.g. the six services or a tagline loop), pausing on
  hover.
- **Hover micro-interactions** — buttons (magnetic / fill / arrow slide), links (underline
  grow), image cards (zoom / tilt / reveal caption).
- **Accordion** for the FAQ (smooth height, one open at a time).
- **Section-to-section transitions** and tasteful reveal of imagery (clip-path / mask / image
  scale-in).
- Optional, only if it stays classy: a custom cursor, text scramble/split-text headings,
  scroll-progress indicator.

**Guardrails:** keep total motion cohesive (a consistent easing/spring language), never
block reading, never cause layout shift (CLS≈0), and keep the main thread free enough that
scrolling never stutters on a mid-range Android phone.

---

## 4. Technical requirements

- **Performance:** Lighthouse **90+ on mobile** for Performance/SEO/Best-Practices/A11y.
  Target LCP < 2.5s on 4G, CLS ≈ 0. Ship responsive, lazy-loaded **WebP/AVIF**; preload the
  hero; code-split; avoid heavy unused JS.
- **Responsive:** mobile-first, fluid down to ~320px and up to large desktops; real
  attention to the mobile nav, tap targets, and mobile motion (lighter, not absent).
- **Stack:** your choice — a modern one (e.g. **Next.js / React + Framer Motion + Tailwind**,
  or Astro, or SvelteKit). If it can be a **static/SSG export**, even better: it must deploy
  to shared **cPanel hosting** as static files (it will live at a subdomain document root,
  served by Apache). If you use a framework, provide a static-export build.
- **SEO:** semantic HTML5, sensible headings, meta/OpenGraph/Twitter tags, `sitemap.xml`,
  `robots.txt`, descriptive titles, JSON-LD `LocalBusiness` schema (Addis Ababa, phone,
  hours if known).
- **Accessibility:** landmarks, alt text, focus-visible, reduced-motion, color contrast.
- **Analytics-ready** and a working **contact path** (form + click-to-call + WhatsApp).
- **No fake backends:** the contact form can post to a simple endpoint or mailto/WhatsApp;
  don't fabricate a server.

---

## 5. Content integrity rules (read this — it's a hard rule)

This site is used for **tenders**, so **do not invent facts**. Use the content below exactly
as marked:

- **[CONFIRMED]** — real, safe to publish.
- **[DRAFT]** — written copy you may use and polish; keep the meaning.
- **[PLACEHOLDER]** — a real gap. **Build the section beautifully but leave a clear
  placeholder** (e.g. "Client testimonial to be added", "Registration details available on
  request"). **Never** invent client names, quotes, project details, registration/license
  numbers, certifications, insurance figures, or statistics.

---

## 6. The content

### Brand basics — [CONFIRMED]
- **Name:** Star Angels (legal: Star Angels Construction PLC)
- **Location:** Bole Road, Addis Ababa, Ethiopia
- **Founded:** 2016
- **Phone:** +251 913790984 and +251 924451560 (both reach the General Manager)
- **WhatsApp:** +251 913790984
- **Email:** starangelsconstructionplc@gmail.com
- **Proof stats:** 50+ Projects Completed · 98% Client Satisfaction · 6 core services · since 2016

### Hero — [CONFIRMED headline, keep it]
- **Headline:** Transforming Skylines with Precision & Elegance
- **Subhead:** Addis Ababa's premier construction finishing specialist, offering world-class
  solutions for high-rise buildings.
- **Primary CTA:** Get a Quote  ·  **Secondary:** See Our Work / Learn More
- **Visual:** rope-access technicians finishing a glass facade at height (provided).

### Services (six) — [CONFIRMED names] + [DRAFT descriptions]
1. **High-Rise Painting** — From single facades to full tower recoats, planned around access,
   weather, and occupancy so your building looks new without disrupting the people inside it.
2. **Glass Solutions** — Every pane measured, cut, and fitted for a precise structural
   finish — mirrors, curtain walls, and specialty glazing handled by technicians trained for
   height.
3. **Building Decoration** — Interiors and exteriors taken from functional to memorable,
   aligning finishes with how the space is actually used.
4. **Structural Cleaning** — Rope-access and lift-based cleaning that keeps glass, stone, and
   metal surfaces maintained year-round, not just after a one-time job.
5. **Facade Renovation** — Aging exteriors restored to current standards: structural repair,
   resealing, and refinishing in one coordinated scope.
6. **Consultancy** — Before you commit budget, we scope the finishing work realistically —
   what it will actually take, cost, and require access-wise.

### About / Story — [CONFIRMED facts] + [DRAFT narrative]
Facts: founded in Addis Ababa in 2016; grew from a local contractor into a leading high-rise
finishing specialist; 50+ projects; 98% client satisfaction; combines traditional
craftsmanship with modern technique.

Draft narrative (polish, keep meaning):
> Star Angels began in Addis Ababa with a simple idea: high-rise finishing should be done
> with the same precision the buildings themselves demand. What started as a local
> contracting outfit has grown into a specialist team trusted with some of the city's most
> visible facades — the kind of work you see every time you look up.
>
> Founder **Yared Kebede** built the company on the belief that construction finishing is
> where a building's first impression actually happens. A structure can be engineered
> perfectly and still fall short if the finish — the paint, the glass, the facade — isn't
> handled by people who understand height, precision, and the realities of working on
> occupied buildings.
>
> Today, Star Angels combines traditional craftsmanship with the technical rigor high-rise
> work demands: rope access, precision glazing, and finishing systems built to last through
> Addis Ababa's climate and construction pace.

*(A specific early project or turning point from Yared would strengthen this — leave room.)*

### Stats band — [CONFIRMED]
Animated counters: **50+** Projects Completed · **98%** Client Satisfaction ·
**Since 2016** · **6** Specialist Services.

### How We Work — process, 5 steps — [DRAFT, standard finishing workflow]
1. **Site Assessment** — We walk the building, assess access, and scope the real condition of
   the surface or glazing.
2. **Proposal & Planning** — A clear, itemized plan: materials, timeline, safety protocol,
   and cost.
3. **Access & Safety Setup** — Rope access, lifts, or scaffolding — whatever the building and
   job require, set up to code.
4. **Execution** — Skilled technicians carry out the work with minimal disruption to
   occupants.
5. **Quality Check & Handover** — Final inspection against the original scope before sign-off.

### Portfolio / Featured Projects — [CONFIRMED project names] + [PLACEHOLDER details]
Real, notable projects (safe to name): **La'Gahare, Eagle Hills, East African Holding,
Piassa, PPP Project, Tor-Hailoch, Anbessa.**
Build an attractive project grid/showcase using these names. For each, **leave placeholders**
for scope, building/client type, and photos (e.g. "Case study and project photography coming
soon"). **Do not invent** scope, storey counts, dates, or client details.

### Team / Leadership — [CONFIRMED names & roles]
- **Yared Kebede** — General Manager
- **Hibst Kebede** — Vice Manager
- **Henok Kebede** — Auditor
- **Birhanu Abate** — Quality Manager
- **Meskerem Kebede** — Marketing Manager *(no photo yet — use a tasteful placeholder)*
- **Meron Yeshiwond** — Architect *(no photo yet — use a tasteful placeholder)*

*(Optional trait tags if you want texture — treat as [DRAFT]: Yared — Visionary Leader,
Organizer; Hibst — Balanced Decision-Maker, Problem Solver; Henok — Detail-Oriented,
Analytical; Birhanu — Quality-Focused, Rigorous. Real bios would be better — leave room.)*

### Tenders & Credentials — [PLACEHOLDER, high priority section]
This replaces any "pricing" idea — finishing work isn't sold in monthly plans. Build a
**procurement-focused** section titled around **"Built for Procurement Review."**
Intro (confirmed intent): *Star Angels regularly participates in tender processes for
construction finishing work; this section gives procurement and evaluation teams what they
need quickly.*
Present clean, credible **placeholders** (fill later, do not invent):
- Business registration / trade license number — *available on request*
- Safety certifications & compliance — *to be provided*
- Insurance coverage (public liability, workers') — *to be provided*
- Notable delivered / institutional projects — *(use the real project names above)*
- References — *available on request*
Make this section feel trustworthy and document-ready.

### Testimonials — [PLACEHOLDER — do NOT fabricate]
Design a beautiful testimonials area, but **do not write fake client quotes or names**.
Use a clear state like "Client testimonials — being collected" with 2–3 empty, styled slots
ready to receive real quotes later, or a tasteful CTA to request references.

### FAQ — [DRAFT, safe]
1. **What areas do you serve?** — We're based in Addis Ababa and work throughout the city on
   high-rise and commercial buildings.
2. **Do you handle occupied buildings?** — Yes — our access methods and scheduling are built
   around minimizing disruption to tenants and operations.
3. **Can you provide documentation for tender submissions?** — Yes, we provide registration,
   licensing, insurance, and project-history documentation on request.
4. **What's your typical project timeline?** — It depends on scope and building size; we
   provide a clear timeline as part of every proposal.
5. **Do you offer consultancy without a full project commitment?** — Yes — our consultancy
   service is available standalone for planning and budgeting support.

### Contact — [CONFIRMED]
- **Phone:** +251 913790984 · +251 924451560 (click-to-call)
- **WhatsApp:** +251 913790984 (floating WhatsApp button + link)
- **Email:** starangelsconstructionplc@gmail.com
- **Address:** Bole Road, Addis Ababa, Ethiopia (embed a map)
- **CTA line (keep):** *Ready to Elevate Your Project? Let's collaborate to create something
  extraordinary.*
- **Contact form:** Name, Email, Phone, Service needed (the 6 services), Message → email or
  WhatsApp. Don't fake a backend.

### Footer — [CONFIRMED]
Brand, one-line positioning, nav, the contact details above, social links (placeholders if
unknown), "© Star Angels — Construction Finishing, Addis Ababa. Founded 2016."

### Insights / News — [OPTIONAL, PLACEHOLDER]
If you include a blog/insights area, keep it as a clearly-labeled "coming soon" placeholder.
No fabricated articles.

---

## 7. Assets

A set of **optimized photographs is available** (provide them to Manus alongside this brief)
covering: **hero** (rope-access on a glass facade), one image **per service** (painting,
glass, decoration, cleaning, renovation, consultancy), **process/site** shots, **portfolio**
building exteriors, a **team group photo** (Yared, Hibst, Henok, Birhanu — the two newest
members are not pictured), a **contact/brand** image, and a **footer** image. Optimize
further as needed (responsive sizes, AVIF/WebP).

- **Logo:** none final yet — design a clean, scalable wordmark + mark that fits the brand
  (star / skyline / precision cues), plus a favicon. Keep it tasteful and monochrome-capable.
- **Missing:** individual portraits for Meskerem Kebede and Meron Yeshiwond; project-specific
  photos and case studies; real credentials/registration numbers; real testimonials.

---

## 8. Deliverables & acceptance criteria

**Deliver:**
1. The complete website source, plus a **static production build** deployable to cPanel
   (Apache document root). Include an `.htaccess` (force HTTPS, gzip/brotli, cache headers).
2. `sitemap.xml`, `robots.txt`, favicons, OpenGraph image.
3. A short README: stack, how to run, how to build the static export, how to edit content,
   and where each [PLACEHOLDER] lives.

**Acceptance criteria:**
- Looks premium and distinctly *not* templated; photography-led; cohesive type & color.
- Motion is rich, smooth (60fps), purposeful, and honors `prefers-reduced-motion`.
- Mobile Lighthouse 90+ (Perf/SEO/BP/A11y); LCP < 2.5s/4G; CLS ≈ 0.
- Fully responsive 320px → large desktop; excellent mobile nav and tap targets.
- **Every fact matches §6 exactly; every gap is a clear placeholder — nothing invented.**
- Working contact: form + click-to-call + WhatsApp; map embedded.
- Deploys as static files to shared cPanel hosting.

Build something Star Angels can proudly hand to a client — or a tender committee — on the
first look.
