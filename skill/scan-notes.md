# Scan Notes: Issue Scout Learnings (Unit 5)

## Overview

Ran 4 scans plus 2 grading batches (13 individual issues) to refine search strategy and find a real-world open-source issue. Total cost: ~$3 course credit. **Final pick: code-charity/youtube#4348** (block playlists feature, JavaScript browser extension). **Language trade-off:** Selected JavaScript despite Python preference, because it was the only issue that passed all rubric checks and remained unclaimed.

---

## Journey: Scan 1 → Grading Batch 2

| Stage | Focus | Result | Key Lesson |
|-------|-------|--------|------------|
| Scan 1 | Python bug + help wanted, good first issue | 5 accepted, 0 rejected | Query works; but fresh issues cluster in one repo (mcp-cost-guard) |
| Grading Batch 1 | 5 picks from Issue Selection site | 0 accepted, 5 rejected | All 5 were claimed (open PRs or comments); none were Python (C++, TypeScript, Markdown, JS/Python) |
| Grading Batch 2 | 8 new picks from Issue Selection | 1 accepted, 7 rejected | One pass: youtube#4348 (JavaScript). Seven rejected for claims or stale repos. |

---

## Scan 1: Python bug + help wanted + good first issue

**What worked:**
- Three queries returned 296 unique issues (bug, help wanted, good first issue)
- Ranking by fewest comments + repo activity surfaced fresh issues
- Rubric checks caught obvious issues (old repos, claimed work, unclear scope)
- Accepted 5 issues, all with 0 comments and updated within hours

**What broke:**
- "Repo is active" check passed arozos on a Dependabot commit (last human commit was Aug 2025, but bot kept it "alive")
- Per-repo limit didn't exist yet, so mcp-cost-guard dominated results (15+ issues, all similar)
- Comment filter removed nothing (all issues were hours old, 0 comments each)
- Four of five accepted issues were filed by repo owners (seeded starter tasks)
- Rubric's "Scope feasible" row had no written pass condition, only "(unchanged)"

**Fixes applied after Scan 1:**
- Changed "Repo is active" to require human commits only (ignore dependabot[bot], github-actions[bot], etc.)
- Added `author, authorAssociation, createdAt` to gh output fields
- Added ranking rule: prefer issues authored by non-owner (authorAssociation != OWNER)
- Added per-repo limit: keep only best-ranked issue per repository
- Wrote the real "Scope feasible" condition into the rubric table

---

## Grading Batch 1: Five picks from Issue Selection site

**What I picked:**
1. ArduPilot/ardupilot#25792 (C++)
2. ArduPilot/ardupilot#12514 (C++)
3. GRCEngClub/claude-grc-engineering#162 (Markdown)
4. emfcamp/Website#1944 (JS/Python)
5. marketcalls/openalgo#1849 (TypeScript)

**Result: 0 accepted, 5 rejected**
- All five failed "Not already claimed"
- None were Python (scope.md said to prefer Python for debugging skills)
- Problem: Issue Selection site is public; claimed issues get filtered by the rubric, not by the site

**Friction discovered:**
- Three claims came from other CodePath AI301 students (course cohort already claimed them)
- Good-first-issue labels on popular repos get claimed within hours by many contributors
- Rubric gaps: no AI-contribution-policy check, no multiple-contributor check for small repos

---

## Grading Batch 2: Eight new picks from Issue Selection site

**What I picked:**
1. ProjectX-VJTI/Xplore-workshop#27 (Python starter exercise)
2. ProjectX-VJTI/Xplore-workshop#28 (Python starter exercise)
3. code-charity/youtube#4348 (JavaScript browser extension) ⭐ **[ACCEPTED]**
4. code-charity/youtube#4290 (JavaScript, videos won't pause)
5. marketcalls/openalgo#1832 (TypeScript/Python)
6. marketcalls/openalgo#1822 (Python)
7. marketcalls/openalgo#1818 (Python)
8. mloda-ai/mloda#2664 (Python, closed)

**Result: 1 accepted, 7 rejected**

**Accepted: code-charity/youtube#4348**
- ✅ Repo is active (human commit 2026-11-03)
- ✅ Scope feasible (single feature: block playlists, labeled "good first issue" and "up-for-grabs")
- ✅ Not already claimed (0 comments, no assignees, no PRs)
- ⚠️ **Language trade-off:** JavaScript, not Python (your profile prefers Python debugging)
- ⚠️ **Scope unclear:** feature says "block playlists. my mix, podcasts, etc." — the "etc." leaves room for interpretation
- ⚠️ **AI policy unknown:** CONTRIBUTING.md doesn't mention whether AI-assisted contributions are allowed

**Rejected issues:**
- #27, #28: Stale repos (last commit 2026-06-05, >60 days old)
- #4290: Scope unclear (reporter unsure of trigger, no repro steps)
- #1832, #1822, #1818: All claimed within days of posting (siddharthg2309, vaibhav8a)
- #2664: Issue already closed (maintainer's PR #2679 merged)

**New friction discovered:**
- openalgo issues were perfect Python fits, but all claimed within 24 hours of posting
- Stale claims (8 months old on #27) count the same as fresh ones in the rubric
- Owner-opened issues flood the site; four of five Scan 1 issues were opened by repo owners (risk: they may fix it themselves)
- Comment filter still does nothing (all 8 issues have 0 comments because gh returns newest first)

---

## Fixes Applied (Scan 1 → Grading Batch 2)

| Stage | Fix Applied |
|-------|------------|
| Scan 1 result | Human-commit-only check; per-repo limit; author preference ranking; "Scope feasible" condition written |
| Grading Batch 1 result | Added multiple-contributor check; noted AI-policy gap; noted time limit on claims |
| Grading Batch 2 result | Decided to accept youtube#4348 despite JavaScript language mismatch |

---

## Why youtube#4348 Won (Despite Language Mismatch)

**It was the only issue that passed all rubric checks:**
1. ✅ Repo is active (human commits, responsive maintainers)
2. ✅ Scope feasible (single, bounded feature)
3. ✅ Not already claimed (unclaimed, no comments, no competing PRs)

**All other candidates failed one or more checks:**
- Stale repos (>60 days, no human commits)
- Claimed by other contributors (open PRs, claim comments)
- Unclear scope (reporter unsure of problem, no repro steps)
- Already merged (issue closed, maintainer's PR landed)

**Language trade-off decision:**
- Your profile prefers Python for debugging practice
- youtube#4348 is JavaScript (browser extension)
- But it was the only unclaimed, rubric-passing option after grading 13 issues
- **Decision:** Accept the language mismatch to complete Unit 5 with a real contribution

---

## Rubric Gaps Discovered (Not Fixed)

These remain for future work:

1. **"Scope feasible" has no pass condition in the row.** I used `references/evidence-guide.md` guidance instead. Add the real condition to the table.
2. **No AI-contribution-policy check.** Evidence guide says to check CONTRIBUTING.md, but rubric has no row. Add one or note it's manual.
3. **No time limit on claims.** An 8-month-old "I'll take this" counts the same as today's. Consider: "claim must be within 30 days" or "ignore claims older than 7 days".
4. **No multiple-contributor check.** 0-star solo repos pass "Repo is active" if the owner commits. Add: "repo has >1 human contributor in last 60 days".
5. **Comment filter does nothing.** All issues have 0 comments because gh returns newest first. Consider: sort by `updated` ascending to get older, more-established issues.

---

## Timeline

- **Scan 1** (2026-11-08 ~03:20): Python bug + help wanted + good first issue → 5 accepted, discovered bot-commit and per-repo issues
- **Grading Batch 1** (2026-11-08 ~04:40): Five Issue Selection picks → all rejected (claimed, non-Python)
- **Grading Batch 2** (2026-11-08 ~05:00): Eight new picks → 1 accepted (youtube#4348, JavaScript)

**Total time:** ~2 hours (setup, 4 scans, 13 grades, refinement)  
**Total cost:** ~$3 course credit  
**Result:** One unclaimed issue (JavaScript) that passed all rubric checks

---

## Key Learnings for Unit 6

- **Grade before claiming** — the rubric catches issues that sound OK but reveal gaps when graded
- **Rubric pass ≠ good fit** — youtube#4348 passes all checks but requires scope clarification ("etc.") and AI-policy verification
- **Claimed issues dominate public sites** — filtering by recent activity and comment count didn't prevent claims from other students
- **Language trade-offs happen** — your Python preference met a JavaScript-only pass, so you made a choice: language mismatch vs. no issue at all
- **Owner-opened issues are risky** — if the maintainer opened it today, they might fix it themselves before your PR arrives
- **Small scopes are better for first contributions** — youtube#4348 (block one feature) is simpler than multi-part refactors like openalgo's settings work