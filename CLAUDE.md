# Deconstruction Aggregator — Claude Code Project Instructions

## Project Overview
Cross-religion deconstruction resource aggregator. The first platform to aggregate deconstruction resources across ALL major religions with interactive tools, community features, and programmatic SEO.

**Target**: 50K–100K monthly pageviews within 18–24 months, $5,000–6,500/month revenue.

## Tech Stack
- **Framework**: Next.js 15 (App Router, TypeScript, Tailwind CSS)
- **Database**: Supabase (PostgreSQL + Auth + Realtime + RLS)
- **Hosting**: Vercel
- **Content**: Markdown with YAML frontmatter (source of truth in `/content/`)
- **Charts**: Recharts or D3 for BITE Model radar charts
- **Email**: ConvertKit or Beehiiv API
- **Auth**: Supabase Auth (email/password + Google OAuth)

## Project Structure
```
deconstruction-aggregator/
├── CLAUDE.md                          # THIS FILE — project instructions
├── docs/                              # Strategy docs and reference material
│   ├── blueprint.md                   # Full project blueprint
│   ├── legal-checklist.md             # Legal structure, risks, insurance
│   ├── monetization-strategy.md       # Revenue stack and ad network info
│   ├── seo-strategy.md               # Programmatic SEO plan
│   ├── roadmap.md                     # 90-day launch roadmap with tasks
│   └── competitive-analysis.md        # Competitor landscape
├── content/                           # Markdown content (SOURCE OF TRUTH)
│   ├── resources/                     # 150+ resource files with frontmatter
│   │   ├── mormonism/                 # 30 resources
│   │   ├── christianity/             # 28 resources
│   │   ├── jehovahs-witnesses/       # 18 resources
│   │   ├── scientology/              # 20 resources
│   │   ├── islam/                    # 16 resources
│   │   ├── judaism/                  # 11 resources
│   │   ├── buddhism/                 # Buddhism-specific
│   │   ├── hinduism/                 # Hinduism-specific
│   │   ├── cults/                    # Cults and high-control groups
│   │   └── general/                  # Cross-religion and general resources
│   ├── primary-sources/              # Hostable documents + license notes
│   │   └── README.md                 # Download instructions and licenses
│   ├── pages/                        # Static site pages
│   │   ├── about.md
│   │   ├── disclaimer.md
│   │   ├── dmca-policy.md
│   │   ├── privacy-policy.md
│   │   ├── terms-of-service.md
│   │   └── ftc-disclosure.md
│   └── blog/                         # Launch articles
│       ├── bite-model-explained.md
│       ├── is-mormonism-a-cult.md
│       ├── religious-trauma-syndrome.md
│       ├── complete-guide-faith-deconstruction.md
│       └── ces-letter-summary.md
├── database/
│   └── schema.sql                    # Full Supabase migration SQL
├── config/
│   ├── bite-model-questions.json     # BITE Model quiz data (4 categories, ~80 questions)
│   ├── is-it-a-cult-groups.json      # 50+ groups for programmatic "Is X a cult?" pages
│   ├── religions.json                # Religion metadata (name, slug, icon, description)
│   └── affiliate-links.json          # Affiliate program details and links
└── src/                              # Next.js source (to be scaffolded)
    └── README.md                     # Build instructions
```

## Content Frontmatter Schema
Every resource file in `/content/resources/{religion}/` uses this frontmatter:
```yaml
---
title: "Resource Name"
slug: "resource-slug"
type: "document|book|podcast|website|documentary|subreddit|organization|youtube|tv-series|court-document|gov-document|academic"
url: "https://..."
author: "Author Name"
datePublished: "YYYY-MM-DD"  # or "YYYY" if only year known
religion: "mormonism|christianity|jehovahs-witnesses|scientology|islam|judaism|buddhism|hinduism|cults|general"
license: "cc-by-nc-nd|cc-by-nc|public-domain|standard-copyright|reddit-tos|youtube-standard|informal-free"
hostable: true|false
priority: 5|4|3|2|1  # 5=essential day-one, 1=nice-to-have
tags: ["tag1", "tag2"]
summary: "One-line summary"
difficulty: "beginner|intermediate|advanced"
format: "free-online|paid-book|streaming|podcast-app|reddit|youtube"
affiliateEligible: false  # true for books (Amazon Associates)
---

Extended description and editorial commentary in Markdown.
```

## Key Build Tasks (in order)
1. `npm create next-app@latest` with App Router + TypeScript + Tailwind
2. Set up Supabase project, run `database/schema.sql`
3. Build content parser (`src/lib/content.ts`) to read frontmatter from `/content/`
4. Build `seed-db.ts` script to sync content → Supabase
5. Build religion index page, religion landing pages, individual resource pages
6. Build BITE Model interactive quiz (use `config/bite-model-questions.json`)
7. Build "Is [X] a cult?" programmatic pages (use `config/is-it-a-cult-groups.json`)
8. Build story submission system
9. Build forum (Supabase Realtime)
10. Integrate monetization (ad zones, affiliate links, donation buttons)
11. SEO: JSON-LD, dynamic sitemap, meta tags, programmatic template pages
12. Deploy to Vercel

## Legal Constraints (IMPORTANT)
- Only 7 categories of content can be hosted directly (see `docs/legal-checklist.md`)
- Everything else is LINK + SUMMARIZE + FAIR USE EXCERPT only
- Never reproduce full chapters of copyrighted books
- Always add substantial transformative commentary to quoted material
- Include FTC disclosure on every page with affiliate links
- Scientology content requires extra care (see legal docs)
- BITE Model is trademarked by Steven Hassan — always include attribution

## Monetization Integration Points
- Ad placement zones: header, sidebar, in-content (3 zones per page)
- Therapy affiliate CTAs on resource pages (BetterHelp, Talkspace, Online-Therapy.com)
- Amazon book affiliate links on all book resources
- Donation widget in footer and sidebar
- Newsletter signup in footer + dedicated /newsletter page

## SEO Requirements
- Every dynamic route needs `generateMetadata()` 
- JSON-LD on every page (Book, Article, FAQPage, WebApplication, BreadcrumbList)
- Dynamic `sitemap.ts` covering all routes
- Programmatic pages for `{religion} × {resource_type}` and `{religion} × {tag}`
- Internal linking between related resources and same-religion content
- ISR (Incremental Static Regeneration) for resource pages
