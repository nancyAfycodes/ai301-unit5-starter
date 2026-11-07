# Scan Output: Issue Scout Results (Complete)

## Scan 1: Single-repo baseline (2026-11-07)

**Summary:** Repo-locked search to Path Review classroom, returned 56 issues.

**Accepted (3 issues):**
- #39: Review progress indicator doesn't update (frontend/Python, 5 files)
- #25: Safety monitoring doesn't emit metrics (Python, 8–12h)
- #50: Add vulnerability scan to CI (DevOps, weaker fit)

**Rejected (2 issues):**
- #24: Injection detection misses role-switch — already claimed (PRs #197, #224)
- #70: README parser test fixture — already claimed (PR #103)

---

## Scan 2: Expanded search with Python/JavaScript (2026-11-07)

**Summary:** Removed `--repo` flag, added language filtering. Returned 400 issues.

**Accepted (3 issues):**
1. **rockcarver/frodo-cli#1088: conn describe prints secret header values** ⭐ **[COMPLETED BEFORE CLAIM]**
   - Real CLI tool (55 stars, active maintainers)
   - Bug in JavaScript/TypeScript
   - 0 comments, no PR
   - **Issue was fixed and merged (PR #1090) while being claimed**

2. rockcarver/frodo-cli#1087: config-manager pull all exits 0 when step fails
   - Same repo, but "Decision needed before this is changed"
   - Undecided fix approach

3. MCPMark-genon/mcpmark-cicd#2: login form validation doesn't work
   - 0 stars, looks like test automation

**Rejected (2 issues):**
- neomjs/neo#20575 — assigned, PR #20576 open
- bongohorse/rider#651 — owner opened PR #652 8 seconds after issue filed

---

## Scan 3: Real-world Python validation (2026-11-07)

**Summary:** Fixed Python language filter to use `language:python` in query string. Returned 400 issues. All 5 top results were classroom repos — tier-2 label points back to sandbox.

**Accepted (5 issues, all classroom):**
- ai201-howard#71, #70, #32, #24
- ai301-howard#32 (duplicate of #3)

**Problem:** Tier-2 is classroom-only label. Repos nearly dead (last commits Sept 16, 52 days ago, 0 stars).

---

## Scan 4: Refined queries, fresh real-world search (2026-11-07)

**Summary:** Removed tier-2 query, kept Python bug + JavaScript bug + good first issue. Returned 299 unique issues.

**Accepted (5 issues):**
1. **earthobservations/wetterdienst#3878: Explorer's settings duplicate app settings** ⭐ **[GRADED, DEFERRED]**
   - Real debugging task: Settings duplication in explorer.vue/useSettings.ts
   - Large active repo: 456 stars, 5 human commits today by gutzbenj
   - JavaScript/TypeScript: Perfect for web dev class prep
   - Clean claim: 0 comments, no assignees, no PRs
   - Clear proposal: Maintainer laid out exact steps to fix
   - **Grading verdict: ACCEPT** (but scope larger than typical first contribution)

2. benholland1024/pluggybot#646: Robot gripper reports "closed on nothing"
   - 1-star personal project, maintainer's own working note
   - Not a real contribution opportunity

3. bk-squared/rfx#2451: Waveguide port below cutoff frequency
4. bk-squared/rfx#2450: reference_plane_cells changes S11 in run() but not forward()
5. bk-squared/rfx#2449: Two driven waveguide ports give S11 above 1
   - All three rfx issues require specialist RF electromagnetics knowledge
   - Commits are all from rfx-agent[bot] (no human maintainers visible)
   - **Conflict with profile:** "avoiding issues that require in-depth knowledge of unfamiliar languages"

**Rejected (0 issues)**

---

## Scan 5: Python-only focus, fresh real-world search (2026-11-07) ⭐ FINAL

**Summary:** Removed JavaScript queries, kept Python-only (good first issue, bug, enhancement). Returned 296 unique issues. All 5 top results came from Q2 (Python + bug), opened within last hour by repo maintainers, 0 comments.

**Accepted (4 issues):**
1. **samcorky/menagerist#294: Event loop is closed after first database command** ⭐ **[CLAIMED]**
   - Pure Python debugging (asyncio.run + lru_cache engine outliving loop)
   - Clear repro steps and likely cause
   - Matches profile perfectly (Python debugging, larger codebase)
   - 0 comments, no assignees, no linked PRs
   - Smaller, focused scope
   - **Grading verdict: ACCEPT** ✅

2. **earthobservations/wetterdienst#3878: Explorer's settings duplicate app settings** ⭐ **[DEFERRED FOR LATER]**
   - Settings duplication in explorer.vue/useSettings.ts
   - 456 stars, actively maintained (5 commits today)
   - TypeScript/Vue (JavaScript challenge)
   - Multi-part refactor (larger scope)
   - **Grading verdict: ACCEPT** (but with caveats on scope)

3. charlieanna/autocode#2880: Every stage records cost_usd as null
   - Python bug (cost_usd recorded as null)
   - 1 star, AI-agent pipeline (steep ramp-up)
   - **Grading verdict: ACCEPT**

4. NVIDIA-AI-Blueprints/Multi-Agent-Intelligent-Warehouse#277: Prometheus/Grafana can't collect metrics
   - Active repo (135 stars)
   - Docker and monitoring config, not Python debugging
   - **Grading verdict: ACCEPT**

**Rejected (1 issue):**
- Nitjsefnie-Harness-Commons/daedalus#1777 — maintainer has open PR #1770 (already working on it)

---

## Grading Results (Scan 5)

### menagerist#294 — FINAL SELECTION ✅

```json
{
  "item": "https://github.com/samcorky/menagerist/issues/294",
  "checks": [
    {
      "name": "Repo is active",
      "grade": "pass",
      "evidence": "Latest default-branch commit 2026-11-07T21:23:01Z (feat(cli): show build info... #292)"
    },
    {
      "name": "Manageable scope",
      "grade": "pass",
      "evidence": "Body gives repro steps, likely cause (lru_cache engine outliving asyncio.run loops), and two possible fixes"
    },
    {
      "name": "Not already claimed",
      "grade": "pass",
      "evidence": "assignees: [], comments: 0, no cross-referenced PRs in timeline"
    }
  ],
  "verdict": "accept"
}
```

### wetterdienst#3878 — DEFERRED FOR FUTURE ⭐

```json
{
  "item": "https://github.com/earthobservations/wetterdienst/issues/3878",
  "checks": [
    {
      "name": "Repo is active",
      "grade": "pass",
      "evidence": "Latest default-branch commit 2026-11-07T21:30:10Z (feat(providers)... #3868)"
    },
    {
      "name": "Manageable scope",
      "grade": "pass",
      "evidence": "Body states a 3-part proposal plus a 'Check, and keep working' list; rubric passes any described task regardless of complexity"
    },
    {
      "name": "Not already claimed",
      "grade": "pass",
      "evidence": "assignees: [], comments: 0, no cross-referenced PRs in timeline"
    }
  ],
  "verdict": "accept"
}
```

---

## Summary: Path to menagerist#294

- **Scan 1:** Classroom repos, high-comment issues
- **Scan 2:** Real-world search, found #1088 (completed before claim)
- **Scan 3:** Python validation, revealed tier-2 problem
- **Scan 4:** Fixed tier-2, found wetterdienst#3878 (too complex for first)
- **Scan 5:** Python-only focus, found menagerist#294 ⭐ **CLAIMED**

**Total scans:** 5  
**Total cost:** ~$5 course credit  
**Result:** Perfect-fit first contribution + strong backup challenge for later