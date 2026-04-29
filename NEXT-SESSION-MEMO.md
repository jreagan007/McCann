# MEMO: McCann homepage rebuild as legit live preview

**Paste this entire memo into a fresh session after `/clear`. Do not summarize, read it whole, then dispatch the swarm.**

You are continuing work on the McCann Dillon Jaffe and Lamb homepage demo. The previous session shipped a brand manifesto disguised as a homepage. Jared called it. The next pass rebuilds it as a working PI law firm site with the McCann editorial-led differentiator inside a real operational shell.

---

## 1. Where you are right now

- **Build repo:** `/Users/taqticlaw/Projects/mccann-injury-law/`
- **Working homepage:** `index.html` at root (the rebuild target)
- **Brand-preview backup:** `preview/index.html` and `preview/article-i95-verdicts.html` (the manifesto version Jared wants preserved as reference)
- **Live URLs:**
  - http://localhost:4324/ , currently serves the brand-preview content, swap to the rebuild after the swarm
  - http://localhost:4324/preview/ , serves the brand-preview manifesto for reference, leave intact
  - Python http.server already running, leave it alone
- **GitHub:** https://github.com/jreagan007/McCann (pushed, main branch)
- **Phase per `.client-state.json`:** coding
- **Latest state:** Wave 2 polish landed. 7 voice profiles extracted. Copy-audit skill updated to 20 anti-patterns. Brand preview moved to `/preview/`. Root homepage needs functional rebuild.

## 2. What's broken (the gap to close)

The current `index.html` reads as a brand exploration deck. Section heads are slogan h2s ("Every article is a case file", "Six lanes. Every one tried.", "How a case actually moves"). It pitches the firm instead of running as the firm's actual site.

Missing or wrong, all of which a working PI homepage has:

- **Intake form** (the most-converting element on every PI site, currently nowhere)
- **Real article metadata** (date, reading time, full byline anatomy with photo + name + role)
- **Testimonials** (with name, city, case type, photo)
- **Press strip** (Inquirer, Legal Intelligencer, Philadelphia Magazine, ABC6 logos)
- **Office locations** (map with 4 pins, hours, driving directions per office)
- **Hours of operation** ("we answer 24/7" plus the routing schedule)
- **Functional clickthroughs** (currently anchor links go nowhere, every practice/attorney link should resolve to a real sub-page or be honest about being a stub)
- **Live verdict feed** (currently 4 static cards, real sites have filterable grids)

Plus copy issues to clean:

- "Every one" repeats 4 times across the page (investigations sub, practice h2, eeat pillar #3, eeat pillar #4). Anti-pattern #11 at page scale.
- "Approach" section (5-step "How a case actually moves") reads as manifesto and probably belongs on a `/how-we-work/` sub-page, not the homepage.
- E-E-A-T pillar #4 label "Trial attorneys with bylines" if it has not already been refactored.
- Section h2s should demote to functional headings ("Recent results", "Latest investigations", "Our attorneys") with the brand voice moving into body copy.

## 3. Read these first, in this order

```
~/Projects/taqticscom/clients/mccann-injury-law/.client-state.json          (phase, locked decisions, paths)
~/Projects/taqticscom/clients/mccann-injury-law/audit-script.md             (full audit, market data, $200M+ verdict claims sourced)
~/Projects/taqticscom/clients/mccann-injury-law/research/money-keyword-positions.md   (McCann ranks 0/8 Philly PI money keywords, target list)
~/Projects/taqticscom/clients/mccann-injury-law/research/practice-car-accidents.md    (current site scrape, what they say now)
~/Projects/taqticscom/clients/mccann-injury-law/research/practice-medical-malpractice.md
~/Projects/taqticscom/clients/mccann-injury-law/research/practice-truck-accidents.md
~/Projects/taqticscom/clients/mccann-injury-law/research/contact.md         (current contact page, intake form pattern)
~/Projects/taqticscom/clients/mccann-injury-law/research/homepage.md        (current homepage scrape, reference the structure)
~/Projects/taqticscom/clients/mccann-injury-law/brand-system.md             (locked tokens, 10ft viewing rules, fighter visual language)
~/Projects/taqticscom/clients/mccann-injury-law/editorial-system.md         (7 author voices, content matrix)
~/Projects/taqticscom/clients/mccann-injury-law/figma.md                    (6-unit messaging architecture, locked tagline, brand DNA)
~/Projects/taqticscom/clients/mccann-injury-law/voice-profiles/             (7 voice-{slug}.md files, one per author)
~/Projects/taqticscom/clients/mccann-injury-law/demo-preflight/2026-04-28-homepage.json  (last preflight, PASS at 84)
~/Projects/taqticscom/clients/mccann-injury-law/homepage-demo/SESSION-LEARNINGS.md       (what worked, what broke, recurring patterns)
~/Projects/taqticscom/clients/mccann-injury-law/homepage-demo/SKILLS-FLOW-ANALYSIS.md    (569-line skills inventory + pipeline map)
~/Projects/mccann-injury-law/index.html                                                 (current homepage, what to rebuild)
~/Projects/mccann-injury-law/CLAUDE.md                                                  (build repo instructions, locked decisions)
```

## 4. The skills available, hit them

All listed in your session sidebar after `/clear`. Invoke as agent dispatches with explicit briefs:

| Skill | Use for |
|---|---|
| `/demo-perfection-pass` | Master orchestrator. Runs copy-audit + voice + cro-ux-director + trust-signals as a 4-skill swarm. Use after the rebuild. |
| `/copy-audit` | 20 anti-patterns now, including methodology dumps, jargon, corporate disclaimers, page-wide noun repetition. Use as a parallel worker. |
| `/taqtics-meta-messaging` | 6-unit messaging architecture (hero tagline, alts, positioning, proof, benefit, CTA). Use to validate each section. |
| `/voice-builder` | Loads voice-profile.md files. Use to validate every byline excerpt on the page against its assigned author voice. |
| `/cro-ux-director` | Spawns 6 parallel sub-audits (cro, a11y, form, copy, trust, perf). Single command, ranked unified fix list. |
| `/form-optimization` | Critical for the intake form you'll add. Lead-form conversion science, field count, progressive disclosure. |
| `/trust-signals-audit` | E-E-A-T audit. Validates real verdicts, real attorney bylines, real awards, no fake-trust. |
| `/where-are-we` | Re-orient any time. Reads `.client-state.json`, prints phase + task + locked decisions. |

## 5. Voice and cadence rules (non-negotiable)

**Cadence pattern (Jared's, applied page-wide):**
```
25 Years.
One Record.
One Call.
```
Three short ascending lines. Numerals digit-first. Declarative. No throat-clearing. No adjectives.

**McCann voice (per editorial-system.md, Robert McCann's section):**
- First person founder authority. "I pulled the verdict slips on every I-95 corridor case..."
- Restraint over performance. No bombast. No adjective stacks.
- Statute and verdict citations inline.
- Active voice. Never passive.

**Hard guardrails (PreToolUse hook will block):**
- No em-dashes or en-dashes anywhere
- No banned words (see CLAUDE.md global)
- No negation describing the firm ("we don't", "not a", "no [bad thing]")
- Numerals digit-first, not spelled out
- Contractions always
- Active voice
- Infer don't explain (cut every clause that spells out the previous clause's implication)
- Jargon civilians read literally is out (no "3 bars" for bar admissions, no "pleadings" without context)
- Cap any single noun at 2 page-wide instances unless it is the brand term
- 6 anti-patterns added 2026-04-28 to copy-audit, see `~/.claude/skills/copy-audit/SKILL.md` items 14-20

**Locked, never change:**
- Hero h1: `25 Years. / One Record. / One Call.`
- Color system: Independence Navy, Liberty Brass, Alert Crimson, Philly Newsprint, Keystone Slate
- Color rule: brass on dark only, navy weight 700 on light
- Typography: Anton + Inter + JetBrains Mono + Source Serif 4
- Logo: `logos/mccann-logo-dark.png` (488x86, dark-bg only, light-bg version pending)
- Tagline (long form): TWENTY-FIVE YEARS. ONE TRIAL RECORD.
- Verdict amounts and venues, attorney names + roles + bar admissions, all addresses, all schema

## 6. Dispatch this swarm

Send these in a single message (3 parallel agents) right after reading the source material in section 3.

### Agent 1: Functional homepage rebuild

```
Rebuild /Users/taqticlaw/Projects/mccann-injury-law/index.html as a working PI law firm homepage, not a brand pitch deck. Demote manifesto h2s to functional section headings:

- "Recent results" (replaces "The verdicts are the record")
- "Latest investigations" (replaces "Every article is a case file")
- "Practice areas" (replaces "Six lanes. Every one tried.")
- "Our attorneys" (replaces "They try the cases. They write the articles.")
- "How we work" (move 5-step approach to a sub-page or trim to 1-line)
- "Talk to a trial lawyer" (replaces "One call. A real lawyer.")

Add these new sections:
- 3-field intake form below hero (name, phone, what happened)
- Press strip (Inquirer, Legal Intelligencer, Philadelphia Magazine, ABC6) with logos pulled or placeholder marks
- Testimonials grid (3 testimonials with name, city, case type, photo placeholder)
- Office locations with map placeholder, 4 pins, hours
- 24/7 phone-routing eyebrow above footer

Move the McCann editorial-led differentiator to lead position but inside the operational shell. Keep voice rules from section 5 of NEXT-SESSION-MEMO.md. Keep all locked items.

Read /Users/taqticlaw/Projects/taqticscom/clients/mccann-injury-law/research/homepage.md and /Users/taqticlaw/Projects/taqticscom/clients/mccann-injury-law/research/contact.md to see the current site's existing patterns and forms before designing the new intake form.

Edit the file directly. Return a tight report of every section touched.
```

### Agent 2: Data-grounded keyword targeting

```
Read /Users/taqticlaw/Projects/taqticscom/clients/mccann-injury-law/research/money-keyword-positions.md. McCann ranks 0/8 in Philadelphia PI money keywords. The 8 keywords plus their volumes are listed in that file.

Update /Users/taqticlaw/Projects/mccann-injury-law/index.html so that every functional section head, hero copy, meta description, and JSON-LD knowsAbout array reflects the actual money keywords McCann should rank for, not generic "personal injury" terms.

Examples:
- Title tag should target "philadelphia personal injury lawyer" or "philadelphia injury law firm"
- Meta description should hit 2-3 money keywords naturally
- Practice cards should use the keyword phrasing (e.g. "philadelphia car accident lawyer" not "car and truck accidents")
- LegalService schema knowsAbout array should mirror the 8 money keywords

Don't keyword-stuff. Match the keyword phrase once per relevant section. Edit directly. Return a list of changes per section.
```

### Agent 3: Voice validation

```
Read all 7 files at /Users/taqticlaw/Projects/taqticscom/clients/mccann-injury-law/voice-profiles/.

For every byline excerpt on /Users/taqticlaw/Projects/mccann-injury-law/index.html (the 6 article cards in the Investigations section, plus any 1-line attorney bios in the Bench section), validate that the excerpt matches the assigned author's voice profile. Flag mismatches.

Voice profile assignments per article card:
- Card 1 (I-95 verdicts) is Robert E. McCann, see voice-robert-mccann.md
- Card 2 (Roosevelt Boulevard) is Thomas J. O'Malley, see voice-thomas-omalley.md
- Card 3 (SEPTA FELA) is Michael P. Minuti, see voice-michael-minuti.md
- Card 4 (Commodore Barry Bridge) is Timothy A. Dillon, see voice-timothy-dillon.md
- Card 5 (Uber University City) is David S. Bigelow, see voice-david-bigelow.md
- Card 6 (MCARE Act) is Mark Jaffe, see voice-mark-jaffe.md

For each excerpt that does not match (POV person, register, vocabulary, syntax preferences from the profile), rewrite it to match. Edit the file. Return a per-card report of: original excerpt / new excerpt / what voice rule fired.
```

After all 3 agents return, dispatch a final validation:

### Agent 4: Demo-perfection-pass on the rebuild

```
Run /demo-perfection-pass on /Users/taqticlaw/Projects/mccann-injury-law/index.html (file path or http://localhost:4324/).

Apply the 4-skill swarm: copy-audit (now 20 anti-patterns), voice-builder validation (against the 7 voice-profiles/), cro-ux-director (parallel 6 sub-audits), trust-signals-audit. Synthesize a unified PASS/WARN/FAIL report with ranked fix list. Write the report to /Users/taqticlaw/Projects/taqticscom/clients/mccann-injury-law/demo-preflight/2026-04-28-rebuild.json.

Threshold: PASS requires composite score 80 or higher, zero blockers. Anything below 80 surfaces blockers and asks for re-run after fixes.
```

## 7. Acceptance criteria for "ready to show Robert"

- Homepage reads as a working PI firm site, not an agency brand deck
- Intake form present above the fold or right below it, 3 fields max
- Every section head is functional ("Latest investigations", "Recent results", etc.) not slogan
- All 6 article cards have real metadata (date, reading time, byline anatomy)
- Practice areas link to either real sub-pages or honestly-stubbed pages
- Office map present with 4 pins
- Press strip with 4+ outlet logos
- Testimonials with name + city + case type
- Hours of operation visible
- demo-perfection-pass: PASS at 80+, zero blockers
- 0 em-dashes, 0 banned words, 0 negation describing the firm
- Cap any non-brand noun at 2 page-wide instances
- All locked items intact

## 8. References for stuck moments

- Skills inventory: `~/Projects/taqticscom/clients/mccann-injury-law/homepage-demo/SKILLS-FLOW-ANALYSIS.md`
- Session learnings (what we caught, what we missed): `~/Projects/taqticscom/clients/mccann-injury-law/homepage-demo/SESSION-LEARNINGS.md`
- Positive-voice rule: `~/.claude/projects/-Users-taqticlaw/memory/feedback_positive-voice-only.md`
- Demo-perfection-pass spec: `~/.claude/skills/demo-perfection-pass/SKILL.md`
- Where-are-we orientation: `~/.claude/skills/where-are-we/SKILL.md`

When in doubt, read `.client-state.json` first, then the audit-script, then the brand-system. Skip the figma.md until you need messaging architecture references.

End of memo.
