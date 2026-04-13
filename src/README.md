# Deconstruction Aggregator — Development Setup

## Quick Start

### 1. Initialize Next.js Project

```bash
npx create-next-app@latest . --typescript --tailwind --app --src-dir
```

When prompted:
- TypeScript: **Yes**
- ESLint: **Yes**
- Tailwind CSS: **Yes**
- `src/` directory: **Yes**
- App Router: **Yes**
- Import alias: **Yes** (use `@/`)
- Turbopack: **Yes** (optional, for faster builds)

### 2. Install Dependencies

```bash
npm install @supabase/supabase-js gray-matter next-mdx-remote recharts
```

**Package Purposes:**
- `@supabase/supabase-js` — Database and authentication
- `gray-matter` — Parse frontmatter from Markdown files
- `next-mdx-remote` — Render MDX content dynamically
- `recharts` — Interactive charts for quiz results and statistics

### 3. Environment Setup

Create `.env.local`:

```env
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-service-key
```

Get these from your Supabase project dashboard.

### 4. Database Setup

1. Create new Supabase project
2. Run migration from `../database/schema.sql` in Supabase SQL editor
3. Seed religions and resource types (migrations include seed data)
4. Set up authentication (enable email/password or OAuth)

## Project Structure

```
src/
├── app/
│   ├── layout.tsx          # Root layout
│   ├── page.tsx            # Homepage
│   ├── (routes)/           # Route groups
│   │   ├── about/
│   │   ├── resources/
│   │   ├── quiz/
│   │   ├── forum/
│   │   ├── stories/
│   │   └── blog/
│   └── api/                # API routes
│       └── [routes]/
├── components/             # Reusable components
├── lib/                    # Utilities
│   ├── supabase.ts        # Supabase client
│   ├── mdx.ts             # MDX parsing
│   └── constants.ts
├── styles/
│   └── globals.css
└── types/                 # TypeScript types
    └── index.ts
config/                    # Config files (religions, BITE questions, etc.)
└── [JSON files]
content/                   # Markdown content
├── pages/
└── blog/
```

## Key Features

### 1. Blog & Pages
- Markdown files in `content/` with frontmatter
- `gray-matter` parses metadata (title, date, tags)
- `next-mdx-remote` renders as HTML
- Dynamic routes for individual posts

### 2. Quiz System
- BITE Model quiz with 80 questions across 4 categories
- Scoring logic based on `config/bite-model-questions.json`
- Results stored in `quiz_results` table (supports anonymous)
- Share results via unique token

### 3. Resources Database
- Religion-specific resource aggregation
- Filtering by type, difficulty, and tags
- Full-text search via PostgreSQL tsvector
- Affiliate link management

### 4. Forum
- Category-based threaded discussions
- Authentication required to post
- RLS policies enforce row-level security
- Moderation endpoints

### 5. User Accounts
- Supabase Auth integration
- User profiles with privacy controls
- Voluntary submission of recovery stories
- Subscriber-only features

## Development Workflow

### Run Dev Server

```bash
npm run dev
```

Visit `http://localhost:3000`

### Build for Production

```bash
npm run build
npm start
```

### Code Quality

```bash
npm run lint
```

## Deployment

Deploy to Vercel (recommended):

```bash
npm install -g vercel
vercel
```

Set environment variables in Vercel dashboard matching `.env.local`.

## Key Technologies

| Layer | Technology |
|-------|-----------|
| **Frontend** | Next.js 14+, React, TypeScript, Tailwind CSS |
| **Backend** | Supabase (PostgreSQL), Node.js API routes |
| **Content** | Markdown + Frontmatter, MDX rendering |
| **Data** | PostgreSQL, RLS policies, tsvector full-text search |
| **Auth** | Supabase Auth (email, OAuth) |
| **Hosting** | Vercel (frontend), Supabase (backend) |

## API Routes Structure

```
/api/
├── resources/          # GET/POST resources
├── quiz/
│   └── results/       # POST quiz results, GET by token
├── forum/
│   ├── threads/
│   ├── posts/
│   └── categories/
├── stories/           # User testimonies
├── auth/              # Authentication endpoints
└── newsletter/        # Email subscription
```

## Database Notes

- All PKs are UUIDs via `uuid_generate_v4()`
- RLS enabled for user-generated content
- `updated_at` trigger auto-updates on table modifications
- Foreign keys enforce referential integrity
- Indexes on frequently-queried columns (slug, published status, tags)

## Content Management

### Adding Blog Posts

1. Create `.md` file in `content/blog/`
2. Add frontmatter:
   ```markdown
   ---
   title: "Post Title"
   slug: post-slug
   date: 2026-04-12
   tags: [tag1, tag2]
   ---
   ```
3. Write content in Markdown
4. File is auto-discovered at `/blog/post-slug`

### Adding Pages

1. Create `.md` file in `content/pages/`
2. Add frontmatter with slug
3. Server-render via API route or getStaticProps

### Updating Configs

Edit JSON files in `config/`:
- `religions.json` — Add/edit religions and colors
- `bite-model-questions.json` — Modify quiz
- `is-it-a-cult-groups.json` — Update group list
- `affiliate-links.json` — Manage affiliate programs

## Troubleshooting

### Supabase Connection Issues
- Verify `NEXT_PUBLIC_SUPABASE_URL` and `NEXT_PUBLIC_SUPABASE_ANON_KEY`
- Check CORS settings in Supabase dashboard
- Ensure RLS policies allow your role

### MDX Rendering Issues
- Verify frontmatter syntax (YAML)
- Check for unsupported Markdown syntax
- Use custom components for complex layouts

### Quiz Results Not Saving
- Check user authentication status
- Verify `quiz_results` table RLS policy allows inserts
- Check database for constraint violations

## Next Steps

See `CLAUDE.md` in project root for full task list and architecture decisions.

---

**Last Updated:** April 12, 2026
