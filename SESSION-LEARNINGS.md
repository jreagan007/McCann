# Session Learnings, McCann Demo Build (2026-04-28)

The session that built the McCann homepage demo also dialed in the Taqtics agent flow for every future client. Captured here so the lessons don't drift.

## What we built

1. **Two new global router skills** at `~/.claude/skills/`:
   - `/where-are-we`: reads `.client-state.json`, prints phase + task + locks
   - `/client-bootstrap`: sets up new client repo for the pipeline

2. **Thirteen pipeline skills symlinked to global** so every Taqtics client repo can call them:
   audit, cro-ux-director, cro-audit, accessibility-audit, form-optimization, copy-audit, trust-signals-audit, performance-audit, taqtics-meta-messaging, creative-director, voice-builder, figma-brand-preview, ctv-general

3. **Master orchestration skill** `/demo-perfection-pass` at `~/.claude/skills/demo-perfection-pass/`. Single command runs copy-audit + voice-builder + cro-ux-director + trust-signals against any URL. Outputs unified PASS/WARN/FAIL with ranked fix roadmap.

4. **Two clients bootstrapped** into the pipeline:
   - McConathy Law (mid-pipeline, retroactive bootstrap, phase: coding, T004 next)
   - McCann Dillon Jaffe and Lamb (post-design bootstrap, phase: coding, demo built)

5. **McCann homepage demo** at `clients/mccann-injury-law/homepage-demo/`:
   - `index.html` (homepage with hero, ledger, 6 editorial cards, 6 practice areas, 7 attorney bench, E-E-A-T pillars, 5-step approach, CTA, footer)
   - `article-i95-verdicts.html` (full data-journalism piece, Robert byline, sources, related articles)
   - `logos/mccann-logo-dark.png` (488x86 wordmark)
   - `images/` (symlinked to parent dir)

6. **Skills analysis report** at `homepage-demo/SKILLS-FLOW-ANALYSIS.md` (569 lines, 25 skills inventoried, gates mapped, demo-perfection-pass spec defined). Authored by an Explore subagent in parallel while main thread built the demo.

7. **Demo preflight report** at `clients/mccann-injury-law/demo-preflight/2026-04-28-homepage.json`. PASS at 84. Five priority fixes listed, all post-demo polish.

## The flow we proved

```
new client signs
    /client-bootstrap [slug]                creates state file + working dir
    /audit [domain]                         produces audit-script + branded PDF
    /taqtics-meta-messaging                 tagline candidates + 6-unit messaging
    /creative-director                      brand DNA + 3 pillars + voice rules
    /voice-builder                          voice-profile.md per author
    /figma-brand-preview                    brand exploration deck
    [build phase] homepage-demo or Astro repo
    /demo-perfection-pass                   preflight, 4-skill swarm, GO/NO-GO
    show client                             ready to demo
    iterate based on feedback
    /where-are-we                           re-orient anytime, replaces reading 10 docs cold
```

Every gate has a state-file write. Every phase advances on its exit criterion. No more skip-gate failures (the McConathy 2026-04-27 lesson: jumping to Figma without messaging cost hours).

## Lessons from this session

### What worked

1. **Parallel agent dispatch saves time.** Sent the 569-line skills analysis to an Explore subagent while the main thread built the demo. Both finished within the same 20-minute window.

2. **Guardrails caught two real misses.** The em-dash hook + banned-word hook blocked the article HTML twice. First catch was an en-dash in the data table caption. Second was a banned word in body copy. Both real, both shipped clean after rewrite. Without the guardrail, both would have made it to a client review.

3. **State file as single source of truth.** Once `.client-state.json` exists, every future session can run `/where-are-we` and immediately know phase, current task, locked decisions, and paths. Replaces reading HANDOVER.md + CODING-AGENT-PROMPT.md + audit-script + brand-system + 4 other docs cold.

4. **Symlink approach for global skills.** Symlinking taqticscom skills into `~/.claude/skills/` instead of moving them keeps taqticscom canonical, makes them globally available, and stays reversible. Two minute setup, zero refactor risk.

5. **Static HTML demo beats Figma for "what will the site look like."** Real fonts render, real interaction works, real schema validates, mobile responsive is provable in the preview panel. Figma can't show any of those. Took ~3 hours to ship a homepage plus full article that any client can click through.

### What broke (and the fix)

1. **Brass on light backgrounds fails 10ft contrast.** The brand-system.md explicitly says "no raw brass text on paper" but I shipped section eyebrows, article-source labels, practice numbers, bench roles, and EEAT pillar numbers in brass on Newsprint. Jared caught it: "the gold on light bg sucks". Fixed by swapping all brass-on-light to navy with weight 700 to compensate. Brass stays for dark backgrounds only. Brass-bright stays for small text on dark only.

2. **Spec language leaked into demo copy attempt.** Initial reflex when reading `figma.md` was to pull "scored 44/50, 4 alternates, PRO/CON, red flags cut" type meta-commentary into the site itself. Jared called it: "dont accidentally poison the demo copy with instructional stuff from figma". Site copy must be production-ready prose, not deck-spec language. The Figma is documentation about the brand. The site IS the brand.

3. **Logo placeholder vs real export.** Built initial nav with an SVG bracket placeholder while waiting for Jared to export the real logo from Figma. He dropped it on Desktop, I copied it in, swapped both header and footer. Lesson: don't get fancy with CSS-art logos when the real asset is 5 minutes away. Just ask, build placeholder, swap.

4. **Voice profiles live in editorial-system.md as prose, not as voice-profile.md.** The 7 author voices are documented but not extracted into the voice-builder output format. Future demo passes can't auto-validate voice without the extraction. Flagged as priority fix #1 in the preflight report.

5. **Banned-word recursion.** First two drafts of this very file got blocked because the lessons section described banned-word incidents by NAMING the banned words. The guardrail does substring match, not context match. Lesson: when documenting banned-word lessons, refer to "a banned word" or "the L-word" rather than the actual term. The full banned list lives in CLAUDE.md, refer there.

### What's still missing

1. **No voice-profile.md per author.** Need to run `/voice-builder` against editorial-system.md to extract 7 individual profiles (Robert, Mark, Tim, Patrick, Tom, David, Mike).

2. **No live URL.** Demo is static HTML at `file://`. Performance audit (PSI/CrUX) and full Lighthouse can't run against `file://` paths. Once deployed to a real domain, rerun demo-perfection-pass with all 6 dimensions.

3. **5 of 6 article cards link to fragment IDs that don't exist** (`#article-roosevelt`, etc). Only the I-95 article is built out. The other 5 are placeholders pending content production.

4. **No form on demo.** PI sites need an intake form. Form-optimization audit was skipped. Add form to demo before client signoff.

5. **Build repo doesn't exist locally.** Static HTML demo is in `clients/mccann-injury-law/homepage-demo/`. Production needs a real Astro repo at `~/Projects/mccann-injury-law/` with Phase 0 / Phase 1 / etc. Decision pending: continue iterating in homepage-demo/ vs bootstrap full Astro now. GitHub remote at https://github.com/jreagan007/McCann.git ready for push.

## Recurring patterns to watch

1. **Em-dash temptation.** Default writing style wants em-dashes. The guardrail catches them, but the muscle memory takes effort. Replace with periods, commas, or restructure the sentence.

2. **Banned-word leakage.** Look at CLAUDE.md for the full list. Reach for plainer alternatives: room, sturdy, smooth, complete.

3. **Spec doc vs site doc confusion.** Figma deliverable docs (figma.md, brand-system.md) are MAPS of the brand for internal use. Site copy is the BRAND in production form. Keep them separate.

4. **Dropdown menus in nav need keyboard accessibility.** `:hover` alone fails keyboard users. `:focus-within` handles tab navigation. `aria-haspopup`, `aria-expanded`, `role="menu"` on dropdowns. Mobile needs a different pattern (no hover) but this demo is desktop-first for the demo conversation.

## What this session unblocks

Every Taqtics client signed from now on can hit this exact flow:

```bash
# Day 1
/client-bootstrap acme-law --firm-name "Acme Law Firm" --domain acmelaw.com --market "Tampa, FL" --practice "PI" --phase audit

# Day 1-3
/audit acmelaw.com                  # produces audit-script.md + branded PDF
/taqtics-meta-messaging             # gate 2: messaging
/creative-director                  # gate 3: brand DNA
/voice-builder                      # gate 4: voice profiles
/figma-brand-preview                # gate 5: deck

# Day 4
[build homepage demo, static HTML or Astro]

# Day 5
/demo-perfection-pass               # preflight swarm
[show client]
[iterate]
[deploy]
```

Same flow. Every client. No more re-inventing the plumbing per firm.

## File locations (durable references)

- Skills hub (canonical): `~/Projects/taqticscom/.claude/skills/`
- Skills hub (global, symlinked): `~/.claude/skills/`
- New skills shipped: `where-are-we`, `client-bootstrap`, `demo-perfection-pass`
- McCann demo: `~/Projects/taqticscom/clients/mccann-injury-law/homepage-demo/`
- McCann state: `~/Projects/taqticscom/clients/mccann-injury-law/.client-state.json`
- McCann preflight: `~/Projects/taqticscom/clients/mccann-injury-law/demo-preflight/`
- McConathy state: `~/Projects/mcconathy-law/.client-state.json` (committed in worktree)
- Skills analysis: `~/Projects/taqticscom/clients/mccann-injury-law/homepage-demo/SKILLS-FLOW-ANALYSIS.md`
- McCann GitHub: https://github.com/jreagan007/McCann.git (remote exists, awaiting first push)

End of learnings.
