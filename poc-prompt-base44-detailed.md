# Base44 Continuation Prompt — Exhaustive Detail

For your employee building the Base44 POC. Same content as the Lovable version, stack-neutral language.

**Paste the prompt block below into Base44's AI chat.** It's intentionally exhaustive — every screen, every tab, every field, every modal is listed.

---

```
Bring this project to full parity with the reference HTML demo. Use it as the source of truth for UX, fields, and behavior.

REFERENCE MATERIALS — load these and re-read whenever in doubt:
- Spec: https://raw.githubusercontent.com/avibaruch76/rubyplay-admin-demo/main/poc-prompt.md
- Seed data (use these exact records — do NOT make up data): https://raw.githubusercontent.com/avibaruch76/rubyplay-admin-demo/main/poc-data.json
- Visual reference (THE source of truth): https://rubyplay-admin-demo.onrender.com

PLATFORM: Use Base44's native capabilities — its built-in data modeling, file storage, auth, permissions, and public API. Use whatever UI component library Base44 ships with.

⭐ CRITICAL PLATFORM CAPABILITY THE WHOLE PROJECT DEPENDS ON: a PUBLIC REST or GraphQL API that can be called from OUTSIDE Base44 (curl from an external server) and returns JSON. Set this up early and verify it works. If Base44 can't expose a public API on the available plan — STOP and flag immediately.

The full app has these 18 views. Build/complete each one. After each phase, tell me what works.

═══════════════════════════════════════════════════════════════════
SIDEBAR NAVIGATION (must match exactly)
═══════════════════════════════════════════════════════════════════

Left sidebar, ~240px wide, sticky to top, full height.
Top: RubyPlay logo + "ADMIN" tag.
Sections (each section has a small uppercase label above its items):

CATALOG
- Dashboard
- Games
- Studios
- Game Series
- Game Themes
- Releases

CONTENT
- Media library
- Translations
- News

PUBLIC SITE
- Group homepage
- Pages
- Navigation
- Footer
- Live site preview

WORKFLOW
- Review queue (with red badge showing pending count, e.g. "7")

ADMIN
- Users & roles
- Settings

Bottom of sidebar: user avatar (initials in colored circle) + name + role label, clickable to open user menu (My profile / Preferences / Audit log / Sign out).

TOP BAR (persistent across all views):
- Breadcrumb on the left (e.g. "Games" / "Games › Bufón Fortuna Deluxe 96")
- Search input on the right ("Search games, studios, assets...")
- Bell icon with red dot (opens notifications popover)
- ? help icon

═══════════════════════════════════════════════════════════════════
PHASE 1: DASHBOARD VIEW (id: view-dashboard)
═══════════════════════════════════════════════════════════════════

Page header: "Welcome back, Avi" + subtitle "Here's what's happening across all 6 studios (Ruby Play, Koala Games, Mad Hat, Spincraft + Firerose and X Slots ramping up)."

Top right: [📥 Export report] [+ New game] buttons.

Stat tiles row (4 tiles, each clickable):
- Live games: 656 (+40 upcoming) → clicks to Games view
- Studios: 6 (4 active · 2 ramping) → clicks to Studios view
- Scheduled: 40 (Next: Jun 04) → clicks to Releases view
- Pending review: 7 (red, ↑ 3 since yesterday) → clicks to Review queue

Below: 2-column layout.

LEFT CARD: "Upcoming releases" with "See calendar →" link
- 4 game rows, each clickable to open that game's editor:
  1. Diamond Explosion 777 96 — Ruby Play · 5×3 · 96.37% RTP · 8000x · rp_200 — Jun 04, 2026 — Scheduled pill
  2. Mad Hit Diamonds Deluxe 96 — Ruby Play · 3×3×3 · 96.35% RTP · 3799x · rp_211 — Jun 11, 2026 — Scheduled pill
  3. Bufón Fortuna Deluxe 96 — Ruby Play · J Mania® S07 · 96.33% RTP · 3000x · rp_216 — Jun 18, 2026 — Scheduled pill
  4. Voltage Blitz King Ra 96 — Koala Games · Voltage Blitz® S03 · 96.33% RTP · 6000x · kg_5045 — Jun 25, 2026 — Scheduled pill

RIGHT CARD: "Review queue" with "View all →" link
- 3 row entries, each clickable to Review queue:
  1. Voltage Blitz King Ra 96 — Submitted by Maya (Koala Games) — 95% pill
  2. Sweet Crowns — Submitted by Daniel (Spincraft) — 72% pill
  3. BetWarrior Goalinko 96 — Submitted by Tom (Mad Hat) — 88% pill

═══════════════════════════════════════════════════════════════════
PHASE 2: GAMES VIEW (id: view-games) — DEFAULT LANDING
═══════════════════════════════════════════════════════════════════

Page header: "Games" + subtitle "756 total · 656 active · 40 upcoming · 60 archived"

Top right: [⬇ Bulk import] [+ New game] buttons.

Filter chip row (each chip opens a dropdown when clicked — must actually filter the table):
- All studios ▾ (options: All studios, Ruby Play, Koala Games, Mad Hat, Spincraft, Firerose, X Slots)
- Status: Any ▾ (options: Any, Live, Scheduled, In review, Draft, Retired)
- Mechanic: Any ▾ (options: Any, Free Spins, Respin, Hold & Win, Cascades, Megaways, Buy Feature)
- Series: Any ▾ (options: Any, J Mania®, Diamond Explosion®, Mad Hit®, Voltage Blitz®, Rush Fever®, Immortal Ways®, 20K+ Ways®, Goalinko, Crown Jester)
- Theme: Any ▾ (options: Any + the 13 themes from poc-data.json)
- Volatility: Any ▾ (options: Any, 1 · Low, 2 · Low-Med, 3 · Medium, 4 · Med-High, 5 · High)
- Tag: Any ▾ (options: Any, Upcoming, Live, Bespoke, Special Edition)
- ✕ Clear filters (only appears when any filter active)
- Right side: Sort: Newest first ▾ (options: Newest first, Oldest first, RTP high → low, Name A → Z)

Below: Search input "Search pages by name or URL..." (filters rows by name match)

Table columns: Game (thumbnail + name) · Studio · Series · Status pill · Release date · RTP / Vol · Last edit · ⋯ menu

Status pill colors:
- Live: green background, green text
- Scheduled: blue
- In review: pink
- Draft: amber
- Retired: gray

Each row is clickable → opens that game's editor (NOT a hardcoded default; loads THAT game's data).

Seed 10 rows from poc-data.json:
1. Bufón Fortuna Deluxe 96 — Ruby Play — J Mania® (S07) — Scheduled — Jun 18, 2026 — 96.33% · Vol 5 — 2h ago · avi
2. Diamond Explosion 777 96 — Ruby Play — Diamond Explosion® (S02) — Scheduled — Jun 04, 2026 — 96.37% · Vol 4 — 1h ago · avi
3. Mad Hit Diamonds Deluxe 96 — Ruby Play — Mad Hit® (S08) — Scheduled — Jun 11, 2026 — 96.35% · Vol 4 — 4h ago · avi
4. Voltage Blitz King Ra 96 — Koala Games — Voltage Blitz® (S03) — In review — Jun 25, 2026 — 96.33% · Vol 4 — 3h ago · maya
5. Coelho Jitsu 96 — Koala Games — Voltage Blitz® (S03) — Scheduled — Jun 25, 2026 — 96.33% · Vol 4 — 6h ago · maya
6. BetWarrior Goalinko 96 — Mad Hat — — — In review — Jun 04, 2026 — 96.36% · Vol 1 — 4h ago · tom
7. Jozi Gold: Soft Life Deluxe 96 — Ruby Play — Rush Fever® (S01) — Scheduled — Jun 04, 2026 — 96.37% · Vol 3 — 1d ago · avi
8. Sweet Crowns — Spincraft — — — Draft — TBD — 94.53% · Vol 5 — 5h ago · daniel
9. J Mania Goal Nations 96 — Ruby Play — J Mania® (S07) — Live — May 28, 2026 — 96.36% · Vol 5 — 1w ago · avi
10. Voltage Blitz Heat Rush 96 — Koala Games — Voltage Blitz® (S02) — Live — May 21, 2026 — 96.31% · Vol 5 — 1w ago · maya

Below table: "Showing 10 of 756 games · (demo loads a sample; production paginates) · Load more"

When any filter is active, table also shows a blue info banner: "📊 [filter value]: [real count] games in your full catalog · Showing N matching" — uses these catalog totals: Ruby Play 594, Koala Games 87, Mad Hat 12, Spincraft 2; J Mania® 28, Voltage Blitz® 36, Diamond Explosion® 16, Mad Hit® 32, Rush Fever® 22; Classical Slot 42, Gems 38, Egypt/Ra 26, Volcano 18.

═══════════════════════════════════════════════════════════════════
PHASE 3: GAME EDITOR (id: view-editor) — THE WORKHORSE
═══════════════════════════════════════════════════════════════════

Opens when any game row is clicked. CRITICAL: Loads data for THAT game, not hardcoded. URL changes to /games/[game-id].

Editor header card:
- Title (game name) + 2 pills (status pill matching DB status + tag pill matching DB tag)
- Meta line: [Studio] · [Series] · Game ID: [id] · [Scheduled for / Released] [date] · last edited [time ago] by [user]
- Top right buttons: [↗ Preview on site] [⋯ More actions] [Save draft] [Save & publish]

Tabs (8 tabs, click switches content):
| Basic info | Media | Stats | Features | Demo & Play | Marketing | Translations [2/5] | Operator |

The Translations tab shows a "[2/5]" badge indicating how many languages are complete.

─────────────────────────────────────
TAB 1: BASIC INFO
─────────────────────────────────────

Section header "① Basic identity":
- Title* (text input, max 100 chars; show "Add ® after the series name for trademarked series.")
- Studio* (dropdown: Ruby Play, Koala Games, Mad Hat, Spincraft, Firerose, X Slots)
- Game ID* (text input; hint "Internal ID, e.g. rp_216, kg_5045, mh_10007, sc_15002")
- URL slug (text input; hint shows "rubyplay.com/games/[slug]" dynamically)
- Release date* (date picker)
- Game Series* (dropdown: 9 series from seed data + "+ Add new series…")
- Game Theme* (dropdown: 13 themes from seed data + "+ Add new theme…")
- Game Tag* (dropdown: Upcoming, Live, Bespoke, Special Edition (SE))
- Tagline* (text input, max 80 chars; hint shows live char count "26 used")
- Description* (rich text textarea, 5 rows; hint "First paragraph should be bolded. Supports basic formatting.")

Section header "② Quick stats (shown on game card)":
- Max Win* (text input, e.g. "10,000x")
- Line configuration (text input; hint "Or 'No Lines' / '243 Ways'")
- Trailer link (YouTube) (text input; hint "Skip for SE versions.")

Section header "③ Categorization":
- Themes (multi-tag chips with × to remove, "+ Add theme" button)
- Mechanics (multi-tag chips with × to remove, "+ Add mechanic" button)

─────────────────────────────────────
TAB 2: MEDIA
─────────────────────────────────────

Section "① Logo & primary marks" (right-side label: "All assets auto-compressed on upload (PNG → JPG / TinyPNG)"):
- 3-column grid:
  - Game logo (PNG transparent)
  - Studio mark override (PNG transparent)
  - Series mark (PNG transparent)
- Each tile shows current image OR drag-drop upload zone with cloud icon.

Section "② Hero & banner images" (right label: "Specs match the WordPress workflow exactly"):
- 3-column grid of 6 tiles, each with EXACT dimension enforcement:
  - Hero · Desktop landscape — 1920×785 — no logo
  - Banner · Home page — 1280×523 — with logo · skip for Bespoke
  - Hero · Mobile portrait — 1000×1406 — no logo
  - Poster · Mobile portrait — 700×984 — with logo
  - Slider thumbnail — 456×360
  - Square thumbnail — 600×600

When user uploads, validate dimensions. Reject mismatched dimensions with a clear error "Image must be 1920×785, you uploaded 1920×1080. Crop and retry?"

Section "③ Screenshots" (right label: "From media_pack_png/screenshots_buy_feature"):
- Grid of screenshot tiles + "+ Add screenshot" tile. Each upload must be 1920×1080 and tagged "desktop" or "mobileL".

Section "④ Background art (parallax layers, optional)":
- 3 tiles for background layers, 2400×1200 each.

All images stored in Base44's file storage system, organized per game. Make them retrievable via the public API as game.hero_image_url, game.banner_url, etc.

─────────────────────────────────────
TAB 3: STATS
─────────────────────────────────────

Section "① Math stats (shown on the public game page)":
- RTP %* (numeric input; hint "Default RTP · variants synced from Monday")
- Hit Frequency* (text input; hint "From Hit Rate Frequency column")
- Volatility* (5-step slider/segmented control with labels: 1 · Low, 2 · Low-Med, 3 · Medium, 4 · Med-High, 5 · High; hint "Scale: 1 = Low (≤20%), 5 = High (81–100%)"). Selected step has red background + white text.
- Max Win* (text input, e.g. "3,000x")
- Reel Array (text input; hint "From Reel Array column (e.g. 333, 5×3, 333/777)")
- Lines / Ways (text input)
- Buy Feature* (Yes/No toggle, segmented control with Yes left and No right)
- BF Max Win Multiplier (text input; hint "From BF Max Win Multiplier column")

Section "② Custom stat fields" (right side: "+ Add a new feature stat" link):
- Free Spins Trigger (text input)
- Max Multiplier (text input)

─────────────────────────────────────
TAB 4: FEATURES
─────────────────────────────────────

Section "① Game features" (right side: "+ Add feature" link)
Intro paragraph: "Each feature gets a name, description, and image. Use desktop screenshots (not mobileL). Buy Feature counts as one feature."

Each feature is a draggable card with 3 columns (drag handle ⠿ | image picker | text fields | × remove):
- Feature image (100px square, clickable → opens "Select feature image" modal showing only desktop screenshots from this game)
- Feature name (text input, bold)
- Feature description (textarea, 2 rows)
- Remove button (×)

Seed defaults for Bufón Fortuna (just so the demo isn't empty):
1. Lucky Respin — "Trigger the Whirler with 3+ jester symbols. Lucky multipliers stack on every respin."
2. The Whirler — "The Whirler appears randomly during base game to spin up to 50x multipliers."
3. Buy Feature — "Skip the wait and buy direct access to Lucky Respin for 100x your stake."

Drag-to-reorder using @dnd-kit/sortable.

─────────────────────────────────────
TAB 5: DEMO & PLAY
─────────────────────────────────────

Section "① Demo & play URLs":
- Play demo URL* (text input; hint "Public play-for-fun demo (from Demo Link column)")
- Operator integration URL (text input)
- Demo aspect ratio (dropdown: 16:9 Landscape / 9:16 Portrait / 4:3)

Section "② Test the demo":
- Layout: left iframe preview (16:9 with dark background, big ▶ play button), right 240px sidebar with "Demo health" stats (URL responding 142ms, Mobile-ready, No console errors, Last tested 2h ago) — all green dots except amber for the last one.
- Below iframe: 3 buttons: [▶ Load demo] [📱 Test mobile] [🔗 Validate URL]
- "Validate URL" does a fetch HEAD request and shows toast "Demo URL is reachable (200 OK · 142ms)" or "Demo URL unreachable (error)".
- "Load demo" opens a modal with an iframe loading the demo URL.

─────────────────────────────────────
TAB 6: MARKETING
─────────────────────────────────────

Section "① Featured placement":
- Group homepage placement (dropdown: Featured carousel (rotating) / Featured grid / Not featured on group home) — hint "Shows on rubyplay.com"
- Studio homepage placement (dropdown: Position 1 in carousel / Position 2 / In carousel (auto) / Not on studio home) — hint "Shows on rubyplay.com/[studio-slug]"
- Catalog position (dropdown: Default (sorted by release) / Pinned to top / Top row) — hint "Order in the games index"

Section "② Promo banner":
- Promo banner copy (textarea, 2 rows; hint "Shown on homepage carousel")

Section "③ Press & partnerships":
- Press release URL (text input)
- Art Media Pack (ZIP) (upload tile, 4:1 ratio, accepts .zip; hint "Linked from the game page's 'Download Art Media Pack' button")

Section "④ SEO":
- Meta title (text input, max 60 chars; show live char count)
- Meta description (textarea, max 160 chars; show live char count)
- OG image (upload tile, 1200×630 enforced)
- "Index by search engines?" Yes/No toggle

─────────────────────────────────────
TAB 7: TRANSLATIONS
─────────────────────────────────────

Header: "Localized content" + right label "Configure supported languages in Settings"
Below: "Each row is a language. Empty cells highlighted in amber."

Table with 5 rows (English, Spanish, German, Portuguese, Italian):
| Language | Tagline | Description | Status |
|---|---|---|---|
| 🇬🇧 English | [editable text input] | [editable text input] | Complete pill |
| 🇪🇸 Spanish | [editable] | [editable] | Complete pill |
| 🇩🇪 German | [empty, amber bg] | [empty, amber bg] | Missing pill |
| 🇵🇹 Portuguese | [empty, amber] | [empty, amber] | Missing pill |
| 🇮🇹 Italian | [empty, amber] | [empty, amber] | Missing pill |

Below table: [🌐 Request translations] button (calls placeholder DeepL function; show toast "Translation request sent to translation service").

─────────────────────────────────────
TAB 8: OPERATOR
─────────────────────────────────────

Section "① Operator-facing documents" (intro: "These are gated behind operator login on the public site."):
3 document rows, each: icon + filename + meta + [Download] [Replace] buttons:
- 📄 [game-id]-math-sheet.pdf — Math sheet · 2.1 MB · last updated 5 days ago
- ⚙ RGS-integration-[game-id].pdf — Integration guide · 880 KB
- ✓ cert-GLI-19-[slug].pdf — Certification · GLI-19 · expires 2027-06-15

Section "② Certifications & jurisdictions":
- Approved jurisdictions (multi-select with chips, × to remove). Available options (from poc-data.json → jurisdictions, 15 total):
  🇲🇹 MGA · 🇨🇼 Curacao · 🇳🇱 Netherlands · 🇨🇴 Colombia · 🇦🇷 Buenos Aires · 🇷🇴 Romania · 🇮🇹 Italy · 🇨🇦 Ontario · 🇿🇦 South Africa · 🇪🇸 Spain · 🇬🇪 Georgia · 🇧🇷 Brazil · 🇵🇹 Portugal · 🇵🇪 Peru · 🇺🇸 US-NJ

═══════════════════════════════════════════════════════════════════
PHASE 4: STUDIOS VIEW (id: view-studios)
═══════════════════════════════════════════════════════════════════

Header: "Studios" + subtitle "6 brands under the RubyPlay Group — 4 with active catalogs, 2 ramping up."
Top right: [+ New studio] button.

Grid (auto-fill, min 280px wide) of 6 studio cards + 1 "Add new studio" tile.

Each studio card has:
- Cover band (100px tall, gradient using studio's primary/secondary brand colors)
- Logo big (44×44 rounded square, overlapping cover, white border)
- Studio name (large)
- Meta row: [N] games · [N] upcoming · Active/Coming soon pill

Cards (from poc-data.json):
1. Ruby Play — gradient red→dark red — ▶ logo — 594 games · 18 upcoming · Active
2. Koala Games — gradient purple — ◐ — 87 games · 20 upcoming · Active
3. Mad Hat — gradient green — 🎩 — 12 games · 1 upcoming · Active
4. Spincraft — gradient green — ♛ — 2 games · 1 upcoming · Active
5. Firerose — gradient red, opacity 0.85 — ✿ — 0 games · 0 upcoming · "Coming soon" pill
6. X Slots — gradient dark — ✕ — 0 games · 0 upcoming · "Coming soon" pill

Last tile: dashed border "+ Add new studio" with "Bring a new brand into the group" text. Clickable → opens New Studio modal.

Click any card → opens that studio's detail view (NOT a generic page; load THAT studio's data and brand color theming).

═══════════════════════════════════════════════════════════════════
PHASE 5: STUDIO DETAIL VIEW (id: view-studio-detail)
═══════════════════════════════════════════════════════════════════

THIS IS WHERE LOVABLE IS LIKELY MISSING THE MOST. Build it carefully.

Page is themed with that studio's brand_color_primary. URL is /studios/[slug].

Studio header card (240px tall):
- Cover band (140px) using gradient(studio.primary, studio.secondary)
- "● Public page live" pill top right (only for non-placeholder studios)
- Studio logo (72×72 rounded, white border, overlapping the cover, using studio.logoBg color)
- Studio name (page-title size)
- Studio tagline
- Stats row: [Game count] games · [Upcoming] upcoming · [Series count] series · [Team count] team
- Top right: [↗ View public page] [⋯ More] [Save changes] buttons

6 tabs below: | Overview | Homepage content | Games (N) | Series | Team | Settings |

─────────────────────────────────────
TAB 1: OVERVIEW (default)
─────────────────────────────────────

Two-column layout, 2fr left + 1fr right.

LEFT COLUMN:

Section "① About":
- Studio name* (text input)
- URL slug (text input; hint "rubyplay.com/studios/[slug]")
- Founded (text input, year)
- Headquarters (text input)
- Website (text input)
- Contact email (text input)
- Tagline (text input, max 80 chars)
- Description (textarea, 4 rows)

Section "② Brand assets":
3-column upload grid:
- Studio logo (PNG transparent)
- Studio banner (1920×400)
- Mascot/character art (800×1000; hint "Used on Group home 'Our Brands' card")
- Studio dark logo (PNG, for dark backgrounds)
- Studio icon (tab bar) (SVG, 24×24)

Section "③ Brand colors":
- Primary (color picker)
- Secondary (color picker)
- Accent (color picker)

RIGHT COLUMN:

"i Recent activity" feed:
- 2h ago · avi@ updated [latest edited game]
- 1d ago · avi@ published [game] hero image
- 2d ago · [user] uploaded 4 screenshots
- 1w ago · [user] scheduled [game]

"i Catalog snapshot":
- Active: [count] (green)
- Upcoming: [count] (blue)
- Bespoke/Branded: 12
- Series count: [N]
- Last release: [date]

"i Top jurisdictions":
- 🇲🇹 MGA — [N] games
- 🇨🇼 Curacao — [N] games
- 🇧🇷 Brazil — [N] games
- 🇨🇴 Colombia — [N] games
- 🇷🇴 Romania — [N] games

─────────────────────────────────────
TAB 2: HOMEPAGE CONTENT
─────────────────────────────────────

Intro: "This content drives [studio-domain] — the studio's public homepage. ↗ Preview"

Section "① Hero section":
- Hero title (text input)
- Hero subtitle (text input)
- CTA button text (text input)
- CTA destination (dropdown: → Games index / → Featured game / → External URL)

Section "② Curated games carousel" (right side: "+ Add game to carousel"):
Intro: "Pick 3–6 games to feature on this studio's homepage 'Our Games' section. Drag to reorder."
List of drag-reorderable game rows (⠿ handle + thumb + name + meta + Position [N] pill + × remove).

Section "③ About block":
- About heading (text input)
- About body (full text) (textarea, 5 rows)

Section "④ Studio Director quote":
Intro: "A personal message from your studio director — shown as a stylized quote section."
- Director name (text input)
- Director title (text input)
- Director portrait (image upload, square 120×120 max)
- Director message (textarea, 4 rows)

Section "⑤ Studio Art Media Pack":
Intro: "Single ZIP containing the studio's full marketing collateral. Downloadable from the studio's site footer and header."
- Upload tile (ratio 4:1, accepts .zip; shows filename + size + last updated)

─────────────────────────────────────
TAB 3: GAMES (per studio)
─────────────────────────────────────

Intro: "Showing games for [Studio name]. Use the main Games page for cross-studio search."
Sub-table (re-uses the Games table component but pre-filtered to studio):
Columns: Game · Series · Status · Release · RTP / Vol · ⋯
Footer: "Showing N of [total studio games] · View all in main Games page →"

─────────────────────────────────────
TAB 4: SERIES (per studio)
─────────────────────────────────────

Top: "All series owned by this studio." + [+ New series] button.
List of mini-rows: thumbnail + series name + game count + Active pill.

─────────────────────────────────────
TAB 5: TEAM (per studio)
─────────────────────────────────────

Top: "People with access to this studio's content." + [+ Invite to studio] button.
Table: Member (avatar + name + email) · Role pill · Last active · ⋯

─────────────────────────────────────
TAB 6: SETTINGS (per studio)
─────────────────────────────────────

Section "① Defaults for new games in this studio":
- Default game tag (dropdown: Upcoming, Live)
- Default supported languages (dropdown: All 5 supported, English only, Customize)
- Default approved jurisdictions (multi-tag chips with × + "+ Edit defaults")

Section "② Public visibility":
- Show on public studios page? (Yes/No toggle)
- Accept operator inquiries? (Yes/No toggle)

Section "③ Danger zone" (red theme):
- Archive this studio (red button)

═══════════════════════════════════════════════════════════════════
PHASE 6: GAME SERIES VIEW (id: view-series)
═══════════════════════════════════════════════════════════════════

Header: "Game Series" + subtitle "Series group related games (e.g. Olympus, Giga Match®). Manage them here."
Top right: [+ Add new Game Series]

Search input at top.

List of 9 series mini-rows (from poc-data.json):
Each row: thumbnail (gradient) + series name + studio · game count · S01–S0X + Active pill

1. J Mania® — Ruby Play · 28 games · S01–S07
2. Voltage Blitz® — Koala Games · 36 games · S02–S09
3. Diamond Explosion® — Ruby Play · 16 games · S01–S02
4. Mad Hit® — Ruby Play · 32 games · S01–S08
5. Rush Fever® — Ruby Play · 22 games · S01
6. Immortal Ways® — Ruby Play · 18 games · S01–S04
7. 20K+ Ways® — Koala Games · 14 games
8. Goalinko — Mad Hat · 11 games · branded sports series
9. Crown Jester — Spincraft · 2 games

Click any series row → switch to Games view + apply Series filter to that series (so the games page shows only that series' games + a blue banner explaining "J Mania®: 28 games in your full catalog · Showing N matching").

═══════════════════════════════════════════════════════════════════
PHASE 7: GAME THEMES VIEW (id: view-themes)
═══════════════════════════════════════════════════════════════════

Header: "Game Themes" + subtitle "Themes are used to categorize games on the public site."
Top right: [+ Add new Game Theme]

Search input.

Grid (3-4 columns) of 13 theme mini-rows. Each: theme name + game count.

From poc-data.json + counts:
- Classical Slot — 42 games
- Gems — 38 games
- Classic / Diamonds — 29 games
- Egypt / Ra — 26 games
- Sports / Football — 24 games
- Volcano — 18 games
- Chinese / Monkey — 14 games
- South African / Luxury — 12 games
- Greek / Mythology — 11 games
- Asian / Jiu Jitsu — 9 games
- Buffalo / Neon — 7 games
- Space / Sci-Fi — 6 games
- Monarch / Jester — 5 games

Click any theme → Games view filtered by that theme.

═══════════════════════════════════════════════════════════════════
PHASE 8: RELEASES VIEW (id: view-releases)
═══════════════════════════════════════════════════════════════════

Header: "Release calendar" + subtitle "Roadmap across all studios. Click a day to schedule."
Top right: [Today] [List view] [+ Schedule release]

Below: month name (e.g. "June 2026") + ‹ › nav arrows + legend (blue=Scheduled, amber=Draft, green=Live).

Month-view calendar grid (Sun-Sat header + 5–6 rows of day cells, ~100px tall each).
Each day shows the date number top-left + 0–3 stacked event pills below.
Clicking an empty day → opens "Schedule release" modal.
Clicking a release pill → opens that game's editor.
Drag a release pill to a different day → updates release_date in the database.

June 2026 sample events:
- Jun 4: Diamond Explosion 777 96, Jozi Gold Deluxe 96, BetWarrior Goalinko 96 (Scheduled blue)
- Jun 11: Mad Hit Diamonds Deluxe 96 (Scheduled)
- Jun 18: Bufón Fortuna Deluxe (Scheduled) + "Press kit due" (Draft amber, clickable but no game)
- Jun 25: Voltage Blitz King Ra 96, Coelho Jitsu 96, Turbo Storm Eruption 93 (Scheduled)
- Today (current date): highlight with red circle background around the day number

═══════════════════════════════════════════════════════════════════
PHASE 9: MEDIA LIBRARY VIEW (id: view-media)
═══════════════════════════════════════════════════════════════════

Header: "Media library" + subtitle "All assets across studios — assets are auto-compressed (PNG→JPG via TinyPNG-style pipeline)."
Top right: [Filter ▾] [⬆ Upload]

Filter chips: All studios, Type: All, Unused assets only.

Grid (auto-fill, min 180px) of media item tiles:
Each tile: thumbnail (1:1 aspect, gradient or actual image) + filename + type + dimensions + size.
Click → opens Media Detail modal with full preview + metadata (file, type, dimensions, size compressed-from, used in [game name], uploaded by/when) + Delete/Download/Replace buttons.

Sample 8 tiles:
1. bufon-fortuna-hero.jpg — Hero · 1920×785 · 248 KB
2. voltage-blitz-king-ra-slider.png — Slider · 456×360 · 86 KB
3. diamond-explosion-banner-en.jpg — Banner · 1280×523 · 312 KB
4. betwarrior-goalinko-screen-1.jpg — Screenshot · 1920×1080 · 195 KB
5. mad-hit-diamonds-logo.png — Logo · 800×400 · 32 KB
6. coelho-jitsu-trailer.mp4 — Video · 1920×1080 · 14 MB
7. jozi-gold-poster.png — Poster · 700×984 · 442 KB
8. rp_216-math-sheet.pdf — Math sheet · 2.1 MB · operator-only

═══════════════════════════════════════════════════════════════════
PHASE 10: TRANSLATIONS HUB (id: view-translations)
═══════════════════════════════════════════════════════════════════

Header: "Translations" + subtitle "Manage content across 5 supported languages."
Top right: [+ Add language] [🌐 Request all missing]

Card "Coverage by language":
Table:
| Language | Games covered | Coverage | |
|---|---|---|---|
| 🇬🇧 English | 147 / 147 | 100% bar | [Review] |
| 🇪🇸 Spanish | 132 / 147 | 90% bar | [Review] |
| 🇩🇪 German | 78 / 147 | 53% bar amber | [Review] |
| 🇵🇹 Portuguese | 42 / 147 | 29% bar red | [Review] |
| 🇮🇹 Italian | 22 / 147 | 15% bar red | [Review] |

Click [Review] for any language → opens Translation Review modal:
- Title: "🇪🇸 Review Spanish translations" (varies by language)
- Top banner: "[X] of 147 games complete · [Y] games missing translations — auto-translated drafts marked with ✨"
- Top buttons: [✨ Auto-translate all missing] [📥 Export CSV]
- Search input
- List of per-game cards. Each card has 3 states:
  1. Missing — red dot · "Missing translation" — empty amber input fields · "✨ Auto-translate" button per game
  2. Auto-translated draft — yellow card background · "✨ Auto-translated draft · needs human review" · "✓ Approve" button
  3. Complete — green checkmark · "Translation complete" · "Open editor" button
- Each card shows English original (read-only) + target-language editable fields (Tagline + Description)
- Footer: [Save drafts] [✓ Save & publish]

═══════════════════════════════════════════════════════════════════
PHASE 11: NEWS VIEW (id: view-news)
═══════════════════════════════════════════════════════════════════

Header: "News & Press" + subtitle "Posts powering the 'RubyPlay News' section on the public site. Scope to Group or to a specific studio."
Top right: [Drafts (3)] [+ New post]

Filter chips: All scopes, Status: Any, Author: Any.

Table:
| Post (thumb + title) | Scope (studio pill) | Status pill | Published date | Author | ⋯ |

5 seed rows:
1. RubyPlay launches Bufón Fortuna Deluxe across LATAM — Ruby Play — Published — Jun 18, 2026 — avi@
2. RubyPlay Group expands to South Africa — Group-wide — Published — Jun 10, 2026 — avi@
3. Koala Games: 20 new games in our biggest release wave — Koala Games — Scheduled — Jun 25, 2026 — maya@
4. Mad Hat partners with BetWarrior on co-branded Goalinko — Mad Hat — Draft — — — tom@
5. Spincraft welcomes Crown Jester Gold to its lineup — Spincraft — Published — May 12, 2026 — daniel@

Click any row OR [+ New post] → opens "New news post" modal:
- Title (text input)
- Slug (text input)
- Scope (dropdown: Group-wide / Ruby Play only / Koala Games only / Mad Hat only / Spincraft only / Firerose only / X Slots only)
- Publish date (date picker)
- Hero image (upload, 1920×800)
- Excerpt (textarea, 2 rows)
- Body (rich text editor with B / I / U / H1 / H2 / Quote / List / Link / Image buttons)
- Tags (text input)
- "Featured on homepage?" (Yes/No toggle)
- Footer: [Cancel] [Save draft] [Publish]

═══════════════════════════════════════════════════════════════════
PHASE 12: PUBLIC SITE — GROUP HOMEPAGE (id: view-public-home)
═══════════════════════════════════════════════════════════════════

Header: "Group Homepage" + subtitle "Block-based composer for rubyplay.com (the parent homepage). Drag to reorder · click a block to edit."
Top right: [👁 Preview homepage] (red outline) [Save draft] [Publish]

Two-column layout, 1fr + 280px right rail.

LEFT column: list of block rows, each row has [⠿ drag handle] [icon tile] [block name + summary] [Visible/Hidden pill] [Edit button].
7 default blocks:
1. ⚡ Hero block — "A unified gaming ecosystem built for scale" — Visible — [Edit]
2. ★ Our Brands — 6 studios in order — Visible — [Edit]
3. ⭐ Featured games carousel — 4 curated games — Visible — [Edit]
4. 📰 RubyPlay News — auto-feeds latest 3 published posts (link to News view) — Visible — [Edit]
5. ℹ About Us — supporting text 380 chars — Visible — [Edit]
6. 📦 Art Media Pack CTA — Download the global Art Media Pack — Visible — [Edit]
7. 👥 Our Partners — Logo grid · 12 operators — Hidden by default — [Show]

Bottom: dashed "+ Add a block" tile listing block types: Hero · Brands · Featured Games · News · Text+Image · CTA Banner · Testimonials · Custom HTML.

Click "Edit" on any block → opens block-specific edit modal:
- Edit Hero block: Hero title / Supporting text / CTA text / CTA link / Background image
- Edit Brands block: drag-reorder studios + visibility toggle per studio
- Edit Featured Games: drag-reorder up to 6 games picked from catalog + "+ Add game"
- Edit News block: Block title / Posts to show (Latest 3 / 6 / Pick manually) / Show "See All" link Y/N / Filter to scope
- Edit About block: Heading / Body / CTA text + link
- Edit Art Media Pack: Heading / Supporting text / Download ZIP / CTA text

RIGHT rail:
Card 1: "Live preview" — mini thumbnail mock of homepage with red "👁 Click to open full preview" link. Clickable → opens Page Preview modal.
Card 2: "Page settings" — Last published, Unpublished changes count, URL, [SEO settings] [Version history] buttons.

═══════════════════════════════════════════════════════════════════
PHASE 13: PAGES VIEW (id: view-public-pages) — FULL SITEMAP
═══════════════════════════════════════════════════════════════════

Header: "Pages" + subtitle "Every page on the public site — group-level, per-studio, and auto-generated template pages."
Top right: [📥 Export sitemap] [+ New page]

4 stat tiles: Custom pages 8 · Studio homepages 6 · Auto-generated 778 · Total live pages 792.

Filter row:
- 3 tabs that ACTUALLY filter section visibility: All pages / Custom (composed/static) / Auto-generated
- Scope: All ▾ (dropdown with All, Group, Ruby Play, Koala Games, Mad Hat, Spincraft, Firerose, X Slots, Auto-generated)
- Status: Any ▾ (Any, Published, Draft, Hidden)
- ✕ Clear filters (shown when active)
- Search box "Search pages by name or URL..."

Section cards (each card filterable by tabs/scope; collapsable):

🌐 Group (rubyplay.com) — 7 pages:
| Page | URL | Type pill | Status pill | Last edited | Actions |
- 🏠 Home | rubyplay.com/ | Composed | Published | 2 days ago | [👁] [Open composer →]
- ℹ About Us | rubyplay.com/about | Static | Published | 1 week ago | [👁] [Edit →]
- 👥 Our Partners | rubyplay.com/partners | Static | Published | 2 weeks ago | [👁] [Edit →]
- 📰 News index | rubyplay.com/news | Auto-feed | Published | Auto-updates | [👁] [Manage posts →]
- ✉ Contact | rubyplay.com/contact | Static + form | Published | 3 days ago | [👁] [Edit →]
- 📦 Art Media Pack | rubyplay.com/art-media-pack | Static | Published | 1 month ago | [👁] [Edit →]
- 🔒 Privacy Policy | rubyplay.com/privacy | Static (legal) | Published | 3 months ago | [👁] [Edit →]

▶ Ruby Play (rubyplay.com/ruby-play) — 4 pages:
- 🏠 Home | /ruby-play | Composed | Published | 2h ago | [👁] [Edit homepage content →]
- ◆ Games index | /ruby-play/games | Auto (template) | Published | Auto-updates | [👁] [Manage games →]
- ℹ About Ruby Play | /ruby-play/about | Static | Published | 4 days ago | [👁] [Edit →]
- ✉ Contact Ruby Play | /ruby-play/contact | Static + form | Published | 1 week ago | [👁] [Edit →]

Same pattern for each studio (Koala Games, Mad Hat, Spincraft = 4 pages each).
Firerose + X Slots: "Coming soon — pages hidden from site" + "Set up →" CTA (because studios have 0 games yet, dimmed).

🤖 Auto-generated (from data) — 778 pages:
- 🎰 Game detail pages — 756 pages · /[studio]/games/[slug] — "edit via Games" link
- ⛓ Series detail pages — 9 pages · /[studio]/series/[slug] — "edit via Game Series"
- ✦ Theme detail pages — 13 pages · /themes/[slug] — "edit via Game Themes"
- ★ Studio detail templates — "edit via Studios"

Click "Edit →" on any static page → opens Static Page Editor modal (described below).
Click "👁" on any page → opens Page Preview modal (described below).

═══════════════════════════════════════════════════════════════════
STATIC PAGE EDITOR MODAL
═══════════════════════════════════════════════════════════════════

Header: "Edit page: [Page name]"
Top right of header: Cancel × button

Top banner: URL, Scope pill, Status pill, [↗ Preview] button.

Section "① Page basics":
- Page title* (text input)
- Slug (text input; hint "Becomes the URL after the studio root")
- Hero image (optional) (upload, 1920×600)

Section "② Page content (rich text)":
- Rich text toolbar: B / I / U / | / H1 / H2 / H3 / | / ❝ Quote / • List / 🔗 Link / 📷 Image / ▦ Block / | / ‹/› HTML toggle
- Body textarea (min 280px tall)

Section "③ SEO":
- Meta title (text input)
- Meta description (textarea, 2 rows)
- OG image (upload, 1200×630)
- "Index by search engines?" Yes/No toggle

Section "④ Translations":
- 5-language coverage table (same as game editor translations)

Section "⑤ Danger zone" (red theme):
- Unpublish button (red)
- Delete button (red)

Footer: [Cancel] [History] [Save draft] [Save & publish]

═══════════════════════════════════════════════════════════════════
PHASE 14: PUBLIC NAVIGATION (id: view-public-nav)
═══════════════════════════════════════════════════════════════════

Header: "Site navigation" + subtitle "The persistent Studio Tab Bar at the top of every page + the main nav links."
Top right: [Save changes]

Card "Studio Tab Bar order":
Intro: "This black bar appears at the top of every page across the entire site. Drag to reorder. Toggle visibility per studio."

Visual preview at top: actual black bar mock with the 7 tabs displayed (small icons).

Below: list of drag-reorderable rows:
- ⠿ ▶ RubyPlay Group (parent) | rubyplay.com | Visible
- ⠿ ▶ Ruby Play | rubyplay.com/ruby-play · 594 games | Visible
- ⠿ ◐ Koala Games | rubyplay.com/koala-games · 87 games | Visible
- ⠿ ✿ Firerose | rubyplay.com/firerose · 0 games | Coming soon
- ⠿ 🎩 Mad Hat | rubyplay.com/mad-hat · 12 games | Visible
- ⠿ ♛ Spincraft | rubyplay.com/spincraft · 2 games | Visible
- ⠿ ✕ X Slots | rubyplay.com/x-slots · 0 games | Coming soon

Card "Per-studio header nav":
List of drag-reorderable nav links shown in the header of each studio:
- ⠿ Games → {studio}/games | Visible
- ⠿ About Us → {studio}/about | Visible
- ⠿ Art Media Pack → direct download | Visible
- ⠿ Contact → {studio}/contact | Visible
- [+ Add nav link]

═══════════════════════════════════════════════════════════════════
PHASE 15: PUBLIC FOOTER (id: view-public-footer)
═══════════════════════════════════════════════════════════════════

Header: "Footer" + subtitle "Office address, license info, social links, regulatory badges — shown at the bottom of every page."
Top right: [Save changes]

Two-column layout: 2fr form + 1fr live preview.

Section "① Company details":
- Office address (textarea) — default: "14 SOHO Office Space, The Strand · Fawwara Building, Triq I-Imsida, Il-Gżira, GŻR 1401, Malta."
- License text (textarea) — default: "Licensed and regulated by the Malta Gaming Authority to supply Type 1 gaming services under a B2B Critical Gaming Supply License (License number: MGA/B2B/826/2020, issued on 24th June 2021)."

Section "② Social links" (5 inputs):
- 🟦 Facebook (text input) — default: facebook.com/rubyplay
- 🟪 Instagram — default: instagram.com/rubyplaygames
- 🟦 LinkedIn — default: linkedin.com/company/rubyplay
- ⬛ X (Twitter) — default: x.com/rubyplay
- 🟥 YouTube — default: youtube.com/@rubyplay

Section "③ Regulatory badges":
Upload grid for badge images (3 default + Add):
- 🇲🇹 MGA · Malta Gaming Authority
- RESPONSIBLE GAMING FOUNDATION
- 🇷🇴 ONJN · Romania badge
- + Add regulatory badge

Section "④ Compliance":
- Compliance line (text input) — default: "18+ | Please Gamble Responsibly"
- Copyright (text input) — default: "Copyright © 2026 RubyPlay ® All Rights Reserved."

Section "⑤ Per-studio footer overrides":
Intro: "By default each studio uses the same footer. Override per studio if regulations or branding differ."
List of override rows. [+ Add studio override]

RIGHT rail: "Live preview" — mock dark footer showing how it looks: red ▶ RUBYPLAY logo + social icons + address text + license text + badge pills + compliance + copyright.

═══════════════════════════════════════════════════════════════════
PHASE 16: LIVE SITE PREVIEW (id: view-site-preview) — CRITICAL
═══════════════════════════════════════════════════════════════════

THIS IS THE MAGIC VIEW. AI builders typically miss this — build it carefully.

Header: "Live site preview" + subtitle "Browse the public site as a visitor would. Switch studios via the tab bar — switch pages via the studio nav."
Top right: Device: [🖥 Desktop] [📱 Mobile] [↗ Open]

Below header:

Studio Tab Bar (black background, full width, ~50px tall):
7 round tabs in a row:
- ▶ GROUP (active = white background, brand color text, "popped up" with rounded top corners)
- ▶ (Ruby Play, brand red)
- ◐ (Koala, yellow)
- ✿ (Firerose, red — faded 50% because coming soon)
- 🎩 (Mad Hat, yellow)
- ♛ (Spincraft, yellow)
- ✕ (X Slots, gray — faded 50%)
- Right: 🇬🇧 EN

Page tabs row (changes based on selected studio):
- Group: Home / Our Partners / About Us / News / Art Media Pack / Contact / Privacy
- Each studio: Home / Our Games / About Us / Art Media Pack / Contact

Active tab has brand color text + bottom border.

Main preview area below: renders the actual public page content (no admin chrome) — see Page Renderers section below.

Click any of the 7 Studio Tab Bar tabs → switches the body to that studio's home (or first available page). The Studio Tab Bar itself stays visible.
Click any page tab → renders that page in the body.
Click any game card on the Games index → switches to that game's detail page (with hero, features, stats, Play Demo, Watch Trailer buttons).
Click Desktop/Mobile → toggles body wrapper between full width and 380px phone frame.

═══════════════════════════════════════════════════════════════════
PUBLIC PAGE RENDERERS (used by Live Site Preview + Pages Preview modal)
═══════════════════════════════════════════════════════════════════

Each renderer takes (studioKey, brandColor) and returns full styled HTML of the public page. NO admin chrome — these render a real-looking public site.

1. group-home — RubyPlay Group homepage:
   - White hero section with big black headline "A unified gaming ecosystem built for scale"
   - Black background "Our Brands" section with 4 studio cards (mascot art with logo overlay)
   - Black background "Featured Games" carousel (4 game tiles)
   - White "RubyPlay News" section (3 news cards)
   - Light gray "About Us" section
   - Darker gray "Art Media Pack" section with red CTA
   - Black footer (full RubyPlay footer with badges)

2. group-about — About Us page:
   - White hero with "About Us" title
   - Long body content with H2 sections (Our story, Our reach, Get in touch)
   - Footer

3. group-partners — Our Partners:
   - Hero "Our Partners" + subtitle
   - Grid of 18 operator logo placeholders
   - Footer

4. group-contact — Contact:
   - Hero "Get in touch"
   - Form with Name, Email, Company, Topic dropdown, Message textarea, Send message button
   - Footer

5. group-amp — Art Media Pack:
   - Hero with red CTA "Download global pack (42 MB)"
   - 3-column grid of per-studio bundles (Ruby Play 38 MB, Koala 22 MB, Mad Hat 8 MB)
   - Footer

6. group-privacy — Privacy Policy:
   - Hero "Privacy Policy" + last updated date
   - 4 H2 sections of legal text
   - Footer

7. news-index — News index page:
   - Hero "RubyPlay News"
   - 2×2 grid of news cards (each: image + category pill + date + headline + excerpt)
   - Footer

8. studio-home — Per-studio homepage (parameterized by studio):
   - Brand-colored hero gradient with studio's primary/secondary colors and accent text
   - Big tagline (white text on gradient)
   - "Explore our games →" CTA in studio's accent color
   - White "Our Games" section with 4 game card tiles + "View All Games" button
   - Light gray "Studio Director" section with portrait circle + name + title + italic quote
   - White "About [Studio]" section
   - Brand-colored "Art Media Pack" section with CTA
   - Footer

9. studio-about — Per-studio About page:
   - Hero with studio name
   - Description + founded + HQ + game stats
   - Footer

10. studio-contact — Per-studio Contact:
    - Hero "Contact [Studio]"
    - Form with brand-colored submit button
    - "Or email [studio.email]" link below form
    - Footer

11. games-index (per studio or group) — Public games catalog:
    - Studio tab bar + nav header
    - Black background
    - "Our Games" title (brand color)
    - Sort + Filters button + Search icon
    - 3-column grid of game cards. Each card:
      * Square gradient image (using game's brand colors) with game name overlay at bottom (white, bold)
      * Dark card body below: RTP, Volatility, Max Win rows
    - "Load More Games" button
    - Footer
    - CRITICAL: Each game card is clickable → switches to game-detail page

12. game-detail — Public game detail page:
    - Studio tab bar + nav
    - White: Big game name centered
    - 21:9 hero artwork (gradient using game's colors) with game name + Play Demo + Watch Trailer buttons overlaid bottom-left
    - Black: "Supporting one-liner, game intro" title (brand color centered)
    - 2-column body: long description on left (60ch) + right rail (Play Demo CTA + features list with bullets + stats: RTP, Volatility, Hit Frequency, Max Win)
    - White: Watch Trailer + Download Art Media Pack buttons + 3 screenshot thumbnails
    - Footer

═══════════════════════════════════════════════════════════════════
PHASE 17: REVIEW QUEUE (id: view-review)
═══════════════════════════════════════════════════════════════════

Header: "Review queue" + subtitle "7 submissions waiting for HQ approval before publishing."
Top right: [Filter ▾]

5 submission rows. Each row: thumbnail + game name + "Submitted by [submitter] · [studio] · [time ago]" + Completeness bar (140px wide, label "Completeness · NN%", green/amber/red fill) + actions [Review] [Approve & publish] OR [Request changes].

5 seed rows:
1. Voltage Blitz King Ra 96 — Koala Games · kg_5045 · Maya Chen 3h ago — 95% (green) — [Review] [Approve & publish]
2. Coelho Jitsu 96 — Koala Games · kg_5055 · Maya Chen 5h ago — 100% (green) — [Review] [Approve & publish]
3. BetWarrior Goalinko 96 — Mad Hat · mh_10007 · Tom Müller 4h ago — 88% (green) — [Review] [Request changes]
4. Sweet Crowns — Spincraft · sc_15002 · Daniel Cohen 1d ago — 72% (amber) — [Review] [Request changes]
5. Voltage Blitz Lucky Wukong 96 — Koala Games · kg_5570 · Maya Chen 2d ago — 78% (amber) — [Review] [Request changes]

Click [Review] → opens that specific game's editor.
Click [Approve & publish] → row animates out + toast "Game name approved & published".
Click [Request changes] → opens Request Changes modal (textarea + Send button; submitter gets notified).

═══════════════════════════════════════════════════════════════════
PHASE 18: USERS & ROLES (id: view-users) — WITH 4 TABS
═══════════════════════════════════════════════════════════════════

Header: "Users & roles" + subtitle "Manage who can access the admin and what they can do."
Top right action varies by tab:
- Users tab: [+ Invite user]
- Roles tab: [+ New custom role]
- Invites tab: [+ Invite user]
- Audit tab: [📥 Export audit log]

4 tabs:
- Users (5)
- Roles (6)
- Pending invites [red badge 2]
- Activity audit

─────────────────────────────────────
USERS TAB
─────────────────────────────────────
Table: User (avatar + name + email) · Role pill · Scope · Last active · ⋯
Rows (from poc-data.json):
1. Avi Baruch · avi@rubyplay.com — HQ Admin pill — All studios — Just now
2. Maya Chen · maya@koalagames.com — Studio Lead pill (purple bg) — Koala Games only — 3h ago
3. Daniel Cohen · daniel@spincraft.com — Studio Lead pill — Spincraft only — 1d ago
4. Tom Müller · tom@madhat.com — Studio Lead pill — Mad Hat only — 4h ago
5. Sara Martinez · sara@rubyplay.com — Contributor pill (amber) — Ruby Play only — 5h ago

─────────────────────────────────────
ROLES TAB
─────────────────────────────────────

Intro: "Roles determine what each user can do. Click a role to view or edit its permissions. HQ Admin is built-in and can't be edited."

Top: [+ New custom role] button (or in top-right actions).

Table:
| Role | Description | Scope | Users | Permissions | |
|---|---|---|---|---|---|
| HQ Admin (red pill) | Full access to everything across all studios. | All studios | 1 user | 39 / 39 permissions ● (green dot) | [View →] |
| HQ Editor (blue pill) | Manages catalog and public site, can't change users or settings. | All studios | 0 users | 34 / 39 permissions | [Edit →] |
| Studio Lead (blue pill) | Submits/publishes within own studio, manages studio assets and news. | 1 studio | 3 users | 19 / 39 permissions | [Edit →] |
| Contributor (amber pill) | Drafts game content, can submit but not publish. | 1 studio | 1 user | 11 / 39 permissions | [Edit →] |
| Translator (purple pill) | Edit-only access to translations across the catalog. | All studios | 0 users | 3 / 39 permissions | [Edit →] |
| Read-only (gray pill) | View access only — for stakeholders or auditors. | Configurable | 0 users | 6 / 39 permissions (view-only) | [Edit →] |

Below: Section "i Quick comparison" — table showing all 6 roles in columns + 12 key permission rows. Cells show ✓ (green) / ✕ (red) / "own" (green) / "submit" (amber).

Key permissions to show in comparison: View games · Create/edit games · Publish games · Approve submissions · Edit translations · Edit Group homepage · Edit Studio homepage · Manage media library · Manage studios/series/themes · Manage users · Edit settings · View audit log.

ROLE EDITOR MODAL (click any role row):
- Header: "Edit role: [Role name]" or "View role: HQ Admin" (HQ Admin is readonly) + counter "N / 39 permissions · X users"
- Section "① Role basics": Role name, Pill color, Description, Default scope (Single studio / All studios / Configurable), Can be assigned to (Internal team / External users / Both)
- Section "② Permissions matrix" — 39 individual Yes/No toggles in 6 grouped cards:

📂 Catalog (9 toggles):
- View games (all studios)
- View games (own studio only)
- Create new games
- Edit existing games
- Publish games (skip review)
- Submit games for HQ review
- Archive / delete games
- Bulk import games (folder upload)
- Override Monday-synced fields

★ Studios, Series & Themes (5 toggles):
- View studios
- Create new studios
- Edit studio info & branding (own)
- Manage Game Series
- Manage Game Themes

📰 Content (7 toggles):
- Upload to media library
- Delete media assets
- Edit translations (own studio)
- Auto-translate via DeepL
- Create news posts (own studio)
- Publish news posts
- Manage group-wide news posts

🌐 Public site (6 toggles):
- Edit Group Homepage composer
- Edit Studio Homepage (own)
- Edit static pages (About/Contact/Privacy)
- Edit navigation (tab bar + nav)
- Edit footer
- Manage Art Media Pack (own studio)

✓ Workflow & operator (5 toggles):
- View review queue
- Approve submissions
- Request changes on submissions
- Upload operator certs (GLI / RGS docs)
- Manage jurisdictions

⚙ Admin (7 toggles):
- Invite users
- Change user roles
- Edit custom roles & permissions
- View audit log (own scope)
- View audit log (all studios)
- Edit global settings (languages, integrations)
- Manage Monday.com sync

Toggle states MUST reflect the actual role's permissions (not hardcoded). Loading the HQ Admin shows all 39 YES. Loading Studio Lead shows the specific pattern from rolePerms in the demo.

Below toggles: "Users with this role" list — shows only the actual users with THIS role (not always Maya/Daniel/Tom).

Footer: [Delete role] (red, hidden for built-in HQ Admin) + [Cancel] + [Save changes]

CRITICAL: Permissions must ACTUALLY apply via Base44's record-level permission system / access control:
- Studio Lead user logged in → can only see games where studio_id = their assigned studio
- Contributor user → can't see Publish button on games
- HQ Editor → can see all studios' games but NOT the Users & roles section

─────────────────────────────────────
PENDING INVITES TAB
─────────────────────────────────────
Intro: "2 invitations sent, awaiting acceptance. Invites expire after 7 days."
Table: Email · Role pill · Scope · Sent by · Sent · Expires · [Resend] [Revoke]
Rows:
1. new.designer@rubyplay.com · Studio Lead · Firerose · avi@ · 2 days ago · in 5 days
2. auditor@external.com · Read-only · All studios · avi@ · 4 days ago · in 3 days

─────────────────────────────────────
ACTIVITY AUDIT TAB
─────────────────────────────────────
Filter chips: All users / Action: Any / Last 7 days + search input.
Table: When · User · Action · Target · Result pill
Rows:
1. 2 min ago · avi@ · Published · Bufón Fortuna Deluxe 96 · Success
2. 14 min ago · maya@ · Submitted for review · Voltage Blitz King Ra 96 · Success
3. 1 hour ago · avi@ · Approved · Coelho Jitsu 96 (Koala) · Success
4. 3 hours ago · tom@ · Uploaded asset · betwarrior-screen-1.jpg · Success
5. 5 hours ago · daniel@ · Tried to publish · Sweet Crowns · "Blocked — no permission" (gray pill)
6. 1 day ago · avi@ · Invited user · new.designer@rubyplay.com · Success

═══════════════════════════════════════════════════════════════════
PHASE 19: SETTINGS (id: view-settings)
═══════════════════════════════════════════════════════════════════

Header: "Settings" + subtitle "Brand, languages, integrations, audit."

Single card with sections:

Section "① Supported languages":
- 5 default chips (🇬🇧 English default ×, 🇪🇸 Spanish ×, 🇩🇪 German ×, 🇵🇹 Portuguese ×, 🇮🇹 Italian ×) + "+ Add language"

Section "② Integrations":
- 📺 YouTube (trailers) — Connected · API key configured — [Manage]
- 🗜 TinyPNG compression — Connected · auto-compress on upload — [Manage]
- 🌐 DeepL translation — Connected · auto-translate drafts — [Manage]
- 📋 Monday.com (game data sync) — Connected · sync every 15 min — [Manage]

Section "③ Audit log":
"Last 5 changes shown. View full log →"
Lines:
• 2h ago · avi@ updated "Bufón Fortuna Deluxe 96" basic info
• 3h ago · maya@ submitted "Voltage Blitz King Ra 96" for review
• 4h ago · tom@ uploaded 3 screenshots to Mad Hat library
• 5h ago · daniel@ created "Sweet Crowns" draft
• 1d ago · avi@ published "Diamond Explosion 777 96" hero image

═══════════════════════════════════════════════════════════════════
CROSS-CUTTING FEATURES (build alongside everything else)
═══════════════════════════════════════════════════════════════════

1. NOTIFICATIONS POPOVER
Click the bell icon in topbar → opens popover (anchored to top-right, 360px wide).
Title: "Notifications" + [Mark all read] link.
List of recent activity rows:
- Maya submitted "Voltage Blitz King Ra 96" for review — 3h ago · Koala Games (red dot for unread)
- Tom submitted "BetWarrior Goalinko 96" — 5h ago · Mad Hat (red dot)
- Reminder: Bufón Fortuna Deluxe releases in 3 weeks — 9h ago · Schedule (red dot)
- Daniel uploaded 6 new screenshots — 1d ago · Spincraft (no dot)
Click rows → navigate to relevant view.

2. USER MENU
Click avatar bottom-left of sidebar → opens menu:
- My profile
- Preferences
- Audit log
- (divider)
- Sign out (red text)

3. TOAST NOTIFICATIONS
Bottom-right of screen, stacked. Each toast: icon + message. Types: success (green icon), error (red), info (blue). Auto-dismiss after 2.8 seconds.

4. SEARCH BOX
Topbar search → autocomplete suggestions for games, studios, assets. On Enter: navigates to filtered Games view.

5. LOADING SKELETONS on data fetches.
6. 404 page for invalid game/studio slugs.
7. Empty states with clear CTAs (e.g. "No games yet for Firerose — [+ Add first game]").

═══════════════════════════════════════════════════════════════════
MODALS (28 total) — all must work and look like the HTML demo
═══════════════════════════════════════════════════════════════════

1. New game (Title / Studio / Game ID / Release date / Series / Tag → Create draft → opens editor)
2. New studio (Name / Slug / Founded / Short description / Logo upload)
3. New series (Name / Studio)
4. New theme (Name / Display color picker)
5. Upload asset (drag-drop file area + auto-suggest slot based on dimensions)
6. Bulk import games (folder upload, auto-detect game IDs from folder names)
7. Play demo (mock slot game player with reels + SPIN button + balance/credits)
8. Preview (full public-site page preview)
9. Request changes (textarea + Send)
10. Schedule release (Game dropdown + Date + Send press kit Y/N)
11. Invite user (Email / Role / Studio scope)
12. Role editor (the big 39-toggle matrix — described above)
13. Page preview (mock public page rendering)
14. Static page editor (described above)
15. New page (Page name / Slug / Scope / Type / Template starting point)
16. New post (described above)
17. Edit Hero block / 18. Edit Brands / 19. Edit Featured / 20. Edit News / 21. Edit About / 22. Edit AMP / 23. Add block picker
24. Translation Review (described above)
25. Add language (Language picker + Auto-translate Y/N)
26. Media detail (image preview + metadata + Delete/Download/Replace buttons)
27. Select feature image (filtered to desktop screenshots only)
28. More actions (Duplicate game / Export to JSON / Archive game / Delete permanently)

═══════════════════════════════════════════════════════════════════
ACCEPTANCE TESTS (verify ALL of these work before declaring done)
═══════════════════════════════════════════════════════════════════

✅ Click 10 different game rows → editor shows 10 different game contents (not Bufón every time)
✅ Click a Ruby Play studio card → studio detail page uses red brand color theming
✅ Click a Koala Games studio card → studio detail page uses purple brand theming
✅ Click "Live site preview" in sidebar → Studio Tab Bar shows + Group home renders
✅ Click ◐ Koala in Studio Tab Bar → switches to Koala homepage with purple branding
✅ Click "Our Games" page tab while on Koala → shows Koala games catalog (6 games visible)
✅ Click any game card in Koala games catalog → shows that game's detail page
✅ Click 🎩 Mad Hat in Studio Tab Bar → switches to green-themed Mad Hat home
✅ Open Game Series → click "Voltage Blitz®" → jumps to Games filtered to Voltage Blitz (3 visible)
✅ Open Game Themes → click "Sports / Football" → jumps to Games filtered to Sports (2 visible)
✅ Open Releases → click "Mad Hit Diamonds Deluxe 96" on Jun 11 → editor opens with rp_211
✅ Open Releases → click empty Jun 13 → Schedule release modal opens
✅ Open Users & roles → Roles tab → click HQ Admin → modal shows all 39 toggles ON, all locked (no edit)
✅ Click Studio Lead role → modal shows 19/39 ON with specific pattern (Submit Yes, Publish No)
✅ Click Translator role → modal shows only 3 translation toggles ON
✅ Open Translations → click "Review" next to German → modal shows games missing German translations
✅ Open Group homepage composer → drag Hero block to position 2 → blocks reorder
✅ Click "Edit" on Hero block → modal opens with Hero fields editable
✅ Open Pages view → click "Custom" tab → Auto-generated section hides
✅ Open Pages view → click "Edit →" on "About Us" → Static page editor opens with About Us content
✅ Open Pages view → click "👁" preview on any row → Page Preview modal opens with mock page
✅ Open News → click "+ New post" → modal opens with rich-text editor
✅ Curl /api/games?studio_id=koala&status=live → returns 2 games as JSON (from OUTSIDE Base44 with API key auth)
✅ Curl /api/games?series_id=j-mania → returns 2 games (Bufón + J Mania Goal Nations)
✅ Login as Maya (Studio Lead, Koala) → Games view shows ONLY Koala's games (record-level access enforced)
✅ Login as Sara (Contributor) → Games editor hides the "Save & publish" button
✅ Notifications popover opens when clicking bell icon → shows 4+ items
✅ User menu opens when clicking avatar bottom-left → 4 items + sign out
✅ Toast appears bottom-right on every save/publish action

When done, send screenshots of each ✅ working, plus a curl test of the API showing JSON returned.

═══════════════════════════════════════════════════════════════════
BUILD ORDER (do these in this exact order)
═══════════════════════════════════════════════════════════════════

1. Wire game rows → openGame(id) → editor loads correct game (highest priority — currently broken)
2. Build out all 8 editor tabs with the listed fields
3. Build Studio detail page with brand theming + 6 tabs
4. Build Game Series + Game Themes views with clickable navigation to filtered Games
5. Build Releases calendar with drag-drop + click handlers
6. Build Media library + Translations hub + News views
7. Build Public Site section (5 views) with composer + Live Site Preview
8. Build Users & roles 4-tab structure with 39-toggle Role editor
9. Wire Base44's permission system to actually enforce roles (studio_lead users can only see/edit games where studio_id matches their assigned studio)
10. Polish: toast, loading skeletons, search, notifications, user menu

After each step, run the acceptance tests for that step before moving on.
```

---

## After pasting the prompt

Base44 will likely chunk this into 3–5 generations. Some tips:

- **If Base44 says "this is too much"** → tell it to start with steps 1 + 2 (game editor + per-row loading), then ask for the rest in follow-up messages
- **Test the public API EARLY** — after step 1 finishes, immediately try `curl https://[your-base44-url]/api/games` from a terminal. If it doesn't work or asks for enterprise tier, STOP and flag to Avi before building more
- **If a phase comes out generic** → say "look at https://rubyplay-admin-demo.onrender.com → [specific view] → the [X] should look like [Y]"
- **If permissions don't enforce** → "Use Base44's permission/access control system: studio_lead users should only be able to read/update games where studio_id matches their assigned_studio_id. Document how this is configured in Base44 so we can verify."
- **If the public API doesn't work or requires an enterprise upgrade** → STOP and flag immediately to Avi. That's the make-or-break test for Base44.
- **If Base44's UI components produce a generic look** → reference the visual demo at https://rubyplay-admin-demo.onrender.com and ask Base44's AI to match the layout patterns (sidebar grouped by section, tabbed game editor, brand-colored studio cards, status pills with semantic colors).
- **If the Live Site Preview is half-built** → "The Live Site Preview view needs to render the actual public page templates inside its body — each page renderer takes (studioKey, brandColor) and outputs the full public site HTML. See the Page Renderers section of the spec."
