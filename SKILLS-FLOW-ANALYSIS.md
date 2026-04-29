# Taqtics Skills Flow Analysis: The Demo-Perfection Pipeline

**Status:** 25 skills analyzed, gates mapped, pipeline defined  
**Target:** Orchestration skill `/demo-perfection-pass` design spec  
**Date:** 2026-04-28

---

## I. The 25 Skills Inventory

### Audit & Research Phase (3)

**1. audit**  
Purpose: Full prospective client audit pipeline. Domain → PDF script + market intel.  
Triggers: `audit [domain]`, `audit [firm]`  
Inputs: Firm domain, DMA, practice area  
Outputs: `audit-script.md`, branded PDF, tech stack, SEO data, market data  
Gate: Entry skill. Produces audit-script.md → feeds gates 2-5.  
Pipeline: AUDIT phase (entry)

**2. taqtics-meta-messaging**  
Purpose: Messaging architecture system. Reader-state → tagline → hero → channel map.  
Triggers: `messaging`, `build messaging`, `brand positioning`  
Inputs: audit-script.md, reader-state context, competitor language audit  
Outputs: Tagline candidates (5x Diamond-scored), 6-unit messaging stack, channel handoff map  
Gate: Gate 2 (runs after audit). Feeds creative-director, voice-builder, figma-brand-preview.  
Pipeline: DESIGN phase  
**Lessons:** Reader-State Rules + Concept-Over-Label must run before Figma. Skipping to Figma without messaging = placeholder work (McConathy fail 2026-04-27).

**3. voice-builder**  
Purpose: Reusable voice profile for firm. Intake copy → patterns → validation → skill doc.  
Triggers: `voice profile`, `build voice`, `what does [firm] sound like`  
Inputs: Copy samples (6+ sources: homepage, blogs, attorney bios, social, video, reviews)  
Outputs: `voice-profile.md` with 9 sections (summary, attributes, tone-by-context, vocab, syntax, CTA rules, positioning, tagline candidates)  
Gate: Gate 4 (runs after creative-director if 3+ named authors). Feeds all copy work downstream.  
Pipeline: DESIGN → CODING phase  
**Lessons:** Brand vs founder voice are distinct. Pattern recognition catches rhythm + posture shifts. Human validation (Jared) required before locking.

### Design Orchestration & Brand (4)

**4. figma-brand-preview**  
Purpose: 16-section Figma brand exploration. Transforms audit → visual deck.  
Triggers: `brand preview`, `figma build`, `transformation deck`  
Inputs: audit-script.md, messaging stack (Gate 2), creative direction (Gate 3), voice rules (Gate 4)  
Outputs: Figma file (URL + fileKey to `figma.md`), `editorial-system.md`, image assets (scenes, logos, attorneys)  
Gate: Gate 5 (final design gate). Autonomous gate progression fires after audit via `post-audit-handoff.py`.  
Pipeline: DESIGN → handoff to CODING  
**Critical lessons:**  
- Single page only. Never multi-page (persistence bug confirmed).  
- Position to right of existing media, never overlap Jared's drops.  
- Inter font inside plugin calls only (custom fonts fail silently).  
- Visual deck, not text-dense report. Dark backgrounds + card grids dominate.  
- Five Taqtics surfaces always render: CTV, social, editorial, design, 10ft contrast.  
- Verify persistence after major writes (child.length check).

**5. creative-director**  
Purpose: Brand positioning + CTV concept dev + 3-pillar framework.  
Triggers: `creative direction`, `positioning`, `CTV concept`, `brand DNA`  
Inputs: audit-script.md, messaging stack (Gate 2), market position  
Outputs: Brand DNA, positioning statement, 3 pillars, AGAINST/FOR framework, voice rules  
Gate: Gate 3 (runs after taqtics-meta-messaging). Feeds voice-builder, figma-brand-preview.  
Pipeline: DESIGN phase

**6. ctv-general**  
Purpose: CTV 30-second spot production (5-scene arc). Gemini images → Veo video → 11Labs VO → Suno soundtrack.  
Triggers: `CTV spot`, `produce CTV`, `video production`, `emotional arc`  
Inputs: Scene formulas (from creative-director), firm positioning, VO script  
Outputs: Image sequences (5x Kodak/Fuji stock sims), video clips, voiceover MP3, soundtrack  
Gate: Runs during DESIGN (part of ctv-general pipeline). Images feed figma-brand-preview.  
Pipeline: DESIGN phase

### Mobile & Conversion Audits (6)

**7. cro-audit**  
Purpose: Mobile CRO + UX audit. Touch targets, button positioning, fold, forms, safe-area.  
Triggers: `mobile audit`, `CRO review`, `UX pass`, `check mobile`  
Inputs: Client site URL, context  
Outputs: JSON audit report per page, fix list ranked by severity  
Gate: Sub-skill of cro-ux-director (runs in parallel with 5 others).  
Pipeline: AUDIT / RESEARCH phase (can run anytime)

**8. accessibility-audit**  
Purpose: WCAG 2.2 AA compliance scan. Semantic HTML, ARIA, keyboard nav, contrast, alt text.  
Triggers: `accessibility audit`, `WCAG`, `A11y pass`, `ADA review`  
Inputs: Client site URL, brand palette (for contrast baseline)  
Outputs: JSON a11y report, per-page fix list with WCAG criterion refs  
Gate: Sub-skill of cro-ux-director (runs in parallel with 5 others).  
Pipeline: AUDIT / RESEARCH phase

**9. form-optimization**  
Purpose: Lead-form conversion science. Field count, progressive disclosure, autofill, validation.  
Triggers: `optimize form`, `form friction`, `why arent leads converting`, `multi-step`  
Inputs: Form HTML, context, legal vertical rules  
Outputs: JSON form audit, field-level rewrite suggestions  
Gate: Sub-skill of cro-ux-director (runs in parallel with 5 others).  
Pipeline: AUDIT / RESEARCH phase

**10. copy-audit**  
Purpose: Body copy + CTA + headlines + trust language audit. Voice rules, scannability, legal compliance.  
Triggers: `audit copy`, `rewrite hero`, `check CTAs`, `tone review`, `voice audit`  
Inputs: Page URL, client voice profile (optional), brand baseline  
Outputs: JSON copy audit, per-page fix list with severity/pattern tags  
Gate: Sub-skill of cro-ux-director (runs in parallel with 5 others).  
Pipeline: AUDIT / RESEARCH → CODING (fixes ship alongside code)

**11. trust-signals-audit**  
Purpose: Legal E-E-A-T audit. Results, testimonials, bar admissions, awards, bylines, fake-trust flags.  
Triggers: `audit trust`, `credibility review`, `E-E-A-T check`, `testimonial audit`  
Inputs: Client site URL, attorney roster  
Outputs: JSON trust audit, per-section fix list, fake-trust flags  
Gate: Sub-skill of cro-ux-director (runs in parallel with 5 others).  
Pipeline: AUDIT / RESEARCH phase

**12. performance-audit**  
Purpose: Core Web Vitals (LCP, INP, CLS) + Lighthouse + CrUX real-world data.  
Triggers: `performance audit`, `Core Web Vitals`, `why is this slow`, `Lighthouse`  
Inputs: Client site URL  
Outputs: JSON perf audit, CrUX field data, PSI lab data, bottleneck list  
Gate: Sub-skill of cro-ux-director (runs in parallel with 5 others).  
Pipeline: AUDIT / RESEARCH → CODING

**13. cro-ux-director**  
Purpose: Meta-orchestrator. Runs all 6 audits in parallel, synthesizes 1 ranked fix roadmap.  
Triggers: `full audit`, `complete CRO/UX review`, `swarm audit`, `run full expert stack`  
Inputs: Client site URL(s), or client slug for sweep  
Outputs: Unified JSON audit (composite score + 6 dimension scores + deduped priority fixes), quick-wins list  
Execution modes: Single URL, Client sweep (10-15 pages), Cross-site sweep (all 4 clients)  
Weighted scoring: perf 1.5x, form 1.5x, trust 1.3x, a11y 1.2x, cro 1.0x, copy 1.0x  
Gate: Meta-skill. Orchestrates 7-12 as parallel child processes.  
Pipeline: AUDIT / RESEARCH phase (can run anytime, any URL)

### Content & Copy (5)

**14. blog**  
Purpose: Full blog pipeline. Keyword → outline → draft → publish.  
Triggers: `publish blog`, `blog [topic]`, `content [keyword]`  
Inputs: Topic, keyword intent, client context  
Outputs: Published article, internal links, metadata  
Pipeline: CODING phase (content refresh)

**15. copy-audit** (duplicate listed above, listed once here for completeness)

**16. proposal**  
Purpose: Generate client proposal.  
Triggers: `proposal`, `generate proposal`  
Inputs: Client data, scope  
Outputs: Proposal PDF  
Pipeline: Pre-AUDIT (prospect stage)

**17. guide-chapter**  
Purpose: Create or optimize guide chapter.  
Triggers: `guide [topic]`, `chapter optimization`  
Inputs: Guide framework, chapter outline  
Outputs: Optimized chapter  
Pipeline: CODING phase

**18. linkedin-post**  
Purpose: Create + post LinkedIn content (voice-compliant).  
Triggers: `post linkedin`, `linkedin content`  
Inputs: Topic, voice rules  
Outputs: Posted content  
Pipeline: CODING phase (content distribution)

**19. x-post**  
Purpose: Create + post X/Twitter content (voice-compliant).  
Triggers: `post x`, `twitter [content]`  
Inputs: Topic, voice rules  
Outputs: Posted content  
Pipeline: CODING phase (content distribution)

**20. og-images**  
Purpose: Generate OG images + featured images.  
Triggers: `og images`, `featured image`  
Inputs: Article metadata, brand palette  
Outputs: OG image set (social, landing page variants)  
Pipeline: CODING phase

### Logo & Visual Design (3)

**21. figma-logo-explore**  
Purpose: Logo mark exploration grid (icon variants, layouts, case, dark/light).  
Triggers: `logo exploration`, `mark studies`, `design logo`  
Inputs: Brand direction, symbol concepts  
Outputs: Figma frame with 20+ logo variations  
Gate: Entry to logo system. Feeds figma-logo-finalize.  
Pipeline: DESIGN phase

**22. figma-logo-finalize**  
Purpose: Winner → asset pack (lockups, colorways, favicon set, brand sheet PDF).  
Triggers: `finalize logo`, `lock mark [X]`, `logo asset pack`  
Inputs: Winning logo mark from exploration grid  
Outputs: Master lockups, orientation variants (square/wide/vertical), colorways (5), favicon set (5 sizes), brand sheet PDF  
Gate: Runs after figma-logo-explore winner picked.  
Pipeline: DESIGN → handoff to CODING

**23. seo**  
Purpose: SEO optimization, internal linking (RELINK), keyword scoring, technical fixes.  
Triggers: `SEO audit`, `relink`, `keyword scoring`, `technical SEO`  
Inputs: Site audit, keyword universe, technical crawl  
Outputs: JSON recommendations, internal link map, technical fix list  
Pipeline: AUDIT / RESEARCH → CODING

### Operations & Infrastructure (4)

**24. apollo**  
Purpose: Apollo CRM ops (contact lookup, enrichment, sequence, outreach).  
Triggers: `apollo [lookup]`, `outreach sequence`  
Inputs: Contact query, campaign data  
Outputs: Enriched contact data, sequence status  
Pipeline: Pre-AUDIT (prospect research)

**25. helm**  
Purpose: Master orchestrator for OpenClaw. Coordinates 8 agents for nightly campaigns.  
Triggers: `helm`, `master orchestrator`, `nightly routine`  
Inputs: Campaign config, agent state  
Outputs: Autonomous campaign execution (research → produce → optimize → distribute)  
Pipeline: Parallel to main audit→design→coding pipeline (separate infrastructure)

### Routers & Global State (4 bonus skills, not in 25 count)

**Where Are We**  
Purpose: Universal client-pipeline router. Reads `.client-state.json`, prints phase + task + next action.  
Triggers: `where are we`, `status`, `orient me`, `what's next`  
Inputs: `.client-state.json` (found by walking up 4 levels)  
Outputs: Orientation block (phase, current task, queue, locked decisions, paths)  
Gate: Front door for any session opened in a client repo.  
Pipeline: Universal entry point

**Client Bootstrap**  
Purpose: Set up new client repo for audit→research→design→coding pipeline.  
Triggers: `new client`, `bootstrap [slug]`  
Inputs: slug, firm-name, domain, market, practice, phase, repo-path  
Outputs: `.client-state.json`, `CLAUDE.md`, working directory structure  
Gate: First skill run on new client. Creates state file for `/where-are-we` to read.  
Pipeline: Pre-AUDIT (prospect setup)

**Board**  
Purpose: Show Taqtics pipeline board (inbox → doing → review → approved → done).  
Triggers: `board`, `pipeline status`  
Outputs: Current project status across all clients  
Pipeline: Operational visibility

**Mission Control Brief**  
Purpose: Rehydrate full Mission Control context (Helm infrastructure, agent state, nightly briefing).  
Triggers: `mission control`, `helm brief`, `nightly routine`  
Inputs: Spec docs, research artifacts, live state  
Outputs: Full context rehydration  
Pipeline: Helm infrastructure only

---

## II. The Demo-Perfection Pipeline

### Goal
Verify any homepage demo or live URL through a 4-skill orchestration pass:

```
copy-audit → taqtics-meta-messaging (validate) → voice-builder (check consistency) 
→ cro-ux-director (full 6-dimension swarm) → unified ranked fix roadmap
```

### Entry Point: `/demo-perfection-pass`

**Triggers:**
- `demo perfection [URL]` / `demo perfection pass [domain]`
- `validate demo [firm]` / `homepage check [URL]`
- `preflight [slug]` / `go/no-go [domain]`

**Inputs:**
```json
{
  "url": "https://mcconathy.com/ or /contact/ or relative path",
  "clientSlug": "mcconathy-law (optional, auto-detect if .client-state.json exists)",
  "forceVoiceCheck": true,
  "mode": "quick (5 min) or full (20 min)"
}
```

**Outputs:**
```json
{
  "passDate": "2026-04-28T14:32:00Z",
  "passStatus": "PASS|WARN|FAIL",
  "passScore": 82,
  "dimensionBreakdown": {
    "copy": { score: 88, issues: 2 },
    "voice": { score: 76, issues: 4 },
    "cro_ux": { score: 82, compositeScore: 82 }
  },
  "blockers": [],
  "quickWins": [],
  "readinessForDemo": "GO",
  "clientStateAdvanced": true,
  "reportPath": "clients/[slug]/demo-preflight/YYYY-MM-DD-[page].json"
}
```

### Execution Flow

1. **Route to /where-are-we** (100ms)  
   - Load `.client-state.json` if available
   - Print current phase + task
   - Confirm we're not skipping gates
   
2. **Copy Audit (3min)**  
   - Fetch URL (desktop + mobile UA)
   - Score against 13 anti-patterns + scannability rules
   - Extract: banned words, em-dashes, uncontracted prose, CTAs, voice fit
   - Output: `demo-preflight/copy-audit.json`

3. **Voice Validation (2min, conditional)**  
   - If `voice-profile.md` exists in `clients/[slug]/`: load it
   - Check page copy against documented voice rules
   - Flag deviations (sentence length, contraction ratio, register shift)
   - Output: `demo-preflight/voice-check.json`

4. **CRO/UX Director (15min, parallel)**  
   - Spawn 6 audits in parallel (cro, a11y, form, copy, trust, perf)
   - Aggregate → dedupe fixes → rank by severity × weight
   - Output: `demo-preflight/cro-ux-unified.json`

5. **Synthesize Report (1min)**  
   - Merge copy + voice + cro-ux outputs into one report
   - Calculate pass/warn/fail thresholds:
     - **PASS:** Composite score ≥ 80, zero blockers
     - **WARN:** 70-79, ≤ 3 blockers
     - **FAIL:** < 70 or any critical-severity blocker
   - Surface 3 highest-impact quick wins
   - Output: `demo-preflight/YYYY-MM-DD-[page].json`

6. **Advance Client State (1min, conditional)**  
   - If `phase: design` + `currentTask.skill: figma-brand-preview` + pass ≥ 80:
     - Write `phase.lastAdvanced` timestamp
     - Move to `currentTask: T001, Prepare coding queue`
     - Advance phase to `coding`
   - If FAIL: flag for re-audit before proceeding

### Decision Matrix

| Composite Score | CRO-UX Issues | Voice Blockers | Copy Blockers | Recommendation |
|---|---|---|---|---|
| ≥ 85 | 0 | 0 | 0 | PASS – ready to demo |
| 80-84 | ≤ 2 minor | 0 | 0 | PASS – minor fixes post-demo |
| 70-79 | 2-5 mixed | ≤ 1 | 0 | WARN – prioritize top 3 fixes |
| 60-69 | ≥ 5 or 1 critical | ≥ 1 major | ≥ 1 | FAIL – rework before demo |
| < 60 | any critical | any | any | FAIL – major rework required |

---

## III. Client State Integration

### The `.client-state.json` Contract

Location: `[repo-root]/.client-state.json` (created by `/client-bootstrap`)

**Required structure** (read `client-bootstrap/state-schema.md` for full spec):

```json
{
  "client": {
    "slug": "mcconathy-law",
    "firmName": "McConathy Law",
    "domain": "mcconathy.com",
    "market": "Dallas, TX (DMA #5)",
    "practice": "DWI / Criminal Defense / Family"
  },
  "phase": {
    "current": "coding",
    "completed": ["audit", "research", "design"],
    "started": "2026-04-15",
    "lastAdvanced": "2026-04-27"
  },
  "currentTask": {
    "id": "T004",
    "title": "Refine homepage hero stack",
    "skill": null
  },
  "queue": {
    "remaining": ["T004", "T005", "T006"],
    "done": ["T001", "T002", "T003"],
    "queueDoc": "clients/mcconathy-law/HANDOVER.md"
  },
  "lockedDecisions": [
    {
      "key": "tagline",
      "value": "We Fight. We Win.",
      "lockedAt": "2026-04-25",
      "lockedBy": "taqtics-meta-messaging (Gate 2)"
    }
  ],
  "paths": {
    "research": "~/Projects/taqticscom/clients/mcconathy-law/research/",
    "handover": "~/Projects/mcconathy-law/HANDOVER.md",
    "codingPrompt": "~/Projects/taqticscom/clients/mcconathy-law/coding-prompt.md"
  },
  "devServer": "localhost:4326"
}
```

### What Demo-Perfection-Pass Writes

After execution (if PASS ≥ 80):

```json
{
  "phase": {
    "current": "coding",
    "lastAdvanced": "2026-04-28T14:32:00Z"  // ← UPDATED
  },
  "currentTask": {
    "id": "T001",
    "title": "Prepare coding queue",
    "skill": null
  },
  "demoPerfectionPass": {
    "executedAt": "2026-04-28T14:32:00Z",
    "url": "https://mcconathy.com/",
    "passStatus": "PASS",
    "passScore": 82,
    "reportPath": "clients/mcconathy-law/demo-preflight/2026-04-28-homepage.json"
  }
}
```

If FAIL, **do not write** — return report + blockers, ask user to rerun after fixes.

---

## IV. Gap Analysis & Missing Pieces

### Connections That Work Clean
- **audit → taqtics-meta-messaging:** audit-script.md feeds messaging inputs directly ✓
- **taqtics-meta-messaging → creative-director:** Messaging stack → brand DNA ✓
- **creative-director → voice-builder:** Brand DNA + positioning → voice rules ✓
- **voice-builder → figma-brand-preview:** Voice profile feeds editorial system ✓
- **copy-audit ↔ cro-ux-director:** Copy audit is sub-skill, deduped in synthesis ✓

### Connections That Need Wrapper
- **audit → cro-ux-director:** No direct feed. Audit doesn't produce site URL context. **Wrapper needed:** demo-perfection-pass extracts domain, fetches URLs.
- **voice-builder → copy rewrites:** voice-profile.md exists but no skill currently enforces it on new copy. **Wrapper needed:** copy-audit should take optional voice-profile path, score against it.
- **figma-brand-preview → HANDOVER.md:** Figma outputs assets but no single handoff doc. **Wrapper needed:** figma-brand-preview should write or update `clients/[slug]/HANDOVER.md` with asset inventory.

### Skills Not in Main Pipeline
- **apollo, helm:** Prospect research + nightly infrastructure. Parallel to main pipeline, not blocking. ✓
- **blog, linkedin-post, x-post, og-images, seo, guide-chapter, proposal:** CODING phase utility. Can run anytime. ✓
- **figma-logo-explore / figma-logo-finalize:** Optional design branch. Only runs if new logo intended. ✓

---

## V. Proposed Architecture: Demo-Perfection-Pass Skill

### Purpose
Fast preflight validator for any homepage before live demo or final review. Single command, 20min, unified go/no-go + ranked fix roadmap.

### Skill Responsibilities

1. **Router** (leverages `/where-are-we`):
   - Load client state (if exists)
   - Confirm phase + current task
   - Refuse to run if locked decisions would be violated

2. **Fetch & Prepare**:
   - Resolve URL (full URL or slug → domain lookup)
   - Fetch both desktop + mobile viewports (Firecrawl)
   - Extract page title, H1, hero CTA, form count

3. **Parallel Audit Pipeline**:
   - Spawn 4 workers in parallel (copy, voice, cro-ux, trust-signals subset)
   - Timeout: 15 min for cro-ux, 3 min for copy, 2 min for voice
   - Collect JSON reports

4. **Synthesize**:
   - Merge all 4 reports into unified dimension scores
   - Dedupe overlapping issues
   - Rank by severity × client-context weight
   - Calculate pass/warn/fail

5. **Client State Advance**:
   - If pass ≥ 80: write updated `phase.lastAdvanced` + `currentTask`
   - If fail: log reason, surface blockers, ask for rerun

6. **Output**:
   - JSON report to `clients/[slug]/demo-preflight/YYYY-MM-DD-[page].json`
   - Terminal summary (pass status, top 3 issues, next action)
   - Return exit code: 0 (PASS), 1 (WARN), 2 (FAIL)

### Sample Invocation

```bash
/demo-perfection-pass mcconathy.com/
/demo-perfection-pass --slug mcconathy-law --url /contact/
/demo-perfection-pass --force-full-audit https://aeelaw.com/ --mode=full
```

### Tooling

**What it uses:**
- Skill: `/where-are-we` (state routing)
- Skill: `copy-audit` (sub-invoke with URL)
- Skill: `cro-ux-director` (sub-invoke in single-URL mode)
- Bash: JSON merge + dedup logic
- Read: voice-profile.md if exists

**What it doesn't do:**
- Does not invoke audit (too slow, assumes audit already run)
- Does not modify code (read-only)
- Does not require Figma access

---

## VI. Summary: 4-Phase Pipeline Map

| Phase | Entry Skill | Skills Run | Output | Next Phase Gate |
|---|---|---|---|---|
| **AUDIT** | `audit` | audit, ctv-general, apollo (prospect research) | audit-script.md, PDF, tech stack, market data, imagery | audit-script signed off + `clients/[slug]/` populated |
| **RESEARCH** | (folded into audit) | (audit outputs feed next phase) | keyword universe, competitor teardowns, work queue T001-T010 | agent-work-queue.md with ≥10 tasks |
| **DESIGN** | `taqtics-meta-messaging` (Gate 2) → `creative-director` (G3) → `voice-builder` (G4) → `figma-brand-preview` (G5) | All 4 + ctv-general for scene imagery | Taglines, brand DNA, voice profile, Figma deck, Kodak/Fuji image sequences | Figma URL shared + all decisions locked in state file |
| **CODING** | Read HANDOVER.md + coding-prompt.md | blog, copy-audit (rewrites), cro-ux-director (preflight), all 6 sub-audits (as needed), seo, og-images, proposal, linkedin/x-post, guide-chapter, figma-logo-* (if new logo) | Shipped pages on dev server, then prod | All queue tasks done → phase: done |

---

## VII. Orchestration Skill Dependencies

### Demo-Perfection-Pass Orchestration Tree

```
demo-perfection-pass
├── where-are-we                  (state load + phase check)
├── copy-audit                    (URL-scoped, 3min)
├── voice-builder                 (voice-profile load + validate, 2min)
│   └── (no sub-skills, reads existing profile)
├── cro-ux-director (single-URL)  (15min)
│   ├── cro-audit
│   ├── accessibility-audit
│   ├── form-optimization
│   ├── copy-audit (internal, dedupe with step 1)
│   ├── trust-signals-audit
│   └── performance-audit
└── JSON merge + state advance
```

### Failure Modes Documented

1. **figma-brand-preview persistence bug:** Writes to non-working page silently fail. Always verify `page.children.length` after major ops.
2. **Skip-gate failure:** Jumping to design without audit produces placeholder work (McConathy 2026-04-27).
3. **Skip-gate 2:** Going straight to Figma without taqtics-meta-messaging. Results in invented taglines instead of Diamond-scored candidates.
4. **Voice drift:** Not running voice-builder early enough. Copy consistency suffers in multi-author sites.
5. **Copy audit mode confusion:** Mode A (static, fast, free) misses passive voice %. Mode B (agent rewrite) needed for voice fit. Demo-perfection uses Mode A + optional voice-profile validation.

---

## VIII. Implementation Checklist

- [ ] Create `/demo-perfection-pass/SKILL.md` with orchestration logic
- [ ] Write `.client-state.json` read + write logic (leverage `/where-are-we`)
- [ ] Sub-invoke `copy-audit --client=[slug] --url=[path]` with timeout
- [ ] Sub-invoke `cro-ux-director --client=[slug] --url=[path]` in single-URL mode
- [ ] Optional: Load + validate voice-profile.md if exists
- [ ] Merge 4 JSON reports → unified dimension scores
- [ ] Dedupe overlapping issues (common: missing labels flagged by both a11y + form)
- [ ] Rank by severity × context-weight
- [ ] Calculate pass/warn/fail thresholds
- [ ] Write client state advance logic (conditional on pass ≥ 80)
- [ ] Output report JSON + terminal summary
- [ ] Test against mcconathy-law, aeelaw, mesowatchorg URLs

---

**End of Analysis**
