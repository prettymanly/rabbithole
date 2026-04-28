# Design — C-Levels pilot site redesign

| | |
|---|---|
| Date | 2026-04-28 |
| Status | DRAFT — pending user review |
| Authors | Ziff Lau + Jia Liang (rabbithole), spec captured by Claude |
| Repo | github.com/prettymanly/rabbithole |
| Live | rabbitholesg.vercel.app (canonical) → clevels.sg (target) |
| Supersedes | The current single-page v2 site (commit `ada76cd` and earlier) |
| Skill used | superpowers:brainstorming → superpowers:writing-plans (next) |

---

## 1 — Problem statement

The current `clevels.sg` is a single-page manifesto-style landing site for one programme. The user (Ziff) has clarified that the actual offering is a **brand umbrella with two programmes**, that the current page is "way too wordy," and that the page is not pushing readers toward booking a call.

The current page conflates four jobs:
1. Defining a new brand category (C-Levels, C-Level, the trilogy framing)
2. Selling a programme (was implicit; now needs to be **two** programmes side by side)
3. Acting as a manifesto / belief artefact
4. Driving a single conversion: book a call with the founders

These jobs pull the page in different directions. The result is a long single-page scroll that does no single job sharply.

## 2 — Goals & success criteria

### Primary goal (Q1 locked)
**Conversion.** Two Singapore schools commit to running pilot cohorts in 2026.

### Success criteria
- Two pilot schools confirmed within ~8 weeks (by end of Term 1).
- Each pilot school self-selects which programme to run (Curiosity or Design).
- The site is forwardable both as a URL and as a 1-page PDF; school leadership teams can ingest either format.
- The site holds two programmes without becoming wordier than the v2 single-page predecessor.

### Non-goals
- Cold inbound conversion at scale. The page is optimised for warm referrals from the founders' network, not SEO/social acquisition.
- Parent acquisition. Parents are deferred until the pilot lands; institutional adjacencies (private schools, NLB) get a one-line acknowledgement on the hub but no dedicated page.
- A pricing page. Paid cohort pricing is post-pilot.
- A blog or newsletter. The manifesto on `/why` is the long-form expression; nothing more is built for now.

## 3 — Key decisions (locked during discovery)

| # | Question | Decision | Implication |
|---|---|---|---|
| Q1 | Primary outcome | Conversion: 2 pilot yeses within 8 weeks | Page architecture serves the offer; manifesto deprioritised |
| Q2 | Most likely reader | Personal network (anchor: ACS principal, ex-Telok Blangah Rise VP from 2019/2020 DT collaboration; teacher friends) | Page is the closer after a personal text, not the discoverer |
| Q3 | Pilot scope | Both programmes available; schools self-select which to run | Both programmes need first-class presentation; the chooser block is critical |
| Q4 | Page architecture | Brand hub + 2 programme pages + 1 manifesto page + 1 PDF | Solves "wordy" structurally, not by trimming |
| Q5 | Brand line | "O-Levels test knowledge. A-Levels test analysis. C-Levels train the thinking AI can't do for them." (after voice revision in Q5b — Chipchase-flavoured rewrite of the original "trilogy completion" frame) | Three short sentences. Periods. Ends on "them" (the students). MOE-fluent trilogy framing. |
| Q6 | Programme names | C-Level: Curiosity / C-Level: Design | Mirrors the brand: one letter (C) → one word (programme name) → one framework (4Cs / 4Ds) |
| Q7 | Manifesto placement | Full text on `/why`; one-line tease on hub linking to it | Hub stays conversion-focused; manifesto preserved as forwardable artefact |
| Q8 | Primary CTA | Calendly primary, WhatsApp secondary, email tertiary | Removes the round-trip of "ask first, book later" |
| Q9 | Forwardable PDF | Yes — 1-page A4 portrait | Singapore schools forward documents; URLs alone don't survive internal email threads |
| Q10 | Methodology scope | Curiosity uses 4Cs (Curiosity → Clarity → Creation → Communication). Design uses 4Ds (Discover → Define → Develop → Deliver, AI embedded at every stage) | Beautiful brand mechanic: each programme's first-letter matches its 4-letter framework |

### Other locked details
- Both founders run both programmes (no per-programme attribution on programme pages).
- Site signals adaptability for private schools, NLB, and similar institutions — one italic line on the hub, no separate page.
- Timing is intentionally not specified in the hero (June, Term 3, end of 2026 all fine — discussed on the call).
- "v0.1 pilot" stamp visible in the footer, signalling this is a real release rather than a placeholder.

## 4 — Information architecture

```
clevels.sg/
├── /                        Brand hub          (~250 words, 7 sections, the chooser)
├── /curiosity               C-Level: Curiosity (~500 words, 8 sections)
├── /design                  C-Level: Design    (~500 words, 8 sections)
├── /why                     Manifesto in long form (~440 words, 6 sections)
└── /c-levels-brief.pdf      1-page A4 forwardable
```

Total site word count target: **~1,700 words across 4 pages + 1 PDF**, vs the current ~1,200 words on a single page. The site is *bigger* in volume but *shorter per page* — each page is single-purpose and below the threshold where wordiness re-emerges.

Nav across all pages: brand mark left ("C-Levels by rabbithole"), three text links right (`Curiosity`, `Design`, `Why`), `Talk to us` CTA on the far right pointing to Calendly. Current page link in nav gets a visual marker.

## 5 — Page-level designs

### 5.1 — `/` (Brand hub)

**Job:** position the brand in 8 seconds, give a principal a confident way to choose between programmes, drive her to Calendly. ~250 words total across 7 sections.

#### §1 Hero
- **Headline (Outfit display, weight 800, deliberate breaks):**
  > O-Levels test knowledge.
  > A-Levels test analysis.
  > **C-Levels** train the thinking AI can't do for them.
- "C-Levels" gets the orange `text-stroke` treatment — eye lands on the brand mark in the line.
- **Subhead:** "Two programmes for Singapore students aged 12–15. Two pilot schools. This year."
- **CTAs:** Calendly button primary + WhatsApp secondary. A quiet "Or read about both programmes ↓" anchor link below.
- **Trust strip (small caps):** "BUILT BY PRACTITIONERS FROM GOVTECH · GRAB · MOE EDTECH · SINGAPORE INSTITUTE OF TECHNOLOGY"
- No floating fragments / decorative chips / pulsing arrow / version badge in hero.

#### §2 The two C-Levels (chooser block)
Section intro:
> **TWO C-LEVELS · PICK YOUR FIT**
>
> One starts from an obsession.
> One starts from a problem.
> Both end with a student who can teach it back.

Two equal-weight cards side by side on desktop, stacked on mobile. Each card:

```
C-Level: Curiosity                 |  C-Level: Design
Turn one obsession into a          |  Turn one problem they keep noticing
learning pursuit they own.         |  into a working prototype.

For students who keep coming back  |  For students who fixate on what's
to one thing — a game, a song,     |  broken or could be better, and want
a question — but haven't been      |  to build, not just complain.
taught to follow it properly.      |

↓ Pick the obsession               |  ↓ Discover the problem
↓ Investigate with AI + sources    |  ↓ Define and prototype with AI
↓ Build a C-Level Board, teach it  |  ↓ Deliver a working solution

Method: 4Cs                        |  Method: 4Ds (AI-embedded)

Read about Curiosity →             |  Read about Design →
```

Same chrome on both. Method badge in orange. Read-more is a text link, not a button (buttons compete with the hero Calendly CTA).

#### §3 Run by
> **RUN BY**
>
> rabbithole — a learning studio working on student curiosity and self-directed inquiry. Both C-Level programmes are co-facilitated by **Ziff Lau** and **Jia Liang**.
>
> *Practice from GovTech · Grab · MOE EdTech · Singapore Institute of Technology · Hyper Island*

No headshots, no full bios. Bios live on programme pages.

#### §4 The pilot
> **THE PILOT**
>
> **Two Singapore schools, this year. No programme fee.**
>
> We haven't run a paid cohort yet. The two pilot schools keep the artefacts and the right to use them publicly. We co-document the run and write up what worked. Each school picks a programme — Curiosity or Design.
>
> *Also adaptable for private schools, NLB, and similar institutions that want a smaller version. Talk to us about format.*

Terms in semibold. Honesty paragraph as regular body. Italic line for institutional adjacencies.

#### §5 Why-tease
> **WHY WE'RE BUILDING THIS**
>
> Not what can we build.
> What should we build.
>
> *Read the longer thinking →*  *(link to `/why`)*

9 words + link. Two-line declarative pulled directly from the manifesto's spine.

#### §6 Final CTA
> **TALK TO US**
>
> *Twenty minutes is usually enough to know if there's a fit.*
>
>   `[ Book a 20-minute call → ]`   `[ WhatsApp ]`
>
>   *Or email hello@clevels.sg*

Dark inverse background to mark the page's closing — black bg, white text, blue button still pops. Primary CTA solid blue, secondary bordered.

#### §7 Footer
```
C-Levels ↓
by rabbithole · Singapore · 2026

Curiosity      Design      Why      Talk to us

hello@clevels.sg     ·     +65 9322 7317

"For students who want to know what sits behind the first answer."

© 2026 rabbithole · v0.1 pilot
```

---

### 5.2 — `/curiosity` (C-Level: Curiosity)

**Job:** give a principal who's clicked through enough depth to confidently book a call about Curiosity specifically. ~500 words across 8 sections.

#### §1 Hero
- Eyebrow: "C-LEVEL: CURIOSITY"
- Headline: **Turn one obsession into a learning pursuit they own.**
- Subhead: "A 1–2 day programme for Singapore students aged 12–15."
- CTAs: identical to hub.

#### §2 The obsession
> **FOR STUDENTS WHO…**
>
> Some students keep coming back to one thing — a football tactic, a song lyric, a manga world, a question living rent-free in their head.
>
> Most curricula treat that as distraction. We treat it as the starting line.
>
> *Curiosity* is the C-Level programme that takes one obsession and walks the student through the work of following it properly: sharpen the question, investigate with AI and primary sources, build something from what holds up, and explain it to someone who wasn't in the room.

#### §3 The 4Cs (methodology)

Four stacked/horizontal cards. Each: stage name + one-line job + concrete student-side example.

| Stage | Job | Example |
|---|---|---|
| 01 · Curiosity | Find the real question inside the obsession. | "Football" becomes "Why do some goalkeepers dive before the kick?" |
| 02 · Clarity | Sharpen the question before chasing answers. | "Topic" → "Inquiry" — a topic is not yet an inquiry. |
| 03 · Creation | Build something concrete from what holds up. | Theory · map · comic · guide · prototype · video · playlist with an argument. |
| 04 · Communication | Teach it to someone who wasn't in the room. | Vague thinking gets exposed in that conversation. |

Method badge: 4Cs in orange.

#### §4 The C-Level Board (artefact)
> **WHAT THEY WALK OUT WITH**
>
> Each student finishes their C-Level with a large-format visual record of their pursuit. Hand-drawn, designed for display, unique to every student.
>
> The Board captures:
> ↓ The question they pursued
> ↓ The sources they used
> ↓ How AI helped, and where it fell short
> ↓ What surprised them
> ↓ What they built
> ↓ What they still want to know

Image placeholder block (16:10): *Photo of an actual C-Level Board — coming after the first pilot run.*

#### §5 Format
> ↓ 1 or 2-day programme
> ↓ Ages 12 to 15
> ↓ Maximum 15 students per cohort
> ↓ Runs as enrichment, CCA, post-exam activity, learning festival, or holiday intensive
> ↓ No prior AI exposure required from students
> ↓ Adaptable to your school's device and platform rules
> ↓ Facilitated by Ziff Lau and Jia Liang, in person

#### §6 Facilitators
**Ziff Lau** — Service designer at GovTech on the Classroom of the Future initiative with MOE EdTech. Adjunct teaching design innovation at Singapore Institute of Technology. Master's at Hyper Island, with a 2019 thesis on AI-supported learning. Founder of Tumbo, helping Singapore parents find enrichment that fits a child's curiosity.

**Jia Liang** — UX researcher and service designer at Grab, where he co-developed internal research and design training curriculum. Has taught design thinking in multiple Singapore primary schools, volunteers weekly with children with special needs, and works inside MOE settings on curiosity-driven learning.

*Practice from GovTech · Grab · MOE EdTech · Singapore Institute of Technology · Hyper Island*

#### §7 Pilot offer
> **THE PILOT**
>
> **Two Singapore schools, this year. No programme fee.**
>
> We haven't run a paid Curiosity cohort yet. The two pilot schools become first-mover partners. They keep the artefacts, the documentation, and the right to use student work publicly. We co-write the case study.
>
> What your school gets:
> ↓ Completed C-Level Boards from every student
> ↓ A documented programme flow
> ↓ Student artefacts suitable for display or sharing
> ↓ A facilitator debrief
> ↓ Classroom integration notes
> ↓ Optional follow-up session two weeks later

#### §8 Final CTA
Same shape as hub CTA. Framing line: *"Twenty minutes is usually enough to know if Curiosity fits your students."*

Footer: identical to hub.

---

### 5.3 — `/design` (C-Level: Design)

**Job:** mirror /curiosity in structure with the design-thinking + AI lens. ~500 words across 8 sections. Programme pages must feel architecturally identical so a principal flipping between them experiences a clean side-by-side comparison.

#### §1 Hero
- Eyebrow: "C-LEVEL: DESIGN"
- Headline: **Turn one problem they keep noticing into a working prototype.**
- Subhead: "A 1–2 day programme for Singapore students aged 12–15."
- CTAs: identical.

#### §2 The problem they keep noticing
> **FOR STUDENTS WHO…**
>
> Some students can't stop noticing what's broken. The bus app that never updates. The PE warm-up that doesn't actually warm anyone up. The wet market mango stall that only mum knows the right one for. A frustration they keep coming back to.
>
> Most curricula treat that as complaining. We treat it as the brief.
>
> *Design* is the C-Level programme that takes one problem a student keeps noticing and walks them through the work of solving it properly: discover the people behind it, define what's actually broken, develop something that might fix it, and deliver a working prototype to someone who'd use it.

Three concrete Singapore-specific examples in the first sentence (tech / school / neighbourhood) so the principal mentally inserts her own students' equivalent frustrations.

#### §3 The 4Ds (methodology, AI-embedded)

| Stage | Job | AI as |
|---|---|---|
| 01 · Discover | Talk to people. See the problem in context. | Research assistant. Interview synthesis, secondary research, pattern-matching across user stories. |
| 02 · Define | Frame what's actually broken. | Thinking partner. Pressure-tests problem statements, surfaces assumptions, sharpens the brief. |
| 03 · Develop | Sketch, prototype, iterate. | Co-builder. Generates options, drafts copy, scaffolds code, produces visuals. Iteration cycles compress from days to hours. |
| 04 · Deliver | Test it with the people who'd actually use it. | Feedback synthesiser. Helps structure user testing, capture findings, decide what to keep. |

Method badge: **4Ds — AI-embedded** in orange.

#### §4 The prototype + Design Log
> **WHAT THEY WALK OUT WITH**
>
> Each student finishes Design with two things.
>
> **A working prototype** — could be an app mock-up, a service blueprint, a redesigned object, a public service announcement, a simple physical build. The format follows the problem.
>
> **A Design Log** — a hand-drawn record of how they got there. The user research, the dead ends, the version that didn't work, the version that did, what they'd change next time.

Image placeholder block (16:10): *Photo of student work — coming after the first pilot run.*

The Design Log is the artefact-twin of the C-Level Board. Both programmes leave a hand-drawn process record. Different format, same brand mechanic.

#### §5 Format
**Identical to /curiosity §5.** Same operational footprint shared across programmes.

#### §6 Facilitators
**Identical to /curiosity §6.** Same bios. Both founders run both programmes.

#### §7 Pilot offer
> **THE PILOT**
>
> **Two Singapore schools, this year. No programme fee.**
>
> We haven't run a paid Design cohort yet. The two pilot schools become first-mover partners. They keep the prototypes, the Design Logs, the documentation, and the right to use student work publicly. We co-write the case study.
>
> What your school gets:
> ↓ A working prototype from every student
> ↓ A Design Log per student
> ↓ A documented programme flow
> ↓ Student artefacts suitable for display or sharing
> ↓ A facilitator debrief
> ↓ Classroom integration notes
> ↓ Optional follow-up session two weeks later

#### §8 Final CTA
Framing line: *"Twenty minutes is usually enough to know if Design fits your students."*

Footer: identical to hub.

---

### 5.4 — `/why` (Manifesto)

**Job:** long-form thinking for the reader who came to think, not to convert immediately. ~440 words across 6 sections. Collective "we" voice (rabbithole as studio).

#### §1 Hero
> *WHY WE'RE BUILDING C-LEVELS*
>
> # Not what can we build.
> # What should we build.
>
> This is the question we've been writing about for the last year. C-Levels is what came out of it.

#### §2 Execution is now frictionless
> A year ago, shipping a working web app might have taken a team several months. Today, a single person with Claude or Cursor can draft one in a weekend. A simple prompt can generate a good-enough landing page in minutes. The same collapse is happening across design, video, music, research, and writing. The trajectory is still accelerating.
>
> So the old question holds. Not what can we build, but what should we build.

#### §3 Judgement is what's scarce
> As execution becomes frictionless, the scarce skill is increasingly judgement. The capacity to notice what matters before building anything. The rigour to ask what something costs, and who bears that cost. Underneath both, the instinct that insists a particular thing needs to exist.
>
> These are often called soft skills, though they may be the hardest ones to develop in a moment when the tools keep getting easier. They are also, we think, the skills a school curriculum now needs to centre.

#### §4 The script that worked for their parents
> Your students are entering an AI-exposed economy carrying a script that worked for their parents. Do well on the tests. Take the reliable path. The system will hold you. That story is beginning to loosen, and the reliable paths are being reshaped faster than any curriculum can track.
>
> The relationship between tests and the work AI will leave for humans is becoming less clear. The need to know what you are for will not change. To notice what only you, from where you stand, can see.

#### §5 Where C-Levels fits
> C-Levels is the small, deliberate version of that.
>
> Two programmes, both designed around what AI cannot do for a student: the asking, the judging, the building from evidence, the explaining.
>
> *C-Level: Curiosity* helps a student turn one obsession into a learning pursuit they own.
>
> *C-Level: Design* helps a student turn one problem they keep noticing into a working prototype.
>
> Both end with a student who can teach what they made to someone who wasn't in the room.
>
> That is the part of an AI-exposed school that we think is still teachable, and worth teaching well.

#### §6 Quiet CTA
> If your school is open to running one of the first two pilots, twenty minutes on a call is usually enough to know if there's a fit.
>
> `[ Book a 20-minute call → ]`
>
> *Or email hello@clevels.sg.*

Footer identical to hub.

---

### 5.5 — `c-levels-brief.pdf` (1 × A4 portrait)

**Job:** internal forwarding artefact for school leadership teams. Built as `/brief.html` with print stylesheet, exported to PDF, hosted at `/c-levels-brief.pdf`. Black on white, orange accent.

Layout (top to bottom, 6 vertical bands):

1. **Header band** — "C-Levels by rabbithole" + clevels.sg URL
2. **Brand line band** — "O-Levels test knowledge. A-Levels test analysis. C-Levels train the thinking AI can't do for them." (large, bold)
3. **Two-column programme body** — Curiosity left, Design right. Each: name, tagline, "for students who…" filter, methodology badge, ↓ stages, artefact line.
4. **Pilot band** — Two Singapore schools, this year, no programme fee, schools self-select, also adaptable for private schools / NLB.
5. **Format band** — single-line operational summary (1 or 2 days · ages 12–15 · max 15 · runs as ... · no prior AI required · school device rules · facilitated by Ziff & Jia Liang in person).
6. **Run-by band** — rabbithole + co-facilitators line + practice-from credentials.
7. **Contact band** — Calendly URL, WhatsApp, email, tagline, "v0.1 pilot" stamp.

No images, no headshots, no manifesto text. Bands separated by thin horizontal rules.

---

## 6 — Visual & technical conventions

### Type
- **Display:** Outfit (weights 600, 800)
- **Body:** Plus Jakarta Sans (weights 400, 500, 600, 700)
- **Utility:** Inter (weight 400, 500, 600 — labels, captions, small caps)
- All loaded from Google Fonts, same `<link>` pattern as v2.

### Colour
- `#000` black, `#fff` white, `#FAFAFA` off-white surface
- `#FF6200` orange — accent (down-arrows, brand-mark stroke, method badges)
- `#0000EE` blue — links and primary CTA buttons
- `#FFE815` yellow — used sparingly (e.g., the callout box on /parents in v2 — likely unused on the new structure)
- `#ABABAB` mid-grey — secondary text
- `#E0E0E0` light grey — borders, dividers

### Spacing
4px base scale: 4 / 8 / 12 / 16 / 20 / 24 / 28 / 32 / 36 / 40 / 52 / 60.

### Border-radius scale
0 / 6 / 8 / 12 / 16 / 20.

### Stack
- Vanilla HTML/CSS/JS per the project's CLAUDE.md.
- **Tailwind via CDN** for utility classes (matches current v2 file `index.html`).
- No build step. No npm. Each page is a single HTML file.
- Shared styles live in `/styles.css`, linked from every page via `<link rel="stylesheet" href="/styles.css">`. Per-page styles use `<style>` blocks for page-specific tweaks (e.g., the print stylesheet on `/brief.html`).

### Routing
- Vercel `vercel.json` with `cleanUrls: true` so URLs are `/curiosity`, `/design`, `/why`, `/brief` (no `.html` suffix).
- Files: `/index.html`, `/curiosity.html`, `/design.html`, `/why.html`, `/brief.html`.
- PDF at site root: `/c-levels-brief.pdf` — generated from `/brief.html` (manual export from browser print → PDF) and committed to repo.

### Analytics
- PostHog snippet on every page (existing pattern). `register: { page_version: 'main' }` replaces the `'v2'` tag.
- Per-page `register: { page: 'hub' | 'curiosity' | 'design' | 'why' }` for funnel analysis.
- CTA click tracking carries forward from current v2 wiring.

### Calendly
- `CALENDLY_URL_HERE` placeholder in code. User to fill before deploy:
  - One Calendly account (free plan)
  - One event type: "C-Levels — 20-min intro call"
  - Same URL used on hub, /curiosity, /design, /why, and brief PDF.

### WhatsApp
- `+65 9322 7317` (Raziff's mobile from his letter).
- Pre-filled message varies per page so we can tell from inbound which page triggered the click:
  - Hub: "Hi, I saw the C-Levels site and would like to talk about running it at our school."
  - /curiosity: "Hi, I saw the C-Levels: Curiosity page and would like to talk about it for our cohort."
  - /design: "Hi, I saw the C-Levels: Design page and would like to talk about it for our cohort."
  - /why: "Hi, I read your manifesto on C-Levels and would like to talk."

### Email
- `hello@clevels.sg` (existing).

## 7 — Migration plan (high level)

This is the design spec; the implementation plan comes from `superpowers:writing-plans`. High-level migration:

1. Promote current `/index.html` (v2 pilot) to `/archive/v2-single-page.html` as a fallback reference.
2. Build new `/index.html` (hub) per §5.1.
3. Build new `/curiosity.html` per §5.2.
4. Build new `/design.html` per §5.3.
5. Build new `/why.html` per §5.4.
6. Build `/brief.html` (print-stylesheet variant) and export `c-levels-brief.pdf`.
7. Add `vercel.json` with cleanUrls + redirects (e.g., legacy URLs → new equivalents if any).
8. Update `.claude/CLAUDE.md` to reflect the new structure.
9. Single commit + push → Vercel auto-deploy.
10. Update copy.md to match the new architecture (move v2 copy to /archive as historical, write new copy.md).

## 8 — Open questions / risks

1. **Calendly URL not set up.** User must create the Calendly account and provide the URL. Implementation can ship with a placeholder; deploy is blocked on the real URL.
2. **PDF generation workflow.** Decision: HTML+print-CSS exported manually via browser → committed PDF. Acceptable manual step (no CI), to revisit if content updates become frequent.
3. **No real photos yet.** All artefact placeholders honest about pre-pilot state. Once a pilot runs, photo placeholders become live photos — that's a future content update, not a structural change.
4. **Programme-1 facilitator load.** Both founders run both programmes. With 2 schools running concurrent pilots in different programmes (or even 2 of the same), facilitator availability is a real-world constraint that doesn't show up on the page but does in the call. Surface this in conversations.
5. **MOE EdTech / institutional approval.** If pilot schools require formal MOE pathway approval, the timeline of "by end of Term 1" may be optimistic. Page does not over-promise; conversations will surface this risk.
6. **Cross-page consistency drift.** Three programme-page elements (format §5, facilitators §6, pilot §7) are deliberately near-identical between /curiosity and /design. If they drift independently during edits, the chooser comparison breaks. Mitigation: extract shared sections into includes if duplication becomes painful, or treat as a known maintenance constraint.

## 9 — Out of scope (explicit)

- A `/parents` page or any parent-acquisition flow.
- A pricing page.
- A blog, substack, or newsletter signup.
- Translations (English only for now).
- Dark mode.
- Animation / motion design beyond what already exists in v2 (subtle hover states, the pulse-down arrow if retained).
- A11y audit beyond standard semantic HTML + sufficient contrast (defer formal WCAG audit until post-pilot).
- SEO optimisation beyond title, meta description, and clean URLs.
- Cookie consent banner (no cookies set besides PostHog's; revisit when site is Singapore-PDPA-evaluated).

## 10 — Reviewer notes (for the spec self-review)

To check before handing off to writing-plans:
- Are all CTAs identified (Calendly, WhatsApp, email) with the right defaults across pages?
- Is the wording consistent for the same concept across pages? (E.g., the "for students who…" filter, the pilot honesty paragraph, the format bullets.)
- Are the methodology cards (4Cs, 4Ds) symmetric in shape?
- Does the brand line appear identically wherever quoted?
- Is the "v0.1 pilot" stamp consistent (footer + PDF)?
- Are URLs consistent: `/curiosity`, `/design`, `/why`, `/c-levels-brief.pdf` (no `.html` suffix in user-facing copy)?
- Is the manifesto's full version on /why and quotes from it (e.g., "Not what can we build. What should we build.") match exactly?

---

## Approvals

- [ ] User reviews and approves spec
- [ ] Spec committed to `git`
- [ ] Hand off to `superpowers:writing-plans` for implementation plan
