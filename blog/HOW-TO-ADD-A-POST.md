# How to add a blog post

Each post is a standalone HTML file in `/blog/`. No build step. Five steps, ~5 minutes plus the writing:

1. **Copy the template**: duplicate `post-template.html` to `your-post-slug.html` (lowercase, hyphens, keywords in the slug — it becomes the URL `abintegrity.com/blog/your-post-slug`).
2. **Fill the head**: replace `POST TITLE HERE` and `POST-SLUG-HERE` everywhere (title tag, description, canonical, og: tags, JSON-LD). Write a unique `<meta name="description">` (~155 chars). Update `datePublished`/`dateModified` in the BlogPosting JSON-LD, and the position-3 name/url in the BreadcrumbList JSON-LD. **Delete the `<meta name="robots" content="noindex">` line** — it exists only to keep the template itself out of Google.
3. **Write the body**: replace the `<article>` content. Keep these scaffolding pieces and just update their text:
   - the `.crumbs` breadcrumb nav (set the last `.here` label to a 2-3 word topic),
   - the `.a-meta` row: `<time datetime="YYYY-MM-DD">` (machine-readable date, keep it accurate), category, and read time,
   - the standfirst and byline,
   - `<h2>` sections with the `<span class="num">01</span>` numbering, links to the tools where relevant, one `.callout` for a key insight, the `.a-cta` block, and the `.author` bio block at the very end.
   Read time = words ÷ 220, rounded. Count with: `grep -o '<article.*</article>' post.html | sed 's/<[^>]*>//g' | wc -w`.
4. **Feature it on the index** (`blog/index.html`): move the current `.feature` post down into the `.posts` list as a `.post-card`, then make your new post the `.feature` (update image, meta, title, excerpt, href). If there's no relevant image yet, reuse `og-image.png`. Also add the new post to the `blogPost` array in the index's Blog JSON-LD.
   Then update the two homepage spots on `/index.html`: the `.hero-note` pill (new post title + href) and the `.blog-feature` card in the `from-blog` section (image, meta, title, excerpt, href).
5. **Register it**: add a `<url>` entry to `/sitemap.xml` and an `<item>` to `/blog/feed.xml` (copy an existing one). Update the `<lastBuildDate>` in the feed.

Then commit and push — Cloudflare Pages deploys it in under a minute.

**Give each post an image.** Posts with a relevant image get better click-through in search and social, and the image itself can rank in Google Images. Build a 1200×630 PNG the same way the site's charts are made: write an HTML file styled with the site's CSS variables, then render it with headless Chrome (`"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --screenshot=out.png --window-size=1200,630 file://$PWD/chart.html`). Always give the `<img>` a descriptive `alt` that states what the chart shows — that alt text is itself an SEO signal.

Voice notes: direct, technically precise, no hedging. Short declarative openers. Bold the one sentence per section the reader must keep. Every claim about statistics should be checkable, the same standard as the "// the math" sections in the tools.

Anti-AI-tells checklist (run every draft through this before publishing):
- No em dashes or en dashes in prose. Use a period, comma, colon, or parentheses instead. (Title-tag separators like "Post Title — Zijlstra Testing Stack" are the site's naming convention and stay.)
- No rule-of-three rhythm ("X, Y, and Z" as a rhetorical flourish). Lists are fine only when they enumerate real things.
- No negative parallelisms ("It isn't X; it's Y", "not just X but Y").
- No "-ing" trailers that fake depth ("...highlighting the importance of...").
- No inflated significance ("pivotal", "testament", "landscape", "underscores").
- Vary sentence length. One short punchy sentence is emphasis; three in a row is theatre.
