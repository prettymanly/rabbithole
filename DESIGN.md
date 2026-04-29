# C-Levels — design system reference

A working reference for anyone editing this site.
Read this before adjusting type, spacing, or colour. Especially before adjusting type.

---

## The one rule

**8 / 2 / 1 hierarchy.**

Per page, you get:
- **One** display moment (the hero `<h1>`)
- **Two** secondary headers (section `<h2>`s)
- **Eight-or-so** body-scale moments (lead paragraphs, list items, card bodies)

Ratios between them, on a desktop screen:
- Hero ≈ **1.5×** the secondary headers
- Secondary headers ≈ **3×** body text
- Therefore hero ≈ **4.5×** body text

If the hero feels like it swallows the page, you've broken the ratio. Drop a tier. The pages on this site use `text-huge` (96px max) for the hero, not `text-mega` (166px max), for exactly this reason. `text-mega` is reserved for poster-style moments only.

---

## Type tokens (in tailwind.config in each page's `<head>`)

| Token | Size (clamp) | Weight | Used for |
|---|---|---|---|
| `text-mega` | 56px → 166px | 800 | Reserved. Don't use unless the page is one big poster. |
| `text-huge` | 40px → 100px | 800 | Hero h1 on every page |
| `text-big`  | 32px → 64px  | 800 | Section h2s |
| `text-lead` | 20px → 30px  | 600 | Lead paragraphs, card subtitles |
| Body (default) | 16–18px | 400 | Everything else |
| Caption / label | 11px | 700, uppercase, tracked | Section labels, eyebrow text |

Line-height and tracking are baked into the tokens — don't override locally without a reason.

**Fonts:** Plus Jakarta Sans (display + body), Outfit (heroes only), Inter (UI / utility / labels).

---

## Colour tokens

| Token | Hex | Used for |
|---|---|---|
| `blue` | `#0000EE` | Primary CTA, links, "Talk to us" button |
| `blue-deep` | `#0B1DFF` | Hover state on blue |
| `orange` | `#FF6200` | Brand accent. The "C-Levels" wordmark in copy. Bullets. Section labels variant. |
| `yellow` | `#FFE815` | Reserved for callouts / hover moments |
| `black` | `#000000` | Body text, dark sections, card borders |
| `white` | `#FFFFFF` | Body bg, dark-section text |
| `off-white` | `#FAFAFA` | Alternating section bg |
| `gray-light` | `#E0E0E0` | Borders, dividers |
| `gray-med` | `#ABABAB` | Secondary text, muted labels |

**Rule:** every section is one of `bg-white`, `bg-off-white`, or `bg-black`. Alternate to create rhythm. Never use a third bg colour without justification.

**Rule:** `text-orange` is a focus glyph. Use it for the brand wordmark and accent moments. Never for body text. Never on white-on-white (use `text-orange` instead of `text-stroke` if the stroke disappears — see the hub hero).

---

## Spacing rhythm

Stick to Tailwind's default scale (4px increments). The pages use:

- Section padding: `py-20` (80px) on most sections, `py-24` (96px) on dark final-CTA
- Section horizontal: `px-6 md:px-12` (24px → 48px)
- Container: `max-w-[1440px] mx-auto` on `<main>`, narrower on text columns
- Text columns: `max-w-2xl` (~672px) for body prose, `max-w-3xl` for slightly wider, `max-w-4xl` for hero block. Never set a body column wider than `max-w-4xl`.
- Vertical between paragraphs: `space-y-5` for prose, `space-y-3` for lists

**Rule:** if it doesn't fit a Tailwind default token (`gap-4`, `mb-8`, `py-20`, etc.), pause before reaching for an arbitrary value. Usually the layout is wrong, not the spacing.

---

## Component patterns

### Section label (eyebrow)
```html
<span class="section-label">YOUR LABEL</span>
```
Defined in `styles.css`. Always uppercase, tracked, blue by default. Variants: `section-label--orange`, `section-label--yellow` for dark sections.

### Down-arrow bullet list
```html
<li class="flex items-start"><span class="text-orange font-bold mr-3">↓</span>List item text</li>
```
The orange ↓ is the brand bullet. Use everywhere a bulleted list would otherwise use a `•`.

### Pill button (primary)
```html
<a class="bg-blue text-white font-inter font-bold uppercase text-xs tracking-[0.18em] px-7 py-4 rounded-full hover:bg-blue-deep transition" href="…">Book a 20-minute call →</a>
```

### Pill button (secondary, outline)
```html
<a class="border-2 border-black text-black font-inter font-bold uppercase text-xs tracking-[0.18em] px-7 py-4 rounded-full hover:bg-black hover:text-white transition" href="…">WhatsApp</a>
```

### Card (programme chooser)
```html
<a href="…" class="group block border-2 border-black bg-white p-8 hover:bg-black hover:text-white transition-all duration-300">
  …
</a>
```
Black border, white bg, full inversion on hover. No shadows, no rounded corners (the cards are square against the pill buttons — that contrast is intentional).

---

## Voice rules (copy)

These come from earlier rounds of editing. Don't re-introduce what we've already cut.

**Avoid:**
- AI-trope tricolons used as filler ("visible, explainable, and repeatable")
- Anaphora chains used to build false weight ("It does not… It does not… It does not…")
- "Not X. But Y." constructions when the contrast isn't earned
- Staccato fragment lists meant to feel punchy ("A theory. A guide. A map.")
- Headlines that double as taglines without saying what the thing is
- Em-dashes used as filler. We use commas, periods, or restructure.

**Prefer:**
- Singular voice ("the student who…") over generic plural ("students who…")
- Concrete examples (canteen redesign, school app, football tactic) over category nouns (problems, interests)
- One claim per paragraph
- Singapore spelling: programme, behaviour, centre, organise, practise (verb)
- Lowercase "rabbithole". Capitalised "C-Levels", "C-Level: Curiosity", "C-Level: Design".

---

## Page hierarchy (the architecture)

- **/** — hub. ~250 words. Brand line + chooser + run-by + pilot + why-tease + dark final CTA + footer.
- **/curiosity** — Programme 1 page. Hero + obsession framing + 4Cs methodology + C-Level Board artefact + format + facilitators + pilot offer + CTA.
- **/design** — Programme 2 page. Hero + problem framing + 4Ds methodology (AI embedded) + prototype + Design Log + format + facilitators + pilot offer + CTA.
- **/why** — manifesto. Long-form essay. The argument behind both programmes.
- **/archive/*** — historical versions. Don't link to from main pages.

Each non-/why page has identical nav and footer. /why's structure is essay-style.

---

## When you're tweaking

1. Change the smallest thing that achieves the result. A whole section rarely needs to change when a single line does.
2. Look at the page on mobile (375px) AND desktop (1440px) before you push. Both should breathe.
3. If you cross 3 sections of edits in one commit, split into multiple commits. Easier to revert one bad call without losing the others.
4. Run `python3 -m http.server 8080` locally before pushing. Eyeball it. Vercel deploys are fast but visiting your own URL on production to find your typo is undignified.
5. If you're unsure about a type/colour choice, the answer is almost always "use the existing token, don't introduce a new one."

---

## When you're stuck

If it doesn't sing, the answer is almost always one of:

- Too much text (cut 30%)
- Too many CTAs (one primary, one secondary, max)
- Wrong hierarchy ratio (probably hero too big — try `text-huge` not `text-mega`)
- Three colours competing (drop to two)
- Spacing too tight or too varied (round to the nearest Tailwind token and re-eyeball)

When in doubt, default to less.
