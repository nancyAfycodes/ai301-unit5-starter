# Scan Notes: Issue Scout Learnings (All Scans)

## Overview

Ran 4 scans to refine search strategy and find a real-world open-source issue. Total cost: ~$4 course credit. **Final pick: earthobservations/wetterdienst#3878** (settings duplication bug in multilingual app).

---

## Journey: Scan 1 → Scan 4

| Scan | Focus | Result | Lesson |
|------|-------|--------|--------|
| Scan 1 | Single-repo (classroom) | Classroom only, high-comment issues | Scope mismatch: queries contradicted scope.md |
| Scan 2 | Python/JS, expanded | Found #1088 (great), but completed before claim | Python/JS filtering works; real-world search works |
| Scan 3 | Python validation | All tier-2 (classroom) | Tier-2 label is classroom-only; points back to sandbox |
| Scan 4 | Drop tier-2, keep bug | Found #3878 (ideal!) | Fresh queries surface real projects; rubric needs tightening |

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

## Scan 4: Refined queries, fresh real-world search ⭐ SUCCESS

**What worked:**
- Dropped tier-2 query
- Kept Python bug + JavaScript bug + good first issue
- Found **#3878** — perfect fit (active repo, clear task, right skills)
- Rubric correctly passed #3878, rejected specialist issues

**What broke (discovered but unfixed):**
1. **Rubric too loose** — passes specialist issues (RF electromagnetics)
2. **No newcomer-scope check** — can't distinguish beginner-friendly from expert-only
3. **Bot commits fool "active repo" check** — rfx has 4 bot commits, 1 human; looks active but may be abandoned
4. **No contribution-policy check** — didn't verify repos accept AI contributions
5. **Q2 and Q3 were duplicates** — both Python bug (scan 3/4)
6. **"Good first issue" buried** — bug preference ranked it below everything
7. **Tier filter useless** — only exists in course sandbox (removed by scan 4)
8. **No sort on search** — all 5 brand-new issues (0 comments, filter never worked)

---

## Fixes Applied (Scan 1 → Scan 4)

| Scan | Fix Applied |
|------|------------|
| 1→2 | Removed `--repo` flag, added language:python and language:javascript |
| 2→3 | Fixed Python filter to use `language:python` in query string (not --language flag) |
| 3→4 | Dropped tier-2 query entirely (classroom-only label) |

---

## Why #3878 Won (From 4 Scans of Learning)

1. **Real project** (456 stars, active humans, 5 commits today)
2. **Clear debugging task** (settings duplication, well-scoped proposal)
3. **Right skills** (TypeScript/Vue, builds JavaScript knowledge for web dev class)
4. **Unclaimed** (0 comments, no PRs, maintainer active in issue)
5. **Language barrier minimal** (German words are just UI labels, not blockers)

---

## Future Fixes (Scan 5+)

These 8 issues should be fixed before running more scans:

| Priority | Problem | Fix |
|----------|---------|-----|
| **High** | Rubric too loose | Add "newcomer scope" check: reject if requires specialist knowledge (RF, ML, etc.) |
| **High** | Bot commits fool "active repo" | Check that >50% of recent commits are by humans, not bots |
| **High** | No contribution-policy check | Read CONTRIBUTING.md; reject if "no AI" or "AI restricted" |
| **Medium** | Q2 and Q3 duplicates | Make them distinct (e.g., Q3: JavaScript + tier-2, or Python + enhancement) |
| **Medium** | "Good first issue" buried | Give it ranking boost (higher priority than bug label) |
| **Medium** | No sort on search | Add `--sort=updated --order=asc` to get older, more-established issues |
| **Low** | Tier filter useless | Remove from strategy (only in classroom); use "good first issue" label instead |
| **Low** | 5-comment cutoff barely works | Tighten to 0–2 comments, or require `commentsCount == 0` |

---

## What Transferred to This Course

- **Debugging real-world bugs** (not classroom exercises)
- **Working with active maintainers** (gutzbenj is triaging issues today)
- **Multilingual codebases** (German UI labels don't block understanding the code)
- **Full-stack understanding** (frontend + backend + settings system)
- **Iterative refinement** (4 scans, each teaching something new)

---

## Timeline

- **Scan 1** (2026-11-07 ~10:30): Classroom repos, high-comment issues
- **Scan 2** (2026-11-07 ~10:51): Real-world (#1088 found, but completed before claim)
- **Scan 3** (2026-11-07 ~11:05): Python validation revealed tier-2 problem
- **Scan 4** (2026-11-07 ~13:27): Fixed tier-2 issue, found #3878 ⭐ **[CLAIMED]**

**Total time:** ~3 hours (including setup, research, and learning)  
**Total cost:** ~$4 course credit  
**Result:** Real-world issue in active project with clear scope