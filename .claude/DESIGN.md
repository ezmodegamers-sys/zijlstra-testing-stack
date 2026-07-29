# AB Integrity — design system

## Scene

A CMO at 9am. Laptop on a bright desk, the agency's slide deck open in another tab,
a board call at 10. They want to know whether the +23% is real. Bright ambient light,
skeptical mood, five minutes to spare.

That scene forces a **light** surface. Dark would be costume here: the reader is not a
developer at night, they are an executive in a meeting room.

## Aesthetic lane

**Calibration lab, brightly lit.** The visual language of an instrument spec sheet
crossed with a confident consumer brand: big display type, hairline rules, real data
marks used as ornament, and one loud correction-pen color.

Explicitly not: dark terminal (the second-order reflex for a testing tool), not
editorial-magazine serif, not SaaS cream.

## Color

Strategy: **Committed.** Electric blue is the identity. Vermilion is the correction pen,
used only for the marker underline and for numbers being struck down. Acid lime is the
verified stamp and appears only on dark or blue fields.

| token | value | role |
|---|---|---|
| `--paper` | `#F6F7FB` | page |
| `--white` | `#FFFFFF` | raised surfaces |
| `--ink` | `#0A0D13` | headings, dark fields |
| `--ink-2` | `#4A5361` | body (7.3:1 on paper) |
| `--ink-3` | `#646D7B` | meta (4.7:1 on paper) |
| `--line` / `--line-2` | `#E2E7F0` / `#CFD7E4` | hairlines |
| `--blue` | `#1B44FF` | primary (6.3:1 on white) |
| `--blue-wash` | `#E8ECFF` | tints, offset shadows |
| `--red` | `#FF4A21` | underline, struck numbers (large only, 3.3:1) |
| `--lime` | `#C4F536` | verified marks, on dark fields only |

Per-tool accents, all ≥4:1 on white so the tool name stays legible when it takes the color:
green `#0F9A57` · blue `#1B44FF` · purple `#7B3FE4` · orange `#E0640B` · ink `#0A0D13` ·
amber `#A8760A` · teal `#0D9488`.

## Type

Kept from the existing identity; the overhaul is carried by color, scale and layout.

- Display: **Bricolage Grotesque** 700/800, letter-spacing `-0.035em` (never tighter than `-0.04em`)
- Body: **Inter** 400/500/600
- Data: **JetBrains Mono** 400/500/700, used for measurements and labels only, never prose

Scale is fluid `clamp()`, ≥1.25 between steps. h1 max 88px. Prose capped at 66ch.

## Layout

Page rhythm alternates surface: paper hero → paper logo band → **blue drench** (Analyze) →
paper tools → paper blog → **ink drench** (manifesto) → paper footer. Two color fields
break up what would otherwise be five white sections in a row.

Section separation is fluid: `clamp(64px, 9vw, 116px)`.

## Motion

One orchestrated page load, then almost nothing. Kicker, headline, marker underline draw,
sub, CTAs, floating chips, logo strip: staggered on `cubic-bezier(.16,1,.3,1)`.
Chips bob on a long loop. Everything else is hover-state only.

Reveals enhance an already-visible default: content is never gated on a class, so a
headless render or a background tab still ships the full page.

`prefers-reduced-motion: reduce` removes every animation and transition.

## Bans in force

No gradient text. No glassmorphism. No side-stripe borders. No nested cards. No tracked
uppercase eyebrow above every section (the hero carries one, deliberately, and no other
section does). Numbered markers appear once, on the seven tools, because that section
genuinely is an ordered index of seven things.

**No `//` prefix on labels.** Kickers, eyebrows and panel headers are the plain words:
`Portfolio`, not `// Portfolio`. The slashes were a code-comment affectation that reads
as machine-written, which is the exact opposite of what a trust product should sound
like. Removed sitewide 2026-07-29. The mono font and letter-spacing already carry the
instrument-panel register without borrowing syntax from a language nobody is writing here.

## Nav CTA

One pill, electric blue, white text (5.31:1, clears AA), darker blue on hover. It points
at the paid product, currently `/portfolio`. It is never hidden: below 430px the wordmark
gives way instead and the label shortens from "Review your portfolio" to "Portfolio" via
`.cta-l` / `.cta-s`. On the homepage the redundant `/portfolio` nav link also drops at
that width, because the CTA beside it already goes there. A CTA that disappears on a phone
is the same as not having one.
