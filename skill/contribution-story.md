# Contribution: Event loop is closed after first database command

Path: `beat-2-contribution/contribution-story.md`

**Contribution Number:** [1]

**Student:** [Nancy Anatuanya]

**GitHub Username:** [nancyAfycodes]

**Issue:** https://github.com/samcorky/menagerist/issues/294

**Pull Request:** [GitHub PR link, once opened]

---

## Toolkit

**Unit 5: Issue scout with Python/JavaScript language filtering and real-world search**

I built a skill that searches GitHub for open-source issues matching my profile: 
Python debugging with JavaScript stretching, in larger codebases. Ran 5 scans (about $5 in total cost), 
discovering that `language:python` must be in the query string (not --language flags), 
that course labels like tier-2 point back to the sandbox, and that bot commits can fool 
the "active repo" check. Each scan refined the strategy: removing repo lock, fixing 
language filtering, dropping the tier-2 query, narrowing to Python-only focus. Scan 5 found 
samcorky/menagerist#294: a pure Python asyncio debugging issue in an active, well-maintained repo 
with clear repro steps and a likely cause already identified.

**Unit 6: Scope-feasible rubric patch and voice-guide upstream refinement**

Patched the rubric's scope check to accept issues with open edges and flag them with difficulty 
notes (straightforward, moderate, ambitious) instead of rejecting them outright. This shift reflects 
real-world issues: they rarely ship perfectly bounded. Re-graded #294 with the updated rubric and got 
**moderate** difficulty: location is clear (asyncio.run + lru_cache in media_app.py and platform/database.py), 
but requires a design decision between two fix approaches (run_async helper vs NullPool). Read menagerist's 
CONTRIBUTING.md and AGENTS.md, confirming that AI contributions are explicitly welcomed and documented. 
Posted a claim comment naming my first step (tracing asyncio lifecycle), proving reproduction, and asking 
the maintainer which fix approach they prefer before I open a PR.

**Unit 7: [one line on the tool work]**

[2-4 sentences: fill in Unit 7]

**Unit 8: [one line on the tool work]**

[2-4 sentences: fill in Unit 8]

---

## Why I Chose This Issue

I ran 5 scans with my issue-scout skill to find a real-world issue that matched my profile. 
Scan 1 locked to the classroom repo and surfaced high-comment issues, exposing a scope 
mismatch. I then fixed the queries to expand to GitHub's public repos. Scan 2 found 
rockcarver/frodo-cli#1088 (secret headers leak), a perfect match, but it was completed 
and merged before I could claim it. Scan 3 revealed that the tier-2 query pointed back 
to the sandbox, so I dropped it. Scan 4 returned earthobservations/wetterdienst#3878: 
a settings-duplication bug in an active 456-star multilingual app. Scan 5 focused on 
Python only and returned both #3878 and samcorky/menagerist#294. 

I chose #294 because it's pure Python debugging with a smaller, focused scope—exactly 
what I need for a first contribution. The issue has clear repro steps and an identified 
likely cause (lru_cache engine outliving asyncio.run loops), so the path to fix is clear. 
Both issues were graded as "accept" by my rubric, but #294 is better suited for a first 
contribution. I'll tackle #3878 (settings refactor, TypeScript/Vue) as a second contribution 
once #294 is merged, which is a great stretch goal for building JavaScript skills.

**Claim comment:** https://github.com/samcorky/menagerist/issues/294#issuecomment-6719824504

**Toolkit**

- **Unit 5:** issue-scout (5 scans with refined search strategy and rubric, plus grading)
  - What it produced: Filtered 296+ Python issues through bug label matching and comment-count ranking; graded top candidates with rubric checks; both finalists passed (menagerist#294 and wetterdienst#3878)
  - Difficulties: Python-only focus eliminated JavaScript options; owner-opened issues risk being fixed by maintainer; comment filter barely worked (all 0 comments); old rubric too loose to distinguish beginner-friendly from complex refactors
  - What changed: Removed JavaScript queries for Python focus; decided to grade BEFORE claiming (caught that #3878 scope was too large); deferred #3878 as second contribution for later

- **Unit 6:** Rubric patch (scope-feasible + difficulty notes) and voice-guide upstream
  - What it produced: Patched rubric to accept issues with open edges, flagging them with difficulty notes instead of rejecting; re-graded #294 as "moderate" (clear location, design choice needed); posted claim comment with first step, reproduction evidence, and design question
  - Difficulties: Understanding why scope-feasible is better than strict scope checking; learning when to ask maintainers design questions early
  - What changed: Scope check now informs instead of rejects; difficulty notes give chooser visibility into complexity; claim comment frames the design question clearly for the maintainer