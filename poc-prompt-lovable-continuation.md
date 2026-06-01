# Lovable Continuation Prompt — Bring POC to Full Demo Parity

Paste this into the Lovable chat for project `8c00734f-735f-4f6d-a82e-985dfc6a5311`.

You already built milestone 1 (foundation + 4 screen shells + REST API). This prompt brings it to full feature parity with the HTML reference demo at **https://rubyplay-admin-demo.onrender.com**.

---

## Continuation prompt to paste

```
Build out the remaining features to match the HTML reference demo at https://rubyplay-admin-demo.onrender.com.

Reference materials (re-read these — they have everything):
- Full spec: https://raw.githubusercontent.com/avibaruch76/rubyplay-admin-demo/main/poc-prompt.md
- Seed data (10 games, 6 studios, 6 roles, 5 users): https://raw.githubusercontent.com/avibaruch76/rubyplay-admin-demo/main/poc-data.json
- HTML demo (click through it for visual + UX reference): https://rubyplay-admin-demo.onrender.com

The HTML demo is the source of truth for UX. Don't redesign — replicate the patterns shown there.

Build in this priority order. Each phase ends with something testable.

PHASE 2: Complete the Game editor (highest priority — the workhorse screen)

Each tab in the game editor must be fully built with the fields from poc-prompt.md. When a user clicks a game row, the editor MUST load THAT game's data — not hardcoded defaults. Use the game's ID to fetch from Supabase.

1. Basic info tab — Title, Studio (dropdown), Game ID, URL slug, Release date, Series (dropdown), Theme, Tag (Upcoming/Live/Bespoke/SE), Tagline (max 80 chars), Description (rich text with bold first paragraph), Max Win, Line configuration, Trailer YouTube URL.

2. Media tab — 6 image upload slots with EXACT dimension enforcement on upload (reject if wrong size, or auto-crop to fit):
   - Game logo (PNG transparent, any size)
   - Hero landscape 1920×785 (no logo)
   - Banner 1280×523 (with logo, home page)
   - Hero portrait 1000×1406 (mobile, no logo)
   - Poster 700×984 (mobile, with logo)
   - Slider 456×360
   - Plus a screenshots gallery (multiple 1920×1080 uploads)
   
   Use Supabase Storage. Each game has a folder. Files retrievable via the API as game.hero_image_url, etc.

3. Stats tab — RTP %, Hit Frequency, Volatility as a 1-5 step slider with labels (Low → Low-Med → Medium → Med-High → High), Max Win, Reels × Rows, Lines/Ways, Buy Feature Yes/No toggle, BF Max Win Multiplier.

4. Features tab — Multiple feature cards. Each has image + name + description. Drag-to-reorder. "+ Add feature" button. Each feature image picked from the screenshots already uploaded for that game.

5. Demo tab — Play demo URL, Operator integration URL, Demo aspect ratio dropdown (16:9/9:16/4:3), embedded iframe preview that loads the demo URL when clicked. "Validate URL" button that does a HEAD request and shows "200 OK · 142ms" or error.

6. Marketing tab — 3 placement dropdowns (Group homepage placement / Studio homepage placement / Catalog position), Promo banner copy, Press release URL, Art Media Pack ZIP upload, SEO fields (meta title, meta description, OG image).

7. Translations tab — Table with 5 rows (English, Spanish, German, Portuguese, Italian). Each row has editable tagline + description for that language. Missing translations highlighted amber. "Auto-translate" button calls a placeholder function (later wired to DeepL).

8. Operator tab — Three PDF upload rows (Math sheet, RGS integration guide, GLI certificate) with Download/Replace buttons. Multi-select for "Approved jurisdictions" — 15 options from poc-data.json (MGA Malta, Curacao, Netherlands, Colombia, Buenos Aires, Romania, Italy, Ontario, South Africa, Spain, Georgia, Brazil, Portugal, Peru, US-NJ).

Editor header: Game name + status pill + tag pill + meta line (studio · series · Game ID · release date · last edited). Top right: Preview, Save draft, Save & publish, ⋯ more menu.

PHASE 3: Studio detail page (per-studio brand theming)

Click any studio card → opens its detail page. The page should adopt the studio's brand_color_primary as the accent. Tabs:

1. Overview — About form (name, slug, founded, HQ, website, email, tagline, long description), Brand assets (logo, banner, mascot/character art uploads), Brand colors (3 color pickers: primary, secondary, accent), right rail with Recent activity feed + Catalog snapshot + Top jurisdictions.

2. Homepage content — Hero title + subtitle, CTA button text + destination, Curated games carousel (drag-reorder up to 6 games picked from this studio's catalog), About body, Studio Director section (name, title, portrait, quote), Studio Art Media Pack ZIP.

3. Games — Filtered table of just this studio's games (re-use the main Games filter component, pre-filtered).

4. Series — List of series owned by this studio with "+ New series" button.

5. Team — List of users scoped to this studio with their roles + last active + "+ Invite to studio" button.

6. Settings — Defaults for new games in this studio (default tag, default supported languages, default approved jurisdictions), Public visibility toggles (Show on public studios page?, Accept operator inquiries?), Danger zone (Archive studio).

PHASE 4: Game Series + Game Themes (separate top-level pages)

Two new sidebar items under Catalog:

1. Game Series page — List of 9 series from poc-data.json. Each row shows series logo + name + studio + game count. "+ Add new Game Series" button. Click a series row → jumps to the Games page pre-filtered to that series (add a Series filter chip to the Games filter bar).

2. Game Themes page — Grid of 13 themes (Classical Slot, Gems, Egypt/Ra, Sports/Football, Volcano, Chinese/Monkey, etc.). Each card shows theme name + game count. Click a theme → jumps to Games page filtered by that theme.

Add Series filter to the Games page filter bar (alongside Studio, Status, Mechanic, Theme, Volatility, Tag).

PHASE 5: Releases calendar (drag-drop scheduling)

Sidebar item under Catalog. Month-view calendar where each release date shows the scheduled game(s). Click a day → opens a "Schedule release" modal (game dropdown + date + "send press kit on release?" toggle). Click a release event → opens the editor for that game. Drag a release to a different day → updates release_date in the database. Legend showing Scheduled / Draft / Live colors.

PHASE 6: Media library

Sidebar item under Content. Grid of all uploaded assets (game thumbnails, banners, screenshots, trailers, math sheets). Each tile shows filename + type + dimensions + size. Filter chips: studio, type, "unused assets only". Click a tile → opens an Asset detail modal with full preview + metadata (file, type, dimensions, size compressed-from, used in [game name], uploaded by/when) and Delete/Download/Replace buttons.

PHASE 7: Translations hub

Sidebar item under Content. Card showing "Coverage by language" — table of 5 languages with games-covered count, completeness bar, Review button. Click "Review" for any language → opens a Translation Review modal listing all games missing that translation. Each game card shows English original (read-only) + target-language input fields with "✨ Auto-translate" button per game. "✨ Auto-translate all missing" bulk button at the top.

PHASE 8: News & Press

Sidebar item under Content. Table of news posts with title + scope (Group / per-studio) + status pill + published date + author. "+ New post" button opens a modal with: title, slug, scope (Group / per-studio dropdown), publish date, hero image upload, excerpt, body (rich text editor with B/I/U/H1-H3/Quote/List/Link/Image/Block buttons), tags, "Featured on homepage" toggle. Save draft / Publish buttons.

PHASE 9: Public Site section (new sidebar section)

This is the biggest. Add a "Public site" sidebar section with these items:

1. Group homepage — Block-based composer. 7 default blocks: Hero, Our Brands (studio cards), Featured Games carousel, RubyPlay News (auto-feed), About, Art Media Pack CTA, Our Partners (hidden by default). Each block has a drag handle, visibility toggle, and Edit button that opens a focused edit modal for that block (Hero: title/text/CTA; Featured Games: pick games to feature; Our Brands: reorder studios). "+ Add a block" picker with Text+Image, CTA Banner, Testimonials, Partners, Custom HTML options. Right rail: live mini-preview + page settings (last published, unpublished changes count, URL).

2. Pages — Sitemap of every public page across the site:
   - Group section: Home (composed), About Us (static), Our Partners (static), News index (auto-feed), Contact (static + form), Art Media Pack (static), Privacy Policy (static)
   - One section per studio (Ruby Play, Koala Games, Mad Hat, Spincraft, Firerose, X Slots): Home (composed) · Games index (auto) · About (static) · Contact (static + form)
   - Auto-generated section: Game detail pages (756) · Series detail pages · Theme detail pages
   
   Each row has: page name + URL + type pill (Composed/Static/Auto-feed) + status + last edited + Preview button (👁) + Edit button.
   
   Static page editor modal: title, slug, hero image, rich text body, SEO (meta title, description, OG image, noindex toggle), translations table (5 languages with Auto-translate), Danger zone (Unpublish/Delete).

3. Navigation — Visual editor for the persistent Studio Tab Bar at the top of every public page. Drag-reorder the 6 studios + Group. Toggle visibility per studio. Below: editor for the per-studio header nav links (Games / About / Art Media Pack / Contact).

4. Footer — Office address textarea, License text textarea, 5 social URL fields (Facebook, Instagram, LinkedIn, X, YouTube), Regulatory badges upload (MGA, Responsible Gaming Foundation, ONJN), Compliance line, Copyright. Per-studio footer overrides section. Live preview pane on the right.

5. Live site preview — In-line preview of the public website as a visitor would see it. Top: Studio Tab Bar (black bar with 7 brand tabs — clicking one switches the previewed studio). Below: per-studio page nav (Home / Our Games / About / Art Media Pack / Contact). Main area: renders the corresponding public page with the studio's brand colors. Game cards in the catalog are clickable → opens a Game detail mock page with hero + features + stats + Play Demo + Watch Trailer CTAs. Desktop/Mobile toggle at top.

PHASE 10: Users + Roles enhancement

Convert the existing Users screen into a tabbed view:

1. Users tab — existing table.

2. Roles tab — List of 6 roles from poc-data.json with description + scope + user count + permissions count. Plus a quick comparison matrix below (table showing ✓/✕ across all 6 roles for 12 key permissions). Click any role → opens a Role editor modal with:
   - Role basics (name, color, description, default scope)
   - Permission matrix: ~39 individual Yes/No toggles grouped into 6 categories (Catalog, Studios/Series/Themes, Content, Public site, Workflow/operator, Admin). The full list from poc-data.json → roles → permissions.
   - HQ Admin is built-in and read-only (all toggles locked YES, no Delete button).
   - Toggles must reflect the actual permissions for THAT role (not hardcoded).
   - Footer: Delete role / Cancel / Save changes.
   
   Roles must actually apply — a Studio Lead user logged in should only see their own studio's games, not all 750+ games. Use Supabase Row-Level Security to enforce.

3. Pending invites tab — Table of unaccepted invitations with email + role + sent by + sent date + expires + Resend/Revoke buttons.

4. Activity audit tab — Per-user action log with filter chips (User, Action, Date range) and search.

PHASE 11: Polish + cross-cutting features

- Notifications popover (bell icon top right) showing recent activity
- User menu (click avatar bottom-left) with My profile / Preferences / Audit log / Sign out
- Studio detail page game rows + Review queue Review button + Releases calendar events + Dashboard "Upcoming releases" cards — all open the editor for the SPECIFIC game clicked (not hardcoded)
- Series and Theme cards clickable → filter Games page
- Search box in topbar (functional, searches games by name)
- Toast notification system for success/error messages
- 404 page for invalid game/studio slugs
- Loading skeletons on all data fetches

ACCEPTANCE CRITERIA:

1. Clicking any of 10 games shows that game's actual data in the editor — not the same hardcoded one
2. Each studio detail page is themed with that studio's brand color
3. The API at /rest/v1/games?studio_id=koala filters correctly and returns only Koala games
4. A Studio Lead user can only see their own studio's games (Row-Level Security working)
5. Permission matrix toggles actually do something (Contributor can't publish; Studio Lead can submit but not approve; etc.)
6. The page editor's rich text editor produces formatted HTML that the public site can render
7. Image uploads succeed at exact dimensions or reject with a clear error
8. The Live Site Preview shows different content per studio with correct brand colors
9. All 10 games from poc-data.json are seeded in the database; do not generate fake games

When everything works, send back: working URL + login + a sample curl /rest/v1/games?studio_id=koala&status=live request showing JSON with the 2 matching games (Voltage Blitz King Ra 96 and Coelho Jitsu 96). Plus screenshots of: Game editor on a non-Bufón game, Studio detail with Koala branding, Role permission matrix, Group homepage composer, Live Site Preview switching studios.
```

---

## Notes for you (Avi) when running this

**You'll likely need 3–5 chat iterations** with Lovable to land everything. Don't paste the whole thing once and hope for the best — paste it as the opening shot, then iterate phase-by-phase.

**Recommended workflow:**
1. Paste the prompt above as your next message in the Lovable chat
2. Lovable will build a lot — likely Phase 2 (game editor tabs) first
3. After each generation, click through the demo and verify against the HTML reference
4. Ask Lovable for specific phases: "Now build Phase 9 — the Group homepage composer with drag-drop blocks"
5. When stuck on a complex piece (permission matrix, RLS scoping), tell Lovable: "Use Supabase Row-Level Security to enforce studio scope on the games table — Studio Lead users should only see games where studio_id = their assigned studio"

**If Lovable gets confused mid-build**, restart with: "Re-read https://raw.githubusercontent.com/avibaruch76/rubyplay-admin-demo/main/poc-prompt.md and continue from Phase X."

**The hardest things for Lovable** (give these extra attention):
- The permission matrix with 39 toggles actually enforced via RLS
- Per-studio brand theming that flows through the studio detail + Live Site Preview
- The Live Site Preview view with the persistent Studio Tab Bar
- The Group homepage block composer with drag-reorder

**Things Lovable will nail easily**:
- Forms with the 60+ fields per game
- Image uploads to Supabase Storage
- Filter chips with dropdowns
- The auto-generated REST API
