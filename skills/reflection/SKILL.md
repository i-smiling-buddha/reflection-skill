---
name: reflection
description: Study any website, app, game or shipped software and recreate it clean-room: evidence-labelled recon, build spec or full build, parity check, refine loop, review-driven fixes, rebrand, launch and deploy. Use for "clone/recreate/reverse engineer/rebuild X" or "how does X work".
---

# Reflection (प्रतिबिंब · Pratibimb): recreate anything, clean-room

*Like the original in what it does, never the original itself.*

One method merged from four open-source sources:
- **REA** (morluto/rea, MIT): evidence-first investigation, target routing, summary-first paging, finding ledger.
- **Craft Anything** (storytold/craft-anything, MIT/Apache-2.0): Study → Build → Check → Ready loop, Clean room vs Deep mode, durable brief/plan/hypotheses/handoff.
- **Replica** (Jakeschincariol/replica-skill, MIT): recon map, feature matrix, architect, design tokens, build, backend, test, diff, entrepreneur, brand, launch, deploy.
- **Reverse engineer Apps (no install)** (Notion, distilled from REA): screenshots-only checklist → findings → data model → "Build this" spec.

**It rebuilds what a product does, never what it owns.** Features, flows and UX patterns, written fresh. Never its code, assets, logo, name, copy, colours, content or private APIs.

---

## 0. Pick the track and the mode (always first)

Ask, or propose and get a yes:

1. **Target**: name + platform (website, web app, desktop, Android, iOS, game, file/package). If the user says "my app" without naming it, ask which. Never pick an example target yourself.
2. **Goal**: understand one feature / write a build spec / build a working version / build a sellable product.
3. **Slice**: "all of Notion" is not a project; "pages, blocks and sharing" is. Default to the core loop (the one flow users pay for).
4. **Who it is for**: own use, a niche, a product to sell.

| Track | When | Ends with |
|---|---|---|
| **Lite** (no install) | only screenshots/recordings/public pages; user wants a spec for Base44, Lovable, Claude, ChatGPT | checklist + findings table + data model + "Build this" spec (Phase L) |
| **Full** | user wants working code | Phases 1–9, optionally 10–13 |
| **Product** | user wants to sell it | Full + Entrepreneur, Brand, Launch, Deploy |

| Mode | What may be read | Default |
|---|---|---|
| **Clean room** | only what a normal user sees: screenshots, recordings, visible text, measured layout/spacing/colours, help docs, pricing, store listings, public API docs, the user's own account driven at human speed | **yes** |
| **Deep** | also the inside of a shipped artifact (binary, APK, ASAR, JS bundle, firmware) via REA / Craft Anything tools | only when the user owns the software, it is open source, or analysis is clearly permitted by its licence/law (interoperability, security of their own release); for private understanding |

Even in Deep mode: findings inform *behaviour*; no decompiled code, extracted assets or strings are pasted into the new build. If a question needs Deep mode and it is not allowed, say so instead of working around it.

---

## Ground rules (every phase)

- **Allowed access only.** Public sources and the user's own account. Never log into someone else's account, ask for passwords, bypass a login, paywall, paid feature, CAPTCHA or rate limit. If the account's terms forbid building a competitor, say so and use public sources only.
- **Reading, not scraping.** No crawlers, bulk downloads or loops against the original. Never load-test, fuzz or hammer the original's servers. Test only your own build.
- **No private APIs.** Only official public APIs with the user's own keys. Never reuse the original's endpoints or OAuth client.
- **Label every claim** (REA + Notion):
  - **OBSERVED**: directly in a screenshot, recording, capture or bytes. Cite the source (screenshot S07, recording F02 0:42, `ev_…` id).
  - **DERIVED**: computed from observations (a flow graph, a call graph, a measured spacing scale).
  - **INFERRED**: judgment ("it must work this way"). Never infer behaviour from labels or names alone.
  - **UNKNOWN**: open; record what would resolve it.
- **Absence is not proof.** "Not found" only covers what was searched. State the search boundary.
- **Predict, then verify.** Before testing a hypothesis, write what you expect. If the result disagrees, update the hypothesis; do not explain the result away.
- **Summary first, then page.** Ask for overviews, then the specific item. Never repeat an identical call that already succeeded or failed.
- **Never fabricate** reviews, quotes, numbers, users, testimonials or check results. Write "to run" for any check nobody ran.
- **The user does accounts and money.** Claude never buys domains, types passwords, cards or live keys, or signs up for services. Claude writes `.env.example`, DNS records and exact steps.
- **Nothing goes live without the user's go**, and never before the rebrand sweep is clean.

---

## Working memory: the `recreate/` folder

Long jobs outlive one context window (Craft Anything). Keep these files current in the user's project:

```
recreate/brief.md          question, why, target, constraints, mode, what "done" looks like
recreate/plan.md           numbered steps, each todo / doing / done / blocked (+ reason)
recreate/ledger.md         hypotheses (prediction, status) + findings (statement, label, evidence) + unknowns
recreate/handoff.md        where things stand, next step, traps (dead ends, slow tools, misleading strings)
recreate/sources.md        every source with URL and date read
recreate/recon.md          screens, flows, components, data model, out of scope, size
recreate/features.csv      feature,area,priority,original,clone,notes
recreate/screens/          reference screenshots of the original (never shipped)
recreate/clone-screens/    same views of the build, same viewport and state
```

1. **Start or resume**: read `handoff.md` and `plan.md` first; continue, do not restart.
2. **New question**: write `brief.md` and `plan.md` before any analysis.
3. **After each batch of work**: update plan status; add hypotheses; promote settled ones to findings with evidence.
4. **End of every turn**: rewrite `handoff.md` as if a stranger picks it up next.
5. Conclusions in replies must match recorded findings, never chat-only claims.

---

## Phase L — Lite track (screenshots only, no install)

Inputs: the app's name; screenshots/recordings from the user's own account or public pages. If none yet, ask for: every main screen, one full journey of the key feature, any settings or results page, and the empty/error states if reachable.

1. **Checklist first**: every screen, every action, every rule, every piece of stored data, with the evidence each answer needs.
2. **Feature by feature**: where the user starts → what they do → what changes → what they end up with. Smallest overview first, then one feature at a time.
3. **Label findings** OBSERVED / INFERRED / UNKNOWN with the source screenshot.
4. **Data**: each table and its fields, and which screen creates, changes or shows it.
5. **Re-check the list**: answered / partly / open. For each open item, say exactly what to click, record or screenshot next. Do not call it complete while items are open.
6. **Build spec** under the heading **"Build this"**: plain steps an app builder can follow; observed behaviour separate from new design choices (own name, colours, words).

Output: checklist with status, findings table (feature | finding | label | source), data model, "Build this" spec. Offer to continue into the Full track.

---

## Phase 1 — Recon (Study)

**1a. Sources table** (URL on every row), in order of value: help center/docs (most complete feature list + settings), pricing page (what they gate = what matters), changelog, store listing (screens, pitch, ratings), public walkthrough videos, marketing site, the user's own account (every state, user-driven), public API docs (data model nearly free).

**1b. Route the target** (Deep mode only for inside-reads; use the live tool list and schemas over this table):

| Target | Clean-room start | Deep start (REA / Craft Anything tools if connected) |
|---|---|---|
| Website / web app | screenshots at 390, 768, 1440 px; visible text; measured layout, fonts, spacing; menus opened | browser observation (`list_browser_targets`, `capture_browser_scenario`), JS bundle analysis (`analyze_javascript_application`, `analyze_web_bundle`) |
| Electron app / ASAR | window screenshots | `analyze_javascript_application`; check `inspect_electron_fuses` before inspector attempts |
| Android APK | store listing + own device screenshots | `inspect_android_package`, `decode_android_resources`, ADB tools |
| iOS / macOS app | store listing + screenshots | `open_binary`, plist/Interface Builder/asset catalog tools |
| Native exe/library | screenshots + docs | `open_binary` → `binary_overview` → `analyze_function` / strings / pseudo-code |
| .NET, Go, Rust, WASM, firmware, SQLite, captures | docs + screenshots | the matching `inspect_*` tool |
| Game | recorded play sessions: rules, controls, win/lose, scoring, levels, timings | only for games the user owns/open source |
| Two versions | screenshots of both | `compare_application_versions`, `find_changed_behavior` |

If REA tools are missing but needed: run `rea doctor`, show `rea setup --dry-run` plan, apply only after the user agrees, then ask them to restart the client. Runtime tools that execute the target or change a device need the user's explicit OK. Close native sessions (`close_binary`) when done.

**1c. Screen inventory** — stable IDs S01, S02…: `ID | screen | route/how to reach | purpose | key components | states seen` (empty, loading, filled, error, permission denied, mobile). An unrecorded empty state is an unbuilt empty state.

**1d. User flows** — F01, F02…: goal + screens passed + edge cases. Count clicks on the happy path: that is the number to beat.
```
F01 Guest books a meeting
    S07 booking page -> S08 pick a time -> S09 details -> S10 confirmed   (4 clicks)
    edge: no slots this week, time zone differs, slot taken mid-form
```

**1e. Components** — every repeated UI part: name, variants, states, screens used.

**1f. Inferred data model** — entities, fields, relations, each with evidence and confidence (high/medium/guess).

**1g. Feature matrix** `features.csv`: `feature,area,priority(must/should/could),original(yes/no),clone(no),notes`.

**1h. What cannot be cloned** — `skip` rows with reasons: licensed content (catalogues, stock libraries), the network and its users, data it owns, partner deals, hardware, regulated licences (banking, health, insurance).

**1i. Size it honestly**: S (weekend), M (few weeks), L (quarter), XL (rescope). Name the three hardest parts. No promise of a perfect clone.

Recon summary: core loop, screen/flow counts, three hardest parts, out of scope, next step.

---

## Phase 2 — Architect

- **Stack**: use what the user knows. Otherwise boring, managed, cheap at zero users, one line of why each: Next.js + TypeScript, Tailwind, Expo for mobile, Postgres (Supabase/Neon), Drizzle/Prisma, Supabase Auth, Stripe or Razorpay (India), Resend, Vercel/Cloudflare. One database, no microservices. Desktop: the user's preferred stack (e.g. Python + PySide6, C#/WPF, Tauri).
- **Schema** (real SQL): uuid ids, `created_at/updated_at`, owner column on owned rows, decided `on delete` rules, indexes on FKs and filter/sort columns, check constraints for status, `timestamptz` in UTC, money as integer minor units + currency, access rules (RLS or one auth check per query — write which). Hard invariants (e.g. no double booking) are database constraints, not UI checks.
- **API**: per flow, `method path | does | who | input | output | flow`; webhooks in/out; jobs with schedules.
- **Parts that bite**: time zones/DST, idempotency, races, rate limits, file limits, search, realtime, offline, email deliverability, multi-tenancy, data deletion (GDPR/DPDP).
- **Build order**: vertical slice → must-haves → should → could → fixes from Phase 10. Each milestone lists S-IDs, tables, routes.

Write `recreate/architecture.md` + `schema.sql`.

---

## Phase 3 — Design system

Rebuild the **system**, not the skin. Measure from screenshots, do not guess:
- **Colour roles** (bg, surface, border, text, text-muted, accent, on-accent, danger, success, warning); count real greys (usually 5–7). Record their brand colour as role `accent` with a neutral placeholder.
- **Type scale** (e.g. 12/14/16/20/28/40), weights, line heights; note font *category*, swap licensed fonts for open ones (Inter, Manrope, IBM Plex, Noto for Indian scripts).
- **Spacing** (4 or 8 base), radius, shadow, motion (2–3 each), layout (max width, grid, breakpoints, sidebar, header).
- Tokens in `tokens.json` → CSS variables → Tailwind theme. Components use tokens only, never raw hex/px.
- **Contrast**: WCAG AA floor — 4.5:1 body text, 3:1 large text, input borders, focus rings. Fix in tokens.
- **Component specs**: variants, sizes, states (default, hover, active, focus-visible, disabled, loading, error, empty), tokens, a11y, used-on.
- Icons from open sets (Lucide, Phosphor, Tabler); own illustrations. Never trace theirs.
- Build primitives in isolation (`/design` route) before screens.

---

## Phase 4 — Build

- **Clean room**: every line written here from recon + specs. Never paste their HTML/CSS/JS/SVG/images, never load from their domain/CDN, never "view source and adapt". Matching what a button does is parity; matching its sentence is copying.
- **Shell**: routes for every screen (stubs OK), layout, tokens, primitives, seed data. Commit.
- **Vertical slice**: the core loop end to end, ugly but working. Use a fake data layer with the real function signatures if the backend is not ready.
- **Screen by screen**, per S-ID: read its recon row → look at reference for layout/hierarchy only → build with primitives → every state (empty, loading, filled, error, no permission, 60-char content, mobile) → semantic HTML, labels, keyboard, focus, alt text → update `features.csv` → screenshot into `clone-screens/` at the reference viewport → one commit per screen.
- **Done per screen**: all states; works at 390 and 1440 px; keyboard-only completes the flow; no console errors; no borrowed copy; matrix updated; screenshot saved.
- **Games**: rules engine separate from rendering; deterministic seedable logic; a self-test that plays scripted inputs and asserts score/state.
- Keep `build-log.md`. When something is bigger than it looked, say so; never quietly ship half.
- Stuck on behaviour? Go back to the original *as a user* (help article, walkthrough, own account), not its code.

---

## Phase 5 — Backend

- Auth: email + verification, reset, magic link/OAuth with the user's own developer apps; http-only secure cookies; roles via one `can(user, action, record)` function; real account deletion.
- DB: checked-in migrations, access rules on every table — test that a second user gets nothing. Seed with fake people only. Backups on.
- Payments: hosted checkout + customer portal (Stripe/Razorpay); verify webhook signatures, store event ids, idempotent handlers; subscription status lives in your DB; one-click cancel.
- Email from your own domain; jobs with retries and a dead-letter log; UTC stored, local shown.
- Integrations: official API, fewest scopes, note review processes (e.g. Google OAuth verification takes weeks — start early).
- **Security checklist**: secrets only in env (`.env*` git-ignored), server-side validation on every route, authz on every read/write, rate limits on auth and anything that sends email/SMS, signed webhooks, upload limits on a separate bucket/domain, no user data in URLs/logs, dependency audit, privacy policy listing every processor. Test mode until deploy.

---

## Phase 6 — Test

- **Plan** per flow: happy path (H), edge cases (E), negative cases (N), numbered F01-H1, F01-E3…
  Edge list for every flow: empty / very long / emoji & Indic text input, two tabs, double submit, back and refresh mid-flow, slow network, offline, expired session, second user's data invisible, time zones & DST, mobile width, keyboard only, screen-reader labels. Negatives: wrong password, declined test card, permission denied, deleted record.
- **Automate** with Playwright against local dev + seed data; role/label selectors, never CSS classes; fail on console errors and any 5xx; axe accessibility scan per screen.
- **Manual pass** for emails, real OAuth, payments end to end, visual glitches (drive the local build with a browser tool if available, else give the user a checklist).
- **Bugs** in `bugs.md`: ID, severity, steps, expected, actual, evidence. S1 data loss/security/payments wrong/core flow blocked; S2 feature broken no workaround; S3 workaround exists or visibly wrong; S4 cosmetic. Only reproduced bugs; "might be" goes to a to-check list.
- **Fix loop**: S1/S2 first; failing test → fix → pass → keep test; re-run suite per batch.

---

## Phase 7 — Check (parity)

**Parity = it does the same job, not that it looks the same.**

- **Feature score**: weights must 3, should 2, could 1; credit yes 1, partial 0.5, no 0; exclude `skip` rows and rows with `original=no` (your additions).
  `score = 100 × Σ(weight × credit) / Σ(weight)`. Report must-haves done/total and the weakest areas first, missing list in build order.
- **Layout score** per key screen: same viewport (1440×900, 768×1024, 390×844), same state and data shape. Compare structure (edge/position of blocks, hierarchy), deliberately ignoring colour so the rebrand does not count against you. Bands: 90+ matches, 75+ close, 50+ partly, below different. Report differing regions biggest first and page-height difference. Use pixel mode only for your own regressions. (If the Replica tools are installed: `parity.py`, `imgdiff.py`.)
- **Behaviour diff**: per flow — clicks to finish, error handling, what is remembered, what emails arrive. Write `flow | original does | clone does | fix or keep`. Fewer clicks is a win.
- **Verdict**: *not shippable* (any must-have missing or open S1) / *shippable* (all must-haves, feature 80+, no open S1/S2) / *better than the original* (shippable + Phase 10 fixes — the real goal; a straight copy has no reason to exist). Honest numbers: 62% is 62%.

---

## Phase 8 — Refine loop (Ready)

Study → Build → Check repeats until the verdict is reached or the user stops it. Each loop: take the top five gaps from Phase 7, form a hypothesis per gap with a predicted result, build, re-check, record findings. Then show the result (open/run/play/preview) and ask what to change. Before any upload/deploy, show a preview and get the user's final decision.

---

## Phase 9 — Investigation close-out

Mark every plan step done/blocked; every conclusion matches a recorded finding; list remaining unknowns with what would resolve them; write `handoff.md`. Do not describe the job as complete while required questions are open.

---

## Phase 10 — Entrepreneur (optional; great to run first on an idea)

- **Collect** 100+ real reviews from 3+ sources, recent first: App Store (official RSS `https://itunes.apple.com/us/rss/customerreviews/id=<APP_ID>/sortBy=mostRecent/json`), Google Play, G2/Capterra/Trustpilot, Reddit ("X alternative", "switched from X", "X vs"), Hacker News (Algolia API), its public feature board and changelog. Read 3–4 star reviews too ("love it, but…"). Read pages like a person; official feeds/APIs within their terms only.
- Each row: `source,url,date,rating,text` verbatim. Drop rows without a link.
- **Rank** into themes; weight low ratings and recency; mark themes with <3 reviews or one source as **thin**; read unmatched low ratings by hand.
- **Three lists**: what they hate / what is missing / what is unsolved (whole groups ignored → positioning). Each with counts, sources, 1–2 linked quotes.
- **Fix plan**: top 5–8 by evidence × cheapness; size; add to `features.csv` with `original=no`.
- **Angle**: `For {who} who {pain}, {your app} {does this instead}. Evidence: {theme}, {n} reviews, {n} sources.` Recommend one.
- Never fake reviews, never use reviewer words as testimonials, state the sample size.

---

## Phase 11 — Brand (mandatory before launch)

- **Name**: 20 candidates (descriptive, compound, invented, metaphor, verb; Indian/Sanskrit roots welcome), cut to 5: not confusingly similar to the original or category peers in sound, look or meaning; short, spellable; fits the angle.
- **Checks, run not assumed** (mark "to run" or result + date): India trademark (IP India public search, classes 9/42), USPTO, EUIPO/TMview, WIPO Global Brand DB, domain whois, App Store/Play name search, social handles, web search "name + category". Screening only, not legal clearance.
- **Palette**: new primary hue from a different family than theirs; same token roles; contrast AA passes.
- **Logo brief** (not a logo): idea, mark type, works at 16 px and 1024 px, deliverables (SVG, 1024 app icon, favicon set, 1200×630 OG); must not resemble their mark.
- **Voice**: three words with what each does not mean, five do/don't pairs; rewrite the 10 most-seen strings fresh.
- **Sweep**: search contents and file names for the original's name (also inside identifiers like `OriginalEmbed`), domains and brand colours, skipping `node_modules`, build output and `recreate/`. Fix until clean (Replica `sweep.py` if installed; else `grep -rniE "name|domain|#hex"`). Check by eye: favicon, titles, emails, OG image, app icon.

---

## Phase 12 — Launch

- **Landing**: hero = the angle + one button + real product screenshot; the problem (top two hate themes, paraphrased); how it works (3 steps); features led by fixes; pricing; FAQ with real objections; final CTA. No fake proof, no invented counts, no "trusted by" rows.
- **Pricing**: their public pricing + 2–3 alternatives with URL and date read; billing complaints with counts; at most 3 tiers named by who they are for; annual ≈ 2 months free; fix billing pain in product. Consider ₹ pricing and UPI for Indian users.
- **Store listing** limits — App Store: name 30, subtitle 30, promo 170, keywords 100, description 4000; Play: title 30, short 80, full 4000. No ranking/price claims in short fields, no wasted keyword characters, **original's name nowhere**. Apple Guideline 4.1 (Copycats): make your fixes and brand visible in screenshots and first lines.
- **Launch plan**: waitlist, analytics + error tracking, the communities where unhappy users talk, a Product Hunt/HN post leading with the fix, the first 10 users talked to by hand.

---

## Phase 13 — Deploy (gate)

**Preflight — any failure stops the deploy:** tests green; parity must-haves done; brand sweep clean; listing lint passes; production build passes; no open S1/S2; privacy policy and terms live (every processor listed); cookie banner if needed; account deletion works; favicon/titles/OG are yours. Show results and ask for the go.

Then: separate production DB with backups and migrations run by deploy; production env vars matching `.env.example`; payments to live mode (recreate products, live webhook secret, one real purchase refunded); OAuth production redirect URIs; verified sending domain. Host (Vercel/Netlify/Cloudflare Pages/Render); DNS the user sets: `A @ → host IP`, `CNAME www → host target`, verification TXT; email SPF, DKIM, `DMARC v=DMARC1; p=none; rua=mailto:…` tightened later; one canonical host; HTTPS checked. Monitoring: error tracking, uptime on home + core flow, alerts. Mobile: `eas build` / `eas submit` to TestFlight and Play internal testing; the user owns developer accounts. Write `recreate/deploy.md`.

---

## Ethics check (Dhamma lens: non-harm, honesty, right livelihood)

Before building, ask once: does this version help people more than the original (a real fix, a neglected group, a fairer price)? Decline or rescope projects whose purpose is deception (phishing look-alikes, fake receipts or reviews, impersonating a real brand), gambling/betting, or harming a private person. Prefer local-first, privacy-respecting, accessible designs. A clone with no improvement and no new audience has no reason to exist.

## Finish

Report plainly: track and mode used, what was built or specified, parity verdict with real numbers, open unknowns, and one next step. This is general information, not legal advice; for money on the line, a trademark/IP lawyer should review before launch.
