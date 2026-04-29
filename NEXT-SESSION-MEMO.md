# MEMO: McCann homepage rebuild

**Paste this entire file into a fresh session after `/clear`. Do not skim. Read it whole, then execute.**

You are the McCann Dillon Jaffe and Lamb homepage build agent. The previous session shipped a brand manifesto disguised as a working site. Jared called it. Your job: rebuild the root `index.html` as a legit working PI law firm homepage with the McCann editorial-led differentiator inside an operational shell. The manifesto version is preserved at `/preview/` for reference.

You have all the Taqtics skills available globally. You have agent dispatch. You have a working localhost server. Don't think, execute the sequence.

---

## STEP 1, Orient (5 min)

Run `/where-are-we` first. Then read these files in this order. No skipping.

```
~/Projects/mccann-injury-law/.client-state.json     phase, locked decisions, paths
~/Projects/mccann-injury-law/index.html             current state, the rebuild target
~/Projects/mccann-injury-law/preview/index.html     manifesto backup, the reference
~/Projects/taqticscom/clients/mccann-injury-law/audit-script.md           full audit
~/Projects/taqticscom/clients/mccann-injury-law/research/money-keyword-positions.md   ranks 0/8 in Philly
~/Projects/taqticscom/clients/mccann-injury-law/research/homepage.md      current site scrape
~/Projects/taqticscom/clients/mccann-injury-law/research/contact.md       current intake form
~/Projects/taqticscom/clients/mccann-injury-law/brand-system.md           locked tokens
~/Projects/taqticscom/clients/mccann-injury-law/editorial-system.md       7 author voices
~/Projects/taqticscom/clients/mccann-injury-law/figma.md                  6-unit messaging
~/Projects/taqticscom/clients/mccann-injury-law/voice-profiles/           7 voice-{slug}.md files
~/Projects/taqticscom/clients/mccann-injury-law/homepage-demo/SESSION-LEARNINGS.md
```

Open these URLs in your browser:
- http://localhost:4324/         current homepage (the rebuild target)
- http://localhost:4324/preview/  brand-preview manifesto (reference, do not edit)

If localhost:4324 is not running, start it: `cd ~/Projects/mccann-injury-law && python3 -m http.server 4324 &`

## STEP 2, Dispatch the swarm (single message, 4 parallel agents)

Send all 4 of these agent dispatches in ONE message so they run in parallel. Each has a focused job and a defined output.

### Agent 1, Functional rebuild

```
Rebuild /Users/taqticlaw/Projects/mccann-injury-law/index.html as a working PI law firm homepage. The current file reads as a brand manifesto, demote slogan h2s to functional headings:

  "Recent results"           replaces "The verdicts are the record"
  "Latest investigations"    replaces "Every article is a case file"
  "Practice areas"           replaces "Six lanes. Every one tried."
  "Our attorneys"            replaces "They try the cases. They write the articles."
  "How we work"              trim to 1 line on the homepage, move 5-step detail to /how-we-work/
  "Schedule a consultation"  replaces "One call. A real lawyer."

Add these new sections:

  Hero: keep h1 "25 Years. One Record. One Call." (locked). Add a 3-field intake form on the right side at desktop, below hero on mobile. Fields: name, phone, what happened.
  Press strip: 4 to 6 outlet logos (Inquirer, Legal Intelligencer, Philadelphia Magazine, ABC6, etc). Use placeholder marks if no logos available, label per outlet.
  Testimonials: 3 cards with name, city, case type, photo placeholder. Use real-sounding quotes per the McCann voice (no superlatives, no exclamations).
  Office locations: map placeholder with 4 pins (Philadelphia, Wilmington, Haddon Township, Jenkintown), hours and driving directions per office.
  24/7 phone-routing eyebrow above the footer.

Move the McCann editorial-led differentiator (Investigations section) high on the page so it leads, but inside the operational shell. Cap "Every one" at 1 instance page-wide. Cap any non-brand noun at 2 instances page-wide.

Voice rules, non-negotiable:
  Cadence: 25 Years. One Record. One Call. Three short ascending lines.
  Numerals digit-first.
  No em-dashes or en-dashes.
  No banned words.
  No negation describing the firm.
  Active voice.
  Infer don't explain.
  No methodology dumps.
  No jargon civilians read literally.
  Robert McCann founder voice in any first-person body copy.

Locked, never change:
  Hero h1, color system (Independence Navy, Liberty Brass, Alert Crimson, Philly Newsprint, Keystone Slate), color rule (brass on dark only, navy weight 700 on light), typography (Anton, Inter, JetBrains Mono, Source Serif 4), logo path, all verdict amounts and venues, all attorney names and roles and bar admissions, all addresses, all schema.

Read /Users/taqticlaw/Projects/taqticscom/clients/mccann-injury-law/research/homepage.md and contact.md before designing the intake form. See what patterns the current site uses, then improve them per /form-optimization rules.

Edit the file directly. Return a tight report listing every section you touched, the new copy verbatim, and which voice rule each refactor enforced.
```

### Agent 2, Data-grounded keyword targeting

```
McCann ranks 0 of 8 for Philadelphia PI money keywords. The 8 keywords plus volumes are listed in /Users/taqticlaw/Projects/taqticscom/clients/mccann-injury-law/research/money-keyword-positions.md.

Update /Users/taqticlaw/Projects/mccann-injury-law/index.html so the page targets these 8 keywords through:

  Title tag           1 to 2 of the highest-volume terms
  Meta description    2 to 3 keywords woven naturally
  Hero h1 lock        do not touch
  Section headings    practice cards use keyword phrasing where it fits
  LegalService schema knowsAbout array  mirror the 8 money keywords
  Page H1 alt text    where applicable
  Footer copy         long-tail keyword variants

No keyword stuffing. Each keyword phrase appears at most once per relevant section. Read the schema in the existing file before editing, do not break it.

Edit the file directly. Return a per-section list of changes plus the final keyword density count.
```

### Agent 3, Voice profile validation per byline

```
Read all 7 files at /Users/taqticlaw/Projects/taqticscom/clients/mccann-injury-law/voice-profiles/ first.

For every byline excerpt and attorney 1-line bio on /Users/taqticlaw/Projects/mccann-injury-law/index.html, validate the copy against the assigned author's voice profile (POV person, register, vocabulary signals, syntax preferences, sample openers).

Voice profile assignments per article card:

  Card 1 I-95 verdicts                Robert E. McCann       voice-robert-mccann.md
  Card 2 Roosevelt Boulevard          Thomas J. O'Malley     voice-thomas-omalley.md
  Card 3 SEPTA FELA                   Michael P. Minuti      voice-michael-minuti.md
  Card 4 Commodore Barry Bridge       Timothy A. Dillon      voice-timothy-dillon.md
  Card 5 Uber University City         David S. Bigelow       voice-david-bigelow.md
  Card 6 MCARE Act                    Mark Jaffe             voice-mark-jaffe.md

For each excerpt that does not match its profile, rewrite it to match. Apply the same check to bench-card 1-line bios. Edit the file directly. Return a per-card report: original excerpt, new excerpt, which voice rule fired.
```

### Agent 4, Run /demo-perfection-pass on the rebuild

After Agents 1, 2, and 3 all complete, dispatch this final agent:

```
Run /demo-perfection-pass on /Users/taqticlaw/Projects/mccann-injury-law/index.html (file path or http://localhost:4324/).

Apply the 4-skill swarm in sequence:
  copy-audit (now 20 anti-patterns, especially items 14 to 20 added 2026-04-28)
  voice-builder validation against the 7 voice-profiles/
  cro-ux-director, parallel 6 sub-audits (cro, a11y, form, copy, trust, perf)
  trust-signals-audit, legal E-E-A-T

Synthesize a unified PASS/WARN/FAIL report with ranked fix list. Write the report to /Users/taqticlaw/Projects/taqticscom/clients/mccann-injury-law/demo-preflight/2026-04-28-rebuild.json.

PASS criteria:
  Composite score 80 or higher
  Zero blockers
  All locked items intact (hero h1, color system, typography, logo, verdicts, attorney details, addresses, schema)
  0 em-dashes, 0 banned words, 0 negation describing the firm
  No non-brand noun appears more than 2 times page-wide
  Intake form present, scored against form-optimization rules
  All 6 article excerpts pass voice validation against their assigned profile

If FAIL, surface blockers, ask for re-run after fixes.
```

## STEP 3, Synthesize and update state

After Agent 4 returns:

1. Read the preflight JSON report at `~/Projects/taqticscom/clients/mccann-injury-law/demo-preflight/2026-04-28-rebuild.json`
2. If PASS, update `.client-state.json`:
   - Move M002 from queue.remaining to queue.done
   - Append a new entry to lockedDecisions with the rebuild result
   - Bump phase.lastAdvanced
3. Commit the rebuild on the McCann repo: `cd ~/Projects/mccann-injury-law && git add . && git commit -m "rebuild: working homepage with intake, press, testimonials, offices"`
4. Ask Jared before pushing to GitHub.

## STEP 4, Show Jared

Once committed, tell Jared:

  http://localhost:4324/         the rebuild
  http://localhost:4324/preview/  the manifesto backup
  Preflight report path
  Pass status and score
  Top 3 quick-win fixes if any

Stand by for his review. Do not iterate further without direction.

---

## Reference, voice and cadence rules

Cadence pattern (Jared's, applied page-wide):

```
25 Years.
One Record.
One Call.
```

Three short ascending lines. Numerals digit-first. Declarative. No throat-clearing. No adjectives.

McCann voice (per editorial-system.md):
- First person founder authority for Robert. "I pulled the verdict slips..."
- Third person, dry, statute-grounded for Mark Jaffe.
- Second person, warm, coach-like for Thomas O'Malley.
- Third person, comparative for Timothy Dillon.
- First person, case-forward for Patrick Lamb.
- Second person, digital-native for David Bigelow.
- Third person, industry-grounded for Michael Minuti.

Hard rules (PreToolUse hook will block on violation):
- No em-dashes or en-dashes anywhere
- No banned words (see CLAUDE.md global)
- No negation describing the firm ("we don't", "not a", "no [bad thing]")
- Numerals digit-first, not spelled out
- Contractions always
- Active voice
- Infer don't explain
- Jargon civilians read literally is out
- Cap any single noun at 2 page-wide instances
- 6 anti-patterns added 2026-04-28 to copy-audit, see `~/.claude/skills/copy-audit/SKILL.md` items 14-20

## Reference, locked items

| Item | Value |
|---|---|
| Hero h1 | `25 Years. / One Record. / One Call.` |
| Tagline (long) | `TWENTY-FIVE YEARS. ONE TRIAL RECORD.` |
| Logo | `logos/mccann-logo-dark.png` (488x86, dark-bg only) |
| Colors | Independence Navy `#0B2545`, Liberty Brass `#E8A22C`, Alert Crimson `#C03221`, Philly Newsprint `#F4EDE0`, Keystone Slate `#5A6F8F` |
| Color rule | Brass on dark only. Navy weight 700 on light. Brass-Bright never on light. |
| Type | Anton (display) + Inter (body) + JetBrains Mono (eyebrow) + Source Serif 4 (article body) |
| Verdicts | $9.5M (Construction, Phila County 2024), $8M (MedMal, Delaware County 2023), $6M (Trucking, I-95 2023), $5.75M (Premises, Montgomery 2022) |
| Attorneys | Robert E. McCann (Founding Member), Timothy A. Dillon (Partner DE), Mark Jaffe (Partner), Patrick C. Lamb (Partner), Thomas J. O'Malley (Attorney), David S. Bigelow (Attorney), Michael P. Minuti (Attorney DE), Jonathan M. Bigelow (Associate DE) |
| Offices | Philadelphia (1845 Walnut St Suite 950, 215.569.8488), Wilmington DE (302.888.1221), Haddon Township NJ, Jenkintown PA |
| Stats | $200M+ recovered, 17 verdicts, 25 years, 4 offices, 8 attorneys, licensed in PA NJ DE, 2698 keywords ranking |

## Reference, skills available

| Skill | Use |
|---|---|
| `/where-are-we` | Orient anytime |
| `/demo-perfection-pass` | Final validation, 4-skill swarm |
| `/copy-audit` | 20 anti-patterns now |
| `/taqtics-meta-messaging` | 6-unit messaging architecture |
| `/voice-builder` | Voice profile validation |
| `/cro-ux-director` | Parallel 6 sub-audits |
| `/form-optimization` | For the new intake form |
| `/trust-signals-audit` | E-E-A-T validation |
| `/cro-audit` | Mobile UX |
| `/accessibility-audit` | WCAG 2.2 AA |
| `/performance-audit` | Core Web Vitals |

End of memo. Execute STEP 1.
