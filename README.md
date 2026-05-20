[![CI](https://github.com/martechbuilder/content-seo-engine/actions/workflows/ci.yml/badge.svg)](https://github.com/martechbuilder/content-seo-engine/actions)
![License](https://img.shields.io/badge/license-MIT-blue)
![Node](https://img.shields.io/badge/node-%3E%3D20-green)

# content-seo-engine

Three tools for the full content workflow — run them independently or chain them:

```
1. brief.js   → Claude generates a full content brief from topic + keyword + audience
2. score.js   → grades a finished post across 5 dimensions (100 pts total)
3. schema.js  → outputs Article + BreadcrumbList + FAQPage JSON-LD
```

## Quick start

```bash
npm install

# Generate a content brief
node src/brief.js \
  --topic="B2B Marketing Automation" \
  --keyword="marketing automation tools" \
  --audience="Marketing Manager" \
  --cluster="Marketing Ops"

# Score a post
node src/score.js path/to/post.html \
  --frontmatter='{"title":"…","description":"…","keyword":"marketing automation","author":{"name":"Jane"}}'

# Generate JSON-LD
node src/schema.js \
  --frontmatter='{"title":"…","slug":"post-slug","domain":"https://your-site.com","datePublished":"2026-01-15","author":{"name":"Jane"}}'
```

## Scoring breakdown (100 pts)

| Category | Pts | What's measured |
|---|---|---|
| Content quality | 25 | Word count, heading structure, external links, date specificity |
| SEO | 25 | Title/meta length, internal links, keyword placement |
| E-E-A-T | 20 | Author byline + credentials, freshness, sourced links |
| Technical | 15 | Image alts, lazy loading, paragraph length |
| AI citation readiness | 15 | TL;DR, Q&A headings, FAQPage schema |

**≥ 80** → ready to publish. **60–79** → one or two targeted fixes needed. **< 60** → rework first.

## Content brief output

- 3 title variants (all ≤ 60 chars, keyword included)
- Meta description (120–160 chars)
- Full H2/H3 outline
- Citation capsule — TL;DR-ready 2-paragraph answer for AI citation
- 5–10 recommended sources (Tier 1 preferred)
- Internal + external linking zones
- FAQ suggestions (feeds directly into FAQPage schema)
- Distribution angles: LinkedIn, email, Reddit

## Setup

```bash
cp .env.example .env
# Add ANTHROPIC_API_KEY
```

## License

MIT
