# McCann Dillon Jaffe and Lamb, Build Repo Instructions

This is the McCann Dillon Jaffe and Lamb build repo. The client pipeline state lives in `.client-state.json` at this directory.

## First Action: Orient

Run `/where-are-we` before doing anything else. It reads `.client-state.json`, prints the current phase plus task plus locked decisions, and tells you which skill to invoke next. Do not skip this step.

## The Pipeline

Every Taqtics client moves through:

```
AUDIT > RESEARCH > DESIGN > CODING
```

This repo is in the **CODING** phase (homepage demo built, static HTML). Audit, research, and design artifacts already exist at `~/Projects/taqticscom/clients/mccann-injury-law/`. Do not redo any of that work, read what's already there.

## Canonical Docs

| Doc | What's there |
|---|---|
| `.client-state.json` | Phase, current task, locked decisions, paths. Single source of truth. |
| `SESSION-LEARNINGS.md` | What was built, what worked, what broke, what to watch |
| `SKILLS-FLOW-ANALYSIS.md` | 569-line definitive skills inventory + pipeline map |
| `~/Projects/taqticscom/clients/mccann-injury-law/audit-script.md` | The branded audit |
| `~/Projects/taqticscom/clients/mccann-injury-law/brand-system.md` | Locked color tokens, 10ft viewing rules |
| `~/Projects/taqticscom/clients/mccann-injury-law/editorial-system.md` | 7 author voices, content matrix, schema fields |
| `~/Projects/taqticscom/clients/mccann-injury-law/figma.md` | Figma V5 spec (10 sections) |
| `~/Projects/taqticscom/clients/mccann-injury-law/attorneys.md` | Full 8-attorney roster with creds |

## Discipline (inherited from global)

- No em-dashes or en-dashes in user-facing copy (HTML, MDX, content MD)
- Contractions always
- Surgical changes only. Do not "improve" adjacent code
- Audit before patching
- Update `.client-state.json` when a task completes

## Demo

Open `index.html` in a browser, or serve with any static server. The Practice and Attorneys nav items have hover dropdowns. Click any editorial card to navigate to the full article.

## Locks (do not relitigate)

Anything in `lockedDecisions[]` is settled. For McCann that includes:

- **Tagline:** TWENTY-FIVE YEARS. ONE TRIAL RECORD.
- **Logo:** Bracket wordmark, dark-bg version at `logos/mccann-logo-dark.png`
- **Colors:** Independence Navy + Liberty Brass + Alert Crimson + Philly Newsprint + Keystone Slate
- **Color rule:** Brass on dark only. Navy or Ink on light. Brass-Bright never on light backgrounds.
- **Type:** Anton + Inter + JetBrains Mono + Source Serif 4
- **Core truth:** McCann prepares every case like it's going to trial.
- **Key numbers:** $200M+ recovered, 17 verdicts, 25 years, 4 offices PA NJ DE, 8 attorneys, 3 state bars

Source of truth is `lockedDecisions[]` in `.client-state.json`. If the user asks to change a locked value, surface the lock plus `lockedAt` and ask for explicit confirmation.

## Demo Preflight

Most recent preflight at `~/Projects/taqticscom/clients/mccann-injury-law/demo-preflight/2026-04-28-homepage.json`. PASS at 84. Five priority fixes documented for post-demo polish.

Run `/demo-perfection-pass` against any URL or local file to revalidate before deploys or client showings.
