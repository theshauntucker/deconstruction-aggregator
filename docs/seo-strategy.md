# SEO Strategy & Programmatic Content

## Programmatic SEO Foundation

### generateStaticParams() Architecture
Create static pages at scale using template system:

```
{religion} x {resource_type} combinations
{religion} x {tag} combinations
{religion} x {topic} combinations
```

**Example expansion**:
- Religions: 8 major (Mormonism, JW, Scientology, Islam, Christianity, Hinduism, Buddhism, Judaism)
- Resource types: 5 (books, testimonies, FAQ, BITE analysis, legal docs)
- Tags: 20+ (trauma, childhood, family, identity, career, psychology, law, history)

**Result**: 8 x 5 x 20 = **800+ pages automatically generated** from templates

### Benefits
- Hundreds of long-tail pages with near-zero marginal cost
- SEO flywheel: each new religion section strengthens domain for all others
- Internal linking structure built automatically
- JSON-LD schema auto-generated per page type

---

## JSON-LD Schema Markup (Required)

Implement on every page type to improve search visibility:

### Blog Articles
```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[Religion] Deconstruction: What It Is and How to Recover",
  "image": "og-image.jpg",
  "datePublished": "2025-01-15",
  "author": {
    "@type": "Person",
    "name": "Author Name",
    "credential": "LMFT, Licensed Therapist"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Deconstruction Aggregator",
    "logo": "logo.png"
  }
}
```

### Book Resources
```json
{
  "@context": "https://schema.org",
  "@type": "Book",
  "name": "Book Title",
  "author": "Author Name",
  "isbn": "123-456",
  "url": "link-to-review",
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.5",
    "ratingCount": "250"
  }
}
```

### FAQ Pages
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Is [Religion] a cult?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Answer text with BITE analysis..."
      }
    }
  ]
}
```

### Interactive Tools (BITE Quiz)
```json
{
  "@context": "https://schema.org",
  "@type": "WebApplication",
  "name": "BITE Model Quiz",
  "url": "quiz-url",
  "description": "Interactive quiz to assess cult characteristics",
  "applicationCategory": "EducationalApplication"
}
```

### Breadcrumb Navigation
```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Mormonism",
      "item": "/religions/mormonism"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "Deconstruction Timeline",
      "item": "/religions/mormonism/deconstruction-timeline"
    }
  ]
}
```

---

## High-Volume Keyword Targets

### "Is [X] a Cult?" Pages
- **Combined search volume**: 50K-100K monthly
- **Competition**: Low to medium
- **Example keywords**:
  - "Is Mormonism a cult?" (5K-12K/mo)
  - "Is Jehovah's Witnesses a cult?" (5K-10K/mo)
  - "Is Scientology a cult?" (4K-8K/mo)
  - "Is Islam a cult?" (2K-5K/mo)
  - "Is Christianity a cult?" (2K-4K/mo)
  - "Is Hinduism a cult?" (1K-3K/mo)

**Page Template**: Religion name + "BITE Model Analysis" + user reviews + legal/academic sources + conversion CTAs

### BITE Model Pages
- **"BITE model test"**: 7K-9K monthly searches
- **"Cult checklist"**: 5K-7K monthly searches
- **"BITE model explained"**: 8K-12K monthly searches
- **Competition**: Very low (no good interactive version exists)

### Religious Trauma & Recovery
- **"Religious trauma syndrome"**: 3K-6K/mo
- **"Deconstruction mental health"**: 2K-5K/mo
- **"Recovery from [religion]"**: 1K-3K per variation
- **"Spiritual abuse"**: 4K-8K/mo

### Deconstruction Guides
- **"How to deconstruct your faith"**: 2K-4K/mo
- **"Faith deconstruction guide"**: 1K-3K/mo
- **"What does deconstruction mean?"**: 1K-2K/mo

---

## Launch Article Strategy (First 90 Days)

Publish 5 cornerstone articles targeting high-volume keywords:

### Article 1: "The BITE Model Explained"
- **Target keyword**: "BITE model explained" (8K-15K monthly)
- **Length**: 3,000+ words
- **Content**:
  - Behavior control definition + examples
  - Information control definition + examples
  - Thought control definition + examples
  - Emotion control definition + examples
  - Comparison to other frameworks (DSM, psychological cult definition)
  - Quiz embed
  - 10+ internal links to specific religion pages
- **Publication**: Day 20

### Article 2: "Is Mormonism a Cult? A BITE Model Analysis"
- **Target keyword**: "Is Mormonism a cult?" (5K-12K monthly)
- **Length**: 4,000+ words
- **Content**:
  - Introduction: What is a cult vs. religion
  - BITE analysis per category (10+ examples each)
  - Historical context (1800s-present)
  - Legal cases & court findings
  - Therapist quotes
  - CES Letter link + summary
  - BetterHelp CTA
- **Publication**: Day 25

### Article 3: "Religious Trauma Syndrome: What It Is and How to Heal"
- **Target keyword**: "Religious trauma syndrome" (3K-6K monthly)
- **Length**: 3,500+ words
- **Content**:
  - Definition & psychological basis
  - Symptoms checklist
  - Recovery framework (6 stages)
  - Therapy recommendations + affiliates
  - Meditation/wellness resources
  - Community support links
- **Publication**: Day 30

### Article 4: "The Complete Guide to Faith Deconstruction"
- **Target keyword**: "Faith deconstruction guide" (5K-10K monthly)
- **Length**: 5,000+ words
- **Content**:
  - Definition of deconstruction
  - Stages of faith deconstruction
  - Common challenges & how to overcome
  - Religion-specific guides (links to individual pages)
  - Timeline: typical deconstruction length
  - Therapist directory + affiliate
  - Workbook download CTA
- **Publication**: Day 35

### Article 5: "CES Letter Summary: Everything You Need to Know"
- **Target keyword**: "CES Letter" + branded traffic (2K-5K monthly)
- **Length**: 3,000+ words
- **Content**:
  - What is the CES Letter (history)
  - Full summary of each major criticism
  - LDS responses & rebuttals
  - Critical analysis (fact-checking)
  - Full CES Letter text (CC-licensed, linked)
  - Follow-up resources (BITE analysis, deconstruction guide)
  - Forum discussion link
- **Publication**: Day 40

---

## E-E-A-T (Expertise, Authoritativeness, Trustworthiness)

### Credentialed Contributors
Hire/partner with:
- **Licensed therapists** (LMFT, LPC, LCSW) — write trauma/recovery content
- **Academics** (religious studies PhDs, sociology) — write historical/analytical content
- **Former clergy** — write insider testimony & institutional critique
- **Lawyers** (First Amendment specialists) — write legal analysis content

### Author Bio Examples
```
Dr. Jane Smith, LMFT

Licensed Marriage and Family Therapist in [State]. 
Specializes in religious trauma recovery. 
[5+ years experience] working with religious deconstruction clients.
```

### Byline Requirements
- Full name + credentials below title
- Photo (professional headshot)
- Bio link to author page
- Internal links to all author's other articles

### Trust Signals
- Newsletter signup: "[Author] sends weekly deconstruction resources"
- Social proof: "5,000+ therapists follow our newsletter"
- Expertise: "Written by former [religion] clergy + licensed therapists"

---

## Internal Linking Architecture

### Same-Religion Links
Every [religion] page links to:
- Main [religion] landing page
- Related [religion] topics
- BITE analysis for that religion
- Testimonies from that religion

**Example**: /religions/mormonism/deconstruction-timeline links to:
- /religions/mormonism/ (landing)
- /religions/mormonism/bite-analysis (BITE)
- /resources/mormonism-books (books)
- /resources/mormon-testimonies (stories)

### Cross-Religion Comparison Links
Every religion page links to:
- "Is [X] a cult?" pages for other religions
- BITE Model quiz
- General deconstruction guide
- Therapy/support resources

**Example**: "Is Mormonism a cult?" links to:
- "Is Jehovah's Witnesses a cult?"
- "Is Scientology a cult?"
- BITE Model explained
- Religious Trauma article

### Content Hub Links
Every topical page links to all religions covering that topic:
- Religious trauma → trauma stories across all religions
- BITE analysis → BITE pages for all religions
- Family dynamics → family impact stories across religions

### Strategy
Internal links = SEO flywheel. Each new religion strengthens all others.

---

## Dynamic Sitemap & Robots.txt

### sitemap.ts (Next.js)
```typescript
// Generate sitemap.xml with all programmatic pages
export default async function sitemap() {
  const religions = getReligions();
  const resourceTypes = getResourceTypes();
  
  const pages = [];
  religions.forEach(religion => {
    resourceTypes.forEach(type => {
      pages.push({
        url: `https://site.com/${religion}/${type}`,
        lastModified: new Date(),
        changeFrequency: 'weekly',
        priority: 0.8
      });
    });
  });
  return pages;
}
```

### robots.txt
```
User-agent: *
Allow: /
Disallow: /admin/
Disallow: /api/
Disallow: /*?*utm_* (no tracking params)

Sitemap: https://site.com/sitemap.xml
Crawl-delay: 1
```

---

## Technical SEO Checklist

- [ ] JSON-LD on all page types
- [ ] Dynamic sitemap.ts generating 500+ pages
- [ ] BreadcrumbList on all pages
- [ ] generateMetadata() with unique titles/descriptions
- [ ] ISR (Incremental Static Regeneration) for content pages
- [ ] Core Web Vitals: LCP <2.5s, FID <100ms, CLS <0.1
- [ ] Mobile-first responsive design
- [ ] AMP consideration (skip for now, declining in importance)
- [ ] 301 redirects for moved content
- [ ] Hreflang tags (if international)
- [ ] Image alt text on all images

---

## Keyword Research Tools

- Semrush (free trial covers 10 reports)
- Ahrefs (free trial covers 20 reports)
- Google Keyword Planner (free, Google Ads required)
- AnswerThePublic (free tier shows related searches)
- Ubersuggest (free tier)

**For this project**: Focus on 50K+ combined search volume across "Is X a cult?" variations. That single keyword family = 50% of organic traffic potential.

---

## Content Calendar (90 Days)

| Week | Task | Output |
|------|------|--------|
| 1-2 | Keyword research, site structure | 100 target keywords, IA document |
| 3-4 | Write 5 cornerstone articles | BITE, Mormonism, Trauma, Deconstruction, CES Letter |
| 5-6 | Create "Is X a cult?" template, publish 10 pages | 10 high-volume pages live |
| 7-8 | Build BITE Model quiz | Interactive tool live |
| 9-10 | Internal linking audit, add breadcrumbs | 1000+ internal links, all pages linked |
| 11-12 | JSON-LD audit, Core Web Vitals optimization | All pages scored 90+ Lighthouse |

