# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal/professional website for Emily Lewis-Pinnell (emilylewispinnell.com). Static HTML/CSS site — no build tools, no framework, no package manager. Rebuilt from a React/Tailwind source into plain HTML + CSS.

## Site Structure

- **index.html** — Main homepage (hero, about, thought leadership cards, media/speaking, connect form)
- **insights.html** — Full insights/publications page with client-side filtering by content type (article, podcast, video, webinar, interview, speaker)
- **404.html** — Custom 404 page
- **css/style.css** — Single stylesheet for all pages
- **images/** — Site images (headshots, logos, OG image)
- **preview-*.html** — Preview/snapshot versions of pages (large files, not for editing)
- **sitemap.xml**, **robots.txt** — SEO files
- **body.json** — Sample form payload

## Development

No build step. Edit HTML/CSS directly and open in a browser to preview. There are no tests, linters, or dev servers configured.

## Key Patterns

- Both `index.html` and `insights.html` share the same `css/style.css` and use the same component class conventions (`.section-header`, `.tl-card`, `.btn`, `.container`/`.container-wide`).
- Thought leadership cards use `data-type` attributes for filtering on the insights page. The filter script is inline at the bottom of `insights.html`.
- SEO: each page has Open Graph tags, Twitter Card meta, canonical URLs, and `index.html` includes JSON-LD structured data for a Person schema.
- SVG icons are inline (not an icon library).
- The site domain is `emilylewispinnell.com`; the associated business is EVAILA (`evaila.com`).

## Thought Leadership Workflow

### Homepage card rules
- `index.html` shows exactly **6 cards**, newest first
- When adding a new entry, insert at the top and remove the oldest (7th) card
- `insights.html` keeps **all cards** — entries are only ever added, never removed

### Card insertion pattern
Each card is preceded by a comment: `<!-- Article: [Title] -->` (or Podcast, Speaker, etc.)
Use this pattern when inserting new cards so entries are easy to locate.

### Indentation
- `index.html` — 4-space indentation
- `insights.html` — 2-space indentation
Match the existing pattern exactly when inserting cards.

### Badge types & colors
| Type | Badge class |
|------|------------|
| Article | `badge-article` (blue) |
| Podcast | `badge-podcast` (dark red) |
| Speaker | `badge-speaker` (green) |
| Interview | `badge-interview` (purple) |
| Webinar | `badge-webinar` (grey) |

### Sitemap
Update all `<lastmod>` dates to today (YYYY-MM-DD) whenever HTML files are modified.

## Deployment
Cloudflare Pages auto-deploys on every push to `main`. No build step needed — just commit and push.