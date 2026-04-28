# rabbithole

## What we're building
A single-page marketing site for a Singapore education programme.
Primary audience: school leaders. Secondary: parents.
Stack: vanilla HTML/CSS/JS. Single index.html. Vercel deployment.

## Architecture decisions
- No frameworks. No build tools. No npm. One file only.
- Graph paper texture via CSS linear-gradient (not image files)
- Form submission is client-side only (no backend, no fetch)
- All fonts loaded from Google Fonts CDN

## Naming conventions
- CSS classes: BEM-lite — block__element (e.g. hero__headline)
- Section IDs match nav anchors: #schools, #parents, #method
- JS functions: camelCase, verb-first (e.g. handleFormSubmit)

## Design reference
jackiezhang.co.za — editorial, graph paper, letter stacking
Brand: rabbithole (always lowercase). Accent: ↓ symbol in amber.
Palette: #F5F0E8 / #1C3A2F / #E07A2F / #1A1A1A

## Never touch
.env files. Any API keys.

## /archive folder
Read-only reference. Holds superseded versions of the site (e.g. archive/v1-editorial.html).
Do not modify files inside it. Do not link to it from index.html — it should not be discoverable.
