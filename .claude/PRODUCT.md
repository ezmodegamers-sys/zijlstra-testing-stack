# AB Integrity — abintegrity.com

**Register:** brand (marketing site; design IS the product)

## What it is

Seven free, browser-only tools that pressure-test ecommerce A/B test results.
Nothing is uploaded, there are no accounts, and every calculation happens client-side.
Static HTML/CSS/JS, one self-contained file per page, deployed via Cloudflare Pages.

## Who it's for

Marketing and ecommerce leaders who are handed A/B test results by an agency or an
internal team and quietly doubt them. They are not statisticians. They need to know
whether a claimed winner survives scrutiny before it goes in a board deck.

Secondary: in-house experimentation people who want a second opinion on their own tests.

## Positioning

The second opinion. Humble authority, never condescending. The site never implies the
reader should already know this; it implies the reader is right to ask.

## Voice

Plainspoken, forensic, unbothered. Short declaratives. Concrete numbers over adjectives.

Hard rules:
- No em dashes anywhere in prose.
- No AI-tell vocabulary (delve, leverage, robust, seamless, unlock, elevate, landscape).
- No rule-of-three flourishes, no "it's not just X, it's Y".
- Claims are stated once, plainly, and then evidenced.

## Surfaces

- `/` homepage — tools index, Analyze entry point, blog feature, manifesto
- `/analyze` — one-shot verdict on a pasted results export
- `/portfolio` — **the paid tier.** One multi-activity export in, every test triaged
  worst-first. Checks that per-test platform reporting does not run: SRM, Sidak
  family-wise correction, achieved power, winner's-curse shrinkage, conversion-against-
  revenue conflict, pace-to-close. Owns the nav CTA. No payment backend yet; the pricing
  block is a mailto.
- 7 tool pages: aa-validator, lockbox, survival, reality-check, receipt, ledger, subscriber-value
- `/blog/`, `/learn/`, `/about`, `/privacy`

## Constraints

- Every page is a single self-contained HTML file. No build step, no framework.
- Fonts come from Google Fonts. Everything else is inline.
- Pages must work with JS disabled for reading; only the tools need JS.
- SEO matters: canonical is non-www https, Search Console is live.
