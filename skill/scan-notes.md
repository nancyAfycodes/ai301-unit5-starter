# Scan Notes: Issue Scout Learnings (Complete, All Scans 1-5)

## Overview

Ran 5 scans to refine search strategy and find a real-world open-source issue. Total cost: ~$5 course credit. **Final pick: samcorky/menagerist#294** (asyncio event loop debugging, pure Python). **Backup: earthobservations/wetterdienst#3878** (settings refactor, TypeScript/Vue, for later challenge).

---

## Journey: Scan 1 → Scan 5

| Scan | Focus | Result | Key Lesson |
|------|-------|--------|------------|
| Scan 1 | Single-repo (classroom) | Classroom only, high-comment issues | Scope mismatch: queries contradicted scope.md |
| Scan 2 | Python/JS, expanded | Found #1088 (great), but completed before claim | Python/JS filtering works; real-world search works |
| Scan 3 | Python validation | All tier-2 (classroom) | Tier-2 label is classroom-only; points back to sandbox |
| Scan 4 | Drop tier-2, keep bug | Found #3878 (too complex) | Fresh queries surface real projects; rubric needs tightening |
| Scan 5 | Python-only focus | Found #294 (perfect fit!) ⭐ | Pure Python debugging, smaller scope, ideal first contribution |

---

## Scan 1: Single-repo baseline

**What worked:**
- Repo-locked search was focused
- Rubric checks caught claimed issues correctly
- Ranking by comment count surfaced unclaimed work

**What broke:**
- "Drop any assignee" filter useless (repo uses comment claims + PRs)
- "Prefer bugs" trusted label too much (issue #50 was really CI work)
- Scope mismatch: queries locked to one repo while scope.md said "real-world"

---

## Scan 2: Expanded Python/JavaScript search

**What worked:**
- Python/JavaScript language filters proved valid
- Found **#1088** — genuinely excellent (but got completed before claim!)
- Real-world search (400 issues) vs. classroom (56 issues)

**What broke:**
- All 3 accepted issues were JavaScript (Python filter may still be broken)
- 5-comment cutoff barely filtered (only 2 of 400 removed)
- No check catches throwaway repos (mcpmark-cicd has 0 stars)
- "Manageable scope" too loose — passed #1087 with "Decision needed"

---

## Scan 3: Real-world Python validation

**What worked:**
- Proved Python language filter works (returned real Python bugs)

**What broke:**
- Tier-2 query pointed back to sandbox despite scope.md saying "sandbox is behind you"
- All 5 results were classroom repos (nearly dead: last commits Sept 16, 52 days ago, 0 stars)
- "Repo is active" check barely passes for classroom repos, will fail by Nov 15

---

## Scan 4: Refined queries, fresh real-world search

**What worked:**
- Dropped tier-2 query
- Kept Python bug + JavaScript bug + good first issue
- Found **#3878** — real project (active repo, clear task)
- Rubric correctly passed #3878, rejected specialist issues

**What broke (discovered but unfixed):**
1. **Rubric too loose** — passes specialist issues (RF electromagnetics)
2. **No newcomer-scope check** — can't distinguish beginner-friendly from expert-only
3. **Bot commits fool "active repo" check** — rfx has 4 bot commits, 1 human; looks active but may be abandoned
4. **No contribution-policy check** — didn't verify repos accept AI contributions
5. **Q2 and Q3 duplicates** — both Python bug (wasted query space)
6. **"Good first issue" buried** — bug preference ranked it below everything
7. **Tier filter useless** — only exists in course sandbox (removed by scan 4)
8. **No sort on search** — all 5 brand-new issues (0 comments, filter never worked)

---

## Scan 5: Python-only focus, fresh real-world search ⭐ FINAL

**What worked:**
- Removed JavaScript queries, focused on Python only
- Found **#294** — pure Python debugging, perfect fit
- Smaller scope than #3878, more appropriate for first contribution
- Clear repro steps and likely cause already identified

**What broke (same as Scan 4, still unfixed):**
1. **Comment filter does nothing** — search returns newest issues first, so every candidate has 0 comments
2. **Rubric can't tell real repos from solo bot-driven ones** — passed 0–3-star repos where owner opens and fixes issues within minutes
3. **Language mismatch slips through** — `language:python` filters on repo's main language, so wetterdienst#3878 (a Vue/TypeScript fix) got ranked
4. **No contribution-policy check** — didn't verify repos' AI policies before suggesting

**New insight from Scan 5:**
5. **Owner-opened issues risk being fixed by maintainer** — Both #294 and #3878 were opened by repo owners within the last hour. They may commit fixes themselves before outside PRs arrive.

---

## Grading Results (Scan 5)

**menagerist#294** ✅ ACCEPT
- All 3 checks pass
- Pure Python debugging (asyncio.run + lru_cache engine outliving loop)
- Clear repro steps and likely cause
- Smaller, focused scope — ideal for first contribution
- **Claim comment posted:** 2026-11-07

**wetterdienst#3878** ✅ ACCEPT (but deferred)
- All 3 checks pass
- TypeScript/Vue (JavaScript challenge)
- Multi-part refactor (larger scope)
- Active repo (456 stars, 5 commits today)
- **Caveats:** Scope larger than typical first contribution; maintainer actively working in this area
- **Status:** Deferred for Unit 6-8 as second contribution (stretch goal)

---

## Fixes Applied (Scan 1 → Scan 5)

| Scan | Fix Applied |
|------|------------|
| 1→2 | Removed `--repo` flag, added language:python and language:javascript |
| 2→3 | Fixed Python filter to use `language:python` in query string (not --language flag) |
| 3→4 | Dropped tier-2 query entirely (classroom-only label) |
| 4→5 | Removed all JavaScript queries, focused on Python only |

---

## Future Fixes (Scan 6+)

These 8 issues should be fixed before running more scans:

| Priority | Problem | Fix |
|----------|---------|-----|
| **High** | Rubric too loose | Add "newcomer scope" check: reject if requires specialist knowledge (RF, ML, etc.) |
| **High** | Bot commits fool "active repo" | Check that >50% of recent commits are by humans, not bots |
| **High** | No contribution-policy check | Read CONTRIBUTING.md or AGENTS.md; reject if "no AI" or "AI restricted" |
| **High** | Owner-opened issues at risk | Check if issue was opened by maintainer today; warn if so (may fix it themselves) |
| **Medium** | Comment filter does nothing | Add `--sort=updated --order=asc` to get older, more-established issues |
| **Medium** | Language mismatch slips through | Verify issue file paths match the language (e.g., don't rank .vue/.ts files under Python) |
| **Low** | Tier filter useless | Remove from strategy (only in classroom); use "good first issue" label instead |
| **Low** | 5-comment cutoff barely works | Tighten to 0–2 comments, or require `commentsCount == 0` |

---

## Why menagerist#294 Won (From 5 Scans of Learning)

1. **Pure Python** (your comfort zone, clear learning goal)
2. **Real debugging task** (asyncio event loop issue, larger codebase)
3. **Smaller scope** (not a multi-part refactor like #3878)
4. **Clear path to fix** (repro steps + likely cause already identified)
5. **Unclaimed** (0 comments, no PRs, no assignees)
6. **Active repo** (recent commits, maintainer responsive)

---

## Future Plan: menagerist#294 → wetterdienst#3878

**Unit 5-8:** Complete menagerist#294 (Python debugging, safer first contribution)
**Future (Unit 9+):** Tackle wetterdienst#3878 (TypeScript/Vue challenge, larger scope, prep for web dev class)

This two-issue approach:
- Guarantees a solid first contribution for class
- Provides a stretch goal to build web dev skills
- Aligns with your stated goal of getting better at JavaScript while staying grounded in Python

---

## Timeline

- **Scan 1** (2026-11-07 ~10:30): Classroom repos, high-comment issues
- **Scan 2** (2026-11-07 ~10:51): Real-world (#1088 found, but completed before claim)
- **Scan 3** (2026-11-07 ~11:05): Python validation revealed tier-2 problem
- **Scan 4** (2026-11-07 ~13:27): Fixed tier-2 issue, found #3878 (too complex)
- **Scan 5** (2026-11-07 ~14:04): Python-only, found #294 ⭐ **[CLAIMED]**

**Total time:** ~3.5 hours (including setup, research, grading, learning)  
**Total cost:** ~$5 course credit  
**Result:** Perfect-fit first contribution + strong backup challenge

---

## Key Learnings for Future Units

- **Grade BEFORE claiming** — your rubric catches issues the grader finds OK but that are actually too complex
- **Check contribution policies** — CONTRIBUTING.md and AGENTS.md matter
- **Owner-opened issues are risky** — if the maintainer opened it today, they might fix it themselves
- **Smaller scope is better for first contributions** — #294 (pure debugging) is more appropriate than #3878 (multi-part refactor)
- **Python-only focus works** — easier to land a first contribution when you stay in your comfort zone