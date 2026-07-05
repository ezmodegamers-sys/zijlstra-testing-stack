# How to add a blog post

Each post is a standalone HTML file in `/blog/`. No build step. Five steps, ~5 minutes plus the writing:

1. **Copy the template**: duplicate `post-template.html` to `your-post-slug.html` (lowercase, hyphens, keywords in the slug — it becomes the URL `abintegrity.com/blog/your-post-slug`).
2. **Fill the head**: replace `POST TITLE HERE` and `POST-SLUG-HERE` everywhere (title tag, description, canonical, og: tags, JSON-LD). Write a unique `<meta name="description">` (~155 chars). Update `datePublished`/`dateModified` in the JSON-LD. **Delete the `<meta name="robots" content="noindex">` line** — it exists only to keep the template itself out of Google.
3. **Write the body**: replace the `<article>` content. Keep the meta row (date · category · read time), the standfirst, and the byline. `<h2>` sections with the `<span class="num">01</span>` numbering, links to the tools where relevant, one `.callout` if there's a key insight, the `.a-cta` block at the end.
4. **List it**: add a `.post-card` to `blog/index.html` (newest on top) — copy an existing card, update href/date/category/read time/title/excerpt.
5. **Register it**: add a `<url>` entry to `/sitemap.xml` and an `<item>` to `/blog/feed.xml` (copy an existing one). Update the `<lastBuildDate>` in the feed.

Then commit and push — Cloudflare Pages deploys it in under a minute.

Voice notes: direct, technically precise, no hedging. Short declarative openers. Bold the one sentence per section the reader must keep. Every claim about statistics should be checkable — same standard as the "// the math" sections in the tools.
