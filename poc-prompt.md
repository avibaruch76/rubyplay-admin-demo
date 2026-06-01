# RubyPlay Admin POC — Build Brief

**Use this same prompt for both Base44 and Lovable** so the two POCs are directly comparable.

You're building a small but representative slice of an admin tool for **RubyPlay Group**, a B2B slot game provider with 6 brand studios and 750+ games. The goal is **not** to build the full app — it's to test whether your platform can handle the specific patterns this project needs.

---

## What to build (7 features only)

### 1. Games list page
- Table of 10 sample games (see `poc-data.json` → `games` array)
- Columns: Thumbnail · Game name · Studio · Series · Status pill · Release date · RTP · Volatility · Last edit · ⋯ menu
- Filter chips at top: Studio · Status · Theme · Volatility (these must actually filter the table — clicking each opens a dropdown of options)
- A search box that filters by game name
- Status pills should be color-coded: Live (green) · Scheduled (blue) · In review (pink) · Draft (amber) · Retired (gray)

### 2. Game editor form (the main workhorse)
Open by clicking any row in the games list. Use **tabbed layout**:

- **Tab 1 — Basic info**: Title · Studio (dropdown) · Game ID · URL slug · Release date · Game Series (dropdown) · Theme · Game Tag (Upcoming/Live/Bespoke/SE) · Tagline (1-line, max 80 chars) · Description (rich text, first paragraph bold) · Max Win · Line configuration · Trailer YouTube URL
- **Tab 2 — Media**: 6 image upload slots with EXACT pixel dimensions enforced:
  - Game logo (PNG transparent)
  - Hero landscape **1920×785** (desktop, no logo)
  - Banner **1280×523** (home page, with logo)
  - Hero portrait **1000×1406** (mobile, no logo)
  - Poster **700×984** (mobile, with logo)
  - Slider thumbnail **456×360**
  - Plus: Screenshots gallery (multiple uploads, must be 1920×1080)
- **Tab 3 — Stats**: RTP % · Volatility (1–5 step slider with labels: Low → Low-Med → Medium → Med-High → High) · Hit Frequency · Max Win · Reels × Rows · Lines/Ways · Buy Feature (Yes/No toggle) · Bonus Buy Cost
- **Tab 4 — Features**: Add multiple feature cards, each with an image + name + description. Drag to reorder.
- **Tab 5 — Demo**: Play demo URL · Operator integration URL · Demo aspect ratio dropdown · A "Test demo" iframe preview
- **Tab 6 — Marketing**: Featured placement (group homepage, studio home, catalog position) · Promo banner copy · Press release URL · Art Media Pack ZIP · SEO meta title + description + OG image
- **Tab 7 — Translations**: Table of 5 languages (English, Spanish, German, Portuguese, Italian) with editable tagline + description per language. Missing translations highlighted amber with "Auto-translate" button.
- **Tab 8 — Operator**: PDF docs (math sheet, RGS integration guide, GLI cert) · Approved jurisdictions multi-select (15 options from `poc-data.json` → `jurisdictions`)

Top bar of the editor must have: **Preview button**, **Save draft**, **Save & publish**, ⋯ more menu.

### 3. Studio detail page
- Click any studio name in the games list → opens a Studio detail page
- Show the studio's logo, banner, brand colors, game count
- Tabs inside: **Overview** (about + brand assets + colors) · **Homepage content** (hero title/subtitle, curated games carousel pick, Studio Director name+title+quote+photo, About body, Studio Art Media Pack ZIP) · **Games** (filtered to this studio) · **Series** · **Team** · **Settings**

### 4. Users + Roles screen
- Top: tabs for **Users** · **Roles** · **Pending invites** · **Activity audit**
- Users tab: table of 5 users from `poc-data.json` → `users`, with Role pill + Studio scope + Last active
- Roles tab:
  - List of 6 roles from `poc-data.json` → `roles`
  - Click a role → opens a **permission matrix modal** with ~30 individual Yes/No toggles grouped into 6 categories (Catalog · Studios/Series/Themes · Content · Public site · Workflow · Admin)
  - HQ Admin is built-in and read-only (all toggles locked YES)
  - Counter at top shows "N / 30 permissions · X users"
  - Toggles must reflect the actual permissions per role (don't hardcode to one role)
- Invite user modal: email + role dropdown + studio scope dropdown

### 5. Public REST or GraphQL API ⭐ CRITICAL
Expose API endpoints so an external public website (rubyplay.com) can read this data:

- `GET /api/games` — list with filters: `?studio=koala&status=live`
- `GET /api/games/:id` — single game with all fields
- `GET /api/studios` — list of studios
- `GET /api/studios/:slug` — single studio + its games
- `GET /api/series` — list of series
- `GET /api/themes` — list of themes
- Auth via API key or OAuth token (document how)
- CORS enabled for the public-site domain
- Return JSON

**If your platform cannot expose a public API for external consumers, mark this POC as failed — the data is trapped otherwise.**

### 6. File upload + storage
- Image uploads in the Game editor must actually store the file
- Uploaded files must be retrievable via the API (e.g. `game.hero_image_url`)
- Document where files are stored (S3-compatible? Your platform's storage?) and any size limits
- Confirm that all 6 image variants per game can co-exist (768 games × 6 images = ~4,500 images at scale)

### 7. Protected routes
- Login screen before accessing the admin
- A logged-out user accessing any URL redirects to login
- After login, redirect back to where they were trying to go
- Show the logged-in user's name + avatar in the sidebar bottom

---

## Data to use

Use `poc-data.json` in this repo as the seed. It contains:
- **6 studios** (4 active + 2 placeholder)
- **10 games** with full real metadata from the operational portfolio
- **9 series**, 13 themes, 15 jurisdictions
- **5 users**, **6 roles** with permission definitions
- 5 supported languages

**Don't make up data — use these exact records.** Both POCs starting identical is what makes them comparable.

---

## Visual reference

A clickable HTML demo of the full design is at:

**https://rubyplay-admin-demo.onrender.com** (or the local `index.html` in this repo)

Look at:
- The sidebar layout (Catalog / Content / Public site / Workflow / Admin sections)
- The Games table with filter chips
- The Game editor with 8 tabs (click any game row)
- The Studio detail page (click any studio card)
- The Roles permission matrix (Users & roles → Roles tab → click HQ Admin or Studio Lead)
- The brand colors per studio

You don't have to match the demo pixel-perfect — but the **information architecture and UX patterns** should be similar.

---

## Brand & styling

- **Primary brand color**: `#ef4444` (RubyPlay red)
- **Accent**: `#0a0a0a` (black) and `#fbbf24` (gold)
- **Studio brand colors**: see `poc-data.json` → each studio has `brand_color_primary/secondary/accent`
- **Font**: Inter, system-ui sans-serif
- **Style**: Clean, modern, B2B SaaS feel (not consumer/gambling). Lots of whitespace, clear typography, restrained color use.

---

## What's explicitly OUT of scope for this POC

Don't build these — they're for the full v1 later:
- The public-facing rubyplay.com website (we'll handle that separately)
- News/blog system
- Group homepage block composer
- Static pages editor (About/Privacy/Contact)
- Footer editor
- Monday.com sync (just expose API; integration comes later)
- Translation review modal
- Release calendar with drag-drop
- Bulk import from folder

**Stick to the 7 features above only.** Adding more bloats the POC and makes comparison harder.

---

## Acceptance criteria (the grading rubric)

After your POC is built, your team will be scored 1–5 on each:

| Criterion | Weight | What "good" looks like |
|---|---|---|
| **Public API access** | ⭐⭐⭐⭐⭐ | All 6 endpoints return JSON, auth works, CORS configured |
| Game editor field completeness | ⭐⭐⭐⭐ | All 8 tabs have the listed fields |
| Match to the demo's look/feel | ⭐⭐⭐⭐ | Sidebar layout, tabs, filter chips, status pills, brand colors |
| Image upload with exact dimensions | ⭐⭐⭐⭐ | All 6 specs enforced, files retrievable via API |
| Permission matrix granularity | ⭐⭐⭐⭐ | 30+ toggles per role, matrix actually applies to user behavior |
| Studio scoping (multi-tenant) | ⭐⭐⭐⭐ | Studio Lead can only see/edit own studio's games |
| Time-to-built (hours from prompt to working) | ⭐⭐⭐ | Faster = more iteration cycles in production |
| Code/data export options | ⭐⭐⭐⭐ | Can you export your data and self-host if you ever leave? |
| Pricing tier for the above | ⭐⭐⭐ | What plan unlocks the API and permission features? |

---

## Deliverables from each POC

1. A **working URL** where the POC can be clicked through
2. A **brief writeup** answering:
   - Which acceptance criteria did you fully meet? Partially? Miss?
   - How many hours did the POC take?
   - What was easy on this platform? What fought you?
   - What pricing tier would be needed for the production build?
   - Sample API request + response (curl command + JSON)
3. **Login credentials** for the demo so the other side can click through

Once both POCs are done, we score them side-by-side and pick a winner.

---

## Tips per platform

### For Lovable
- Start with: "Build a multi-tenant admin for a slot game company. See attached poc-prompt.md and poc-data.json."
- Tech stack: prefer Next.js 14 + Supabase + Tailwind + shadcn/ui (Lovable defaults work well here)
- For the permission matrix: ask Lovable to use Supabase Row-Level Security
- For the API: Supabase auto-generates a REST API + GraphQL — easy win
- Iterate via chat: "Add the Media tab to the Game editor", "Color the studio pills with brand colors", etc.

### For Base44
- Their onboarding will set up the data model — paste in the schema from `poc-data.json`
- Ask explicitly: "I need a public REST API where I can curl `/api/games` from outside the platform and get JSON. Is this on the plan you're quoting?"
- For the permission matrix: their built-in roles may not support 30+ granular permissions — verify with their team
- For exact image dimensions: ask if their file storage supports enforcing exact pixel sizes on upload

---

## Questions to flag during the POC

For whichever platform, write down anything you have to **work around** rather than do natively. Examples:
- "Couldn't make Volatility a 1-5 slider — had to use a text dropdown"
- "Image upload doesn't validate dimensions — would need a custom validator"
- "Studio Lead role couldn't be scoped to a single studio — workaround uses tags"

These are the items that'll cost real engineering time later. Tracking them now reveals the true cost-of-ownership.

---

**Good luck. Same prompt + same data + same scope = a fair comparison.**
