---
name: seo-competitor-benchmark
description: Analyze a website for reusable SEO patterns, technical gaps, risks, and an impact-versus-effort action plan. Use when the user asks what to borrow from a competitor or reference site, requests a deep SEO benchmark, or wants content, technical, local, link, or brand signals evaluated.
---

# SEO Competitor Benchmark

Use this skill to study a reference website and extract practices worth adapting to another site. Treat the target as evidence, not as a model to copy blindly. Separate observed facts, informed inferences, and recommendations.

## Operating Rules

- Confirm the target URL, audience, language, geography, business model, and desired conversion before analysis.
- Ask for the user's own URL only when comparison would materially change the recommendation; do not block if none is available.
- Research facts yourself. Do not ask the user for crawl data, page counts, titles, schema, or public social signals that can be inspected.
- Browse current pages and cite primary sources where claims may change. Cite the target site's pages for observations and official Google documentation for SEO guidance.
- Never claim rankings, traffic, backlink counts, Google Business Profile ownership, Core Web Vitals, or indexation status without first-party or reliable measurement data.
- Mark inaccessible or unverified items as `待验证`; do not turn a failed fetch into a defect finding.
- Respect robots.txt, rate limits, copyright, and image licensing. Do not recommend scraping or reusing third-party images without permission.

## Workflow

### 1. Establish the benchmark brief

Record target URL, comparison URL if available, country, language, audience, business type, main conversion, required SEO dimensions, and desired report depth. If the target is a national content site without a real physical location, classify Google Business Profile and local citations as not applicable. Do not invent local entities.

### 2. Inspect the site

Fetch the homepage, About, author/profile pages, category pages, contact/privacy pages, sitemap, robots.txt, and 5-10 representative articles. Sample across major search-intent patterns such as season, color, style, product, location, or use case.

Capture evidence for titles, H1, meta descriptions, canonicals, robots directives, dates, authors, headings, URL patterns, taxonomies, pagination, breadcrumbs, related modules, content depth, originality, citations, media context, update behavior, image metadata, JSON-LD types, social profiles, creator credits, public links, and genuine local business details. When live fetching is unavailable, use indexed excerpts or public search results, label the limitation, and avoid precise technical claims.

### 3. Model the content strategy

Build a topic matrix using combinations of season/time, color/material, style/intent, form factor, occasion, and technique. Identify hub pages, spokes, repeated title patterns, seasonal refreshes, and keyword cannibalization. Explain which patterns are transferable and which depend on the target's brand, imagery, or authority.

### 4. Evaluate by dimension

Use these report sections: executive conclusion and scope; content and search intent; on-page SEO; architecture and internal links; technical SEO; structured data; images and licensing; local SEO/GBP/citations; backlinks/social/brand; risks not to copy; prioritized action plan.

For every material finding, use: `Observation` -> `Evidence` -> `Why it matters` -> `How to adapt` -> `Risk/constraint`.

### 5. Score and prioritize

Use a qualitative benchmark score unless reliable measurements are available:

| Dimension | Weight |
|---|---:|
| Content quality and intent fit | 25% |
| On-page SEO | 20% |
| Technical SEO | 20% |
| Architecture and internal links | 15% |
| Structured data and images | 10% |
| Authority, links, social, and brand | 10% |

Do not present this as Google's score. Call it a `借鉴价值评分` or `benchmark score` and explain the evidence basis. Prioritize with `expected organic/conversion impact x confidence / implementation cost`. Use P0 for indexability or licensing risks, P1 for high-impact content/architecture, P2 for growth/distribution, and P3 for long-term brand assets.

## Domain Guidance

### Content sites

Favor seasonal or trend clusters, image-led list pages, descriptive subheadings, original commentary, practical metadata, and evergreen hubs refreshed instead of duplicated yearly. Add useful dimensions such as difficulty, audience, tools, time, and use case.

### Local services

Recommend GBP, NAP consistency, local citations, reviews, photos, and location pages only when a real location or service area exists. Local visibility depends on relevance, distance, and prominence; completeness and review responses are operational requirements, not substitutes for a real business.

### Images and creator content

Treat attribution as separate from permission. Recommend original or licensed media, descriptive filenames and alt text, relevant page context, stable dimensions, modern formats, and an image-rights record. Never suggest copying Instagram, Pinterest, or creator images without authorization.

### Structured data

Recommend only types represented by visible page content. Validate with Rich Results Test and Schema Markup Validator. Do not add fake reviews, ratings, products, addresses, or hidden content. Structured data can make a result eligible for richer presentation but does not guarantee it.

## Action Plan Template

Return:

| Priority | Action | Evidence or target pattern | Expected impact | Cost | Owner/next step |
|---|---|---|---|---|---|

Include a short 30/60/90-day sequence. Typical high-value actions include validating robots/sitemap/canonical/schema, consolidating overlapping seasonal URLs, fixing image rights and metadata, adding author and review signals, strengthening hub-to-spoke internal links, expanding thin list entries with practical details, and building creator/brand partnerships.

## Final Quality Gate

Verify that the report distinguishes facts from inference and recommendations; cites externally verifiable claims; does not claim unavailable ranking, traffic, backlink, GBP, or CWV data; separates transferable patterns from target-specific style; includes a clearly labeled `不要照搬` section; ranks actions by impact and cost; and states crawl/data limitations.
