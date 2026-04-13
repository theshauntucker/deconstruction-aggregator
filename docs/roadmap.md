# 90-Day Launch Roadmap

## Phase 1: Foundation (Days 1-15)

### Legal & Business Setup
- [ ] Wyoming anonymous LLC formation ($200)
- [ ] EIN application (free)
- [ ] DMCA designated agent registration with US Copyright Office ($6)
- [ ] Private WHOIS registration for domain ($10-15/year)
- [ ] Domain registration ([projectname].com, .org, or .net)
- [ ] Media liability insurance quote (budget: $78/month)
- [ ] Registered agent service (budget: $50-100/year)

### Development Initialization
- [ ] Next.js 15 project with App Router + TypeScript + Tailwind
- [ ] Supabase project creation + authentication setup
- [ ] Database migration setup (flyway or sql migrations folder)
- [ ] /content/ directory structure for markdown resources
- [ ] content.ts parser (read .md files, extract frontmatter)
- [ ] seed-db.ts script to populate initial religion/resource data
- [ ] Supabase Auth setup (email + optional social login)
- [ ] next.config.ts with ISR configuration
- [ ] base layout.tsx with header, footer, navigation

### Repository
- [ ] GitHub/GitLab repo creation
- [ ] .env.example file (no secrets committed)
- [ ] README.md with setup instructions
- [ ] Initial commit

**Target**: Functional dev environment, database schema designed, static assets organized

---

## Phase 2: Core Content & Basic Site (Days 15-30)

### Content Creation
- [ ] Write 150+ resource index.md files (books, testimonies, articles, legal docs)
  - /content/resources/[religion]/[resource-type]/index.md
  - Frontmatter: title, author, link, description, tags, source-license
- [ ] Download & store hostable primary sources locally
  - CES Letter (CC-licensed)
  - Court filings from PACER
  - FBI FOIA documents
  - Royal Commission reports
- [ ] Write religion introduction pages (500 words each)
  - /content/religions/[slug]/index.md
  - Overview, history, key beliefs, deconstruction resources
- [ ] Write site pages
  - /about.md
  - /privacy.md
  - /tos.md
  - /contact.md
  - /dmca-policy.md

### Frontend Development
- [ ] /religions/page.tsx — Grid layout showing all religions
  - Cards with religion name, follower count, resource count
  - Search/filter
  - Link to individual religion landing page
- [ ] /religions/[slug]/page.tsx — Religion landing page
  - Overview text
  - Key statistics (followers, deconstruction resources available)
  - Related resources grid
  - Internal links to "Is X a cult?" page, BITE analysis, testimonies
- [ ] /religions/[slug]/[resource]/page.tsx — Individual resource detail page
  - Title, author, description
  - External link to resource
  - Related resources
  - Breadcrumb navigation
  - JSON-LD article schema
- [ ] ResourceCard.tsx component
  - Reusable card for displaying resources
  - Image, title, description, tags, link
- [ ] JSON-LD generation
  - Article schema for blog posts
  - Book schema for book resources
  - BreadcrumbList for all pages
- [ ] Dynamic sitemap.ts generating pages from database
- [ ] generateMetadata() function for SEO titles/descriptions
- [ ] Programmatic template pages for {religion} x {resource-type}
- [ ] BreadcrumbList component on all pages
- [ ] Deploy to Vercel (auto-deploy on GitHub push)

**Target**: 200+ pages live (religion landing pages + resource detail pages), site functional and navigable

---

## Phase 3: Interactive Tools (Days 30-50)

### BITE Model Quiz
- [ ] /tools/bite-quiz/page.tsx — Quiz page
- [ ] Quiz data structure (questions, scoring, results)
  - 4 categories: Behavior Control, Information Control, Thought Control, Emotion Control
  - 20+ questions per category (80+ total)
  - Scoring system (0-100 scale)
- [ ] Quiz engine logic
  - Answer tracking
  - Score calculation
  - Result interpretation (Low, Moderate, High cult indicators)
  - Radar chart visualization (Chart.js or Recharts)
- [ ] Results page with:
  - Total score + interpretation
  - Per-category breakdown with radar chart
  - "Save Results" button (stores to quiz_results table)
  - Share button with OG image (customized with score)
  - Optional: name your group feature
  - Therapist CTA
  - Related resources (BITE explained, "Is X a cult?" pages)
- [ ] Shareable results URL (e.g., site.com/quiz-results/[id])

### "Is It a Cult?" Programmatic Pages
- [ ] /is-it-a-cult/[slug]/page.tsx — Dynamic pages
  - Programmatic generation for 50+ initial pages:
    - Is Mormonism a cult?
    - Is Jehovah's Witnesses a cult?
    - Is Scientology a cult?
    - [plus 47 more variations]
  - Page structure:
    - Brief intro
    - BITE Model analysis (Behavior, Information, Thought, Emotion with examples)
    - Legal/academic sources cited
    - Therapist quotes
    - User scores (crowdsourced rating of cult indicators, 1-5 scale)
    - FAQPage schema (Google Featured Snippets)
    - Related "Is X a cult?" links
    - BetterHelp CTA
- [ ] User scoring system
  - Allow authenticated users to rate cult indicators
  - Store ratings in Supabase
  - Aggregate scores on page
  - Simple 1-5 scale per BITE category

### Story Submission System
- [ ] /stories/submit/page.tsx — Story submission form
  - Form fields: name (optional), religion, story title, story text, consent checkbox
  - Optional: email (for follow-up interviews)
  - Optional: publish under pseudonym toggle
- [ ] stories_submissions table in Supabase
  - Store submissions with approval status
- [ ] Admin moderation queue
  - /admin/stories page to approve/reject
  - Filters for religion, status, date
- [ ] /stories/[slug]/page.tsx — Published story page
  - Story text
  - Religion tag
  - Share buttons (Twitter, Facebook, email)
  - "More stories from [religion]" section
  - Related resources

**Target**: BITE quiz live, 50+ "Is it a cult?" pages indexed, story submission working

---

## Phase 4: Community Features (Days 50-70)

### Forum System
- [ ] /forum/page.tsx — Forum landing
  - List of categories (Mormonism, JW, Scientology, General Deconstruction, etc.)
  - Category cards showing post count, recent activity
- [ ] /forum/[category]/page.tsx — Category view
  - Threads list with:
    - Title, author, post count, last activity
    - Sort by recent, trending, most replies
  - Search within category
- [ ] /forum/[category]/[thread-slug]/page.tsx — Thread view
  - Original post + all replies in chronological order
  - User avatars, timestamps, reputation
  - Reply form at bottom
  - Upvoting on posts (for sorting)
  - Optional: nested replies
- [ ] /forum/user/[username]/page.tsx — User profile
  - Posts/threads created by user
  - Follower count
  - Join date
  - Reputation score
- [ ] Database structure
  - forum_categories table
  - forum_threads table
  - forum_posts table
  - post_upvotes table
  - user_profiles table (extending Supabase Auth)
- [ ] Supabase Realtime for live updates
  - Live post notifications in thread
  - Live user online status
- [ ] Moderation tools
  - /admin/forum for flagging/deleting spam
  - Auto-flagging for profanity
  - User reputation system

### Newsletter Integration
- [ ] ConvertKit or Beehiiv API integration
- [ ] Newsletter signup form on homepage + footer
- [ ] Lead magnet landing page (/free-deconstruction-guide)
  - Email capture
  - PDF download (workbook)
  - Email confirmation (double opt-in)
- [ ] NewsletterForm.tsx component (reusable)
- [ ] Email sequence automation
  - Welcome email
  - 3 educational emails (BITE, deconstruction guide, therapy info)
  - Re-engagement every 7 days with new content

### Reddit Integration
- [ ] Reddit oEmbed API integration
- [ ] Widget to embed top posts from:
  - r/exmormon
  - r/exjw
  - r/FundieSnark (religious critique)
- [ ] Sidebar widget: "Discussion on Reddit"
- [ ] Link to subreddit communities

**Target**: Forum functional, newsletter integrated, 1K+ email subscribers

---

## Phase 5: Monetization & Launch (Days 70-90)

### Affiliate & Ad Integration
- [ ] Apply for AdSense (use existing Google account)
- [ ] Apply for Amazon Associates
- [ ] Sign up for BetterHelp (Impact Radius)
- [ ] Sign up for Talkspace (FlexOffers)
- [ ] Sign up for Online-Therapy.com (50% commission)
- [ ] Ko-fi button integration

### Ad Zones
- [ ] Header ad unit (leaderboard, 728x90)
- [ ] Sidebar ad units (300x250 medium rectangle)
- [ ] In-content ad units (300x250 inside text)
- [ ] Footer ad unit
- [ ] Ad network rotation (AdSense primary, fallback to backup)
- [ ] Ad.txt file for supply-side revenue optimization

### Affiliate Component System
- [ ] AffiliateLink.tsx component
  - Wraps all therapy/book links
  - Adds FTC disclosure on hover
  - Tracks clicks (optional analytics)
  - Example: <AffiliateLink href="..." source="BetterHelp" text="Find a therapist" />
- [ ] TherapyCallout.tsx component
  - Displays on therapy/mental health pages
  - "Consider talking to a therapist" with BetterHelp + Talkspace links
  - Optional: match religion (e.g., ex-Mormon therapists)
- [ ] DonationWidget.tsx component
  - Ko-fi embed
  - "Support our work" messaging

### Content & SEO Final Push
- [ ] 5 cornerstone blog articles (published over 3 weeks)
  1. "The BITE Model Explained" (8K-15K search volume)
  2. "Is Mormonism a Cult?" (5K-12K search volume)
  3. "Religious Trauma Syndrome" (3K-6K search volume)
  4. "Complete Guide to Faith Deconstruction" (5K-10K search volume)
  5. "CES Letter Summary" (2K-5K branded volume)
- [ ] Internal linking audit (link every page to 5-10 related pages)
- [ ] robots.txt setup
- [ ] Search Console verification + submit sitemap
- [ ] Google Analytics 4 setup + event tracking
- [ ] Core Web Vitals optimization
  - LCP < 2.5s (image optimization, code splitting)
  - FID < 100ms (avoid long JS tasks)
  - CLS < 0.1 (avoid layout shifts)
- [ ] Lighthouse audit (goal: 90+ on all pages)

### Insurance & Legal
- [ ] Media liability E&O insurance policy purchased ($78/month)
- [ ] All legal pages live (TOS, Privacy, DMCA, Disclaimer, Cookie consent)
- [ ] GDPR/CCPA compliance verified

### Launch Checklist
- [ ] All 5 cornerstone articles published
- [ ] Forum moderation rules posted
- [ ] Community guidelines published
- [ ] Admin contact & moderation process documented
- [ ] Backup strategy (Supabase backups, GitHub, Cloud storage)
- [ ] Error monitoring (Sentry) configured
- [ ] Email support address set up
- [ ] Social media accounts created (Twitter, TikTok, Instagram)
- [ ] First email sequence queued
- [ ] Press release drafted (optional)
- [ ] Beta user outreach (subreddits, newsletters, Twitter)

**Target**: Site fully monetized, 50+ articles published, 2K-5K organic monthly pageviews, 500+ email subscribers

---

## Post-Launch Roadmap (Months 4-6)

### 100 Days to 10K Pageviews
- [ ] Publish 20+ additional articles (one every 2 days)
- [ ] Expand "Is X a cult?" pages to 50+ variations
- [ ] Create video content for YouTube (embed on site)
- [ ] Guest posts on related blogs (Religious Trauma, Deconstruction, Psychology)
- [ ] Twitter/TikTok daily content (stories, BITE tips, resources)
- [ ] Reddit engagement (answer questions in r/exmormon, r/exjw, etc. — link moderately)

### Monetization Milestones
- [ ] 10K monthly pageviews: Apply for Monumetric ($8-15 RPM)
- [ ] 1,000+ monthly therapy affiliate referrals
- [ ] 500+ paid newsletter subscribers on Substack ($5/month)
- [ ] 5+ therapist sponsorships ($100-300/month each)
- [ ] First digital product sold (deconstruction workbook)

### Community & Engagement
- [ ] 100+ forum threads created
- [ ] Host first live Q&A (YouTube/Zoom with therapist)
- [ ] Launch Patreon ($3/$10/$25 tiers)
- [ ] Podcast guest appearances (3-5 appearances)

---

## 6-Month Milestones (End of Phase 6)

- 25K+ organic monthly pageviews
- 200+ published articles
- 100+ "Is X a cult?" pages
- 2K+ forum members
- 1K+ paid newsletter subscribers
- 5K+ therapist referrals (cumulative)
- **Revenue**: $2,000-4,000/month
- **Eligible for**: Raptive (25K PV threshold)

---

## 12-Month Vision

- 100K+ organic monthly pageviews
- 300+ published articles
- 200+ "Is X a cult?" pages
- 10K+ forum members
- 5K+ paid newsletter subscribers
- 20K+ therapist referrals (cumulative)
- **Revenue**: $8,000-12,000/month
- **Next step**: Consider 501(c)(3) conversion or acquisition offers

---

## Key Dates & Deadlines

| Date | Milestone | Deliverable |
|------|-----------|-------------|
| Day 1 | Business formation | Wyoming LLC active |
| Day 15 | Dev environment ready | Deployed skeleton site |
| Day 30 | Core content complete | 200+ resource pages live |
| Day 50 | Interactive tools | BITE quiz, "Is X a cult?" pages |
| Day 70 | Community live | Forum, newsletter, stories |
| Day 90 | LAUNCH | Full monetization, 5 cornerstone articles, 2K-5K PV |
| Month 4 | Scale | 10K monthly pageviews, apply Monumetric |
| Month 6 | Growth phase | 25K monthly pageviews, apply Raptive |
| Month 12 | Maturity | 100K+ monthly pageviews, $8K+/mo revenue |

---

## Risk Mitigation Schedule

| Week | Risk | Mitigation |
|------|------|-----------|
| 1-2 | Litigation discovery | Finalize Wyoming LLC anonymous structure |
| 3 | Google YMYL penalty | Hire first credentialed contributor |
| 6 | Ad network rejection | Prepare "educational/wellness" framing |
| 8 | Forum spam/trolls | Deploy moderation bot + human mods |
| 12 | Copyright DMCA claim | Have media lawyer on retainer |

