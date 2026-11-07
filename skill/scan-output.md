# Scan Output: Issue Scout Results

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

## Scan 4: Refined queries, fresh real-world search (2026-11-07) ⭐ FINAL

**Summary:** Removed tier-2 query, kept Python bug + JavaScript bug + good first issue. Returned 299 unique issues.

**Accepted (5 issues):**
1. **earthobservations/wetterdienst#3878: Explorer's settings duplicate app settings** ⭐ **[CLAIMED]**
   - **Real debugging task:** Settings duplication in explorer.vue/useSettings.ts
   - **Large active repo:** 456 stars, 5 human commits today by gutzbenj
   - **JavaScript/TypeScript:** Perfect for web dev class prep
   - **Clean claim:** 0 comments, no assignees, no PRs
   - **Clear proposal:** Maintainer laid out exact steps to fix

2. benholland1024/pluggybot#646: Robot gripper reports "closed on nothing"
   - 1-star personal project, maintainer's own working note
   - Not a real contribution opportunity

3. bk-squared/rfx#2451: Waveguide port below cutoff frequency
4. bk-squared/rfx#2450: reference_plane_cells changes S11 in run() but not forward()
5. bk-squared/rfx#2449: Two driven waveguide ports give S11 above 1
   - All three rfx issues require specialist RF electromagnetics knowledge
   - Commits are all from rfx-agent[bot] (no human maintainers visible)
   - **Conflict with profile:** "avoiding issues that require in-depth knowledge of unfamiliar languages"

---

## JSON Results (Scan 4)

```json
[
  {"item": "https://github.com/earthobservations/wetterdienst/issues/3878",
   "checks": [
     {"name": "Repo is active", "grade": "pass", "evidence": "Latest default-branch commit 2026-11-07 by gutzbenj (5 human commits today)"},
     {"name": "Manageable scope", "grade": "pass", "evidence": "Body describes the task: Explorer dataSettings in explorer.vue never read app useSettings.ts (convertUnits/units 'persisted and read by nothing')"},
     {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no linked PRs"}
   ], "verdict": "accept"},
  {"item": "https://github.com/benholland1024/pluggybot/issues/646",
   "checks": [
     {"name": "Repo is active", "grade": "pass", "evidence": "Latest commit 2026-11-07 (Merge PR #641 by benholland1024)"},
     {"name": "Manageable scope", "grade": "pass", "evidence": "Body describes the defect: Gripper.held() in humanoid/arms.py wants half the requested force, so thin grips read 'closed on nothing'"},
     {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no linked PRs"}
   ], "verdict": "accept"},
  {"item": "https://github.com/bk-squared/rfx/issues/2451",
   "checks": [
     {"name": "Repo is active", "grade": "pass", "evidence": "Latest commit 2026-11-07 (rfx-agent[bot])"},
     {"name": "Manageable scope", "grade": "pass", "evidence": "Body describes the task: graded port builder falls back to freq_max/2 instead of _default_waveguide_f0"},
     {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no linked PRs"}
   ], "verdict": "accept"},
  {"item": "https://github.com/bk-squared/rfx/issues/2450",
   "checks": [
     {"name": "Repo is active", "grade": "pass", "evidence": "Latest commit 2026-11-07 (rfx-agent[bot])"},
     {"name": "Manageable scope", "grade": "pass", "evidence": "Body: refplane.py:544-546 calls decompose_wire_s_matrix without v_port, changing S11"},
     {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no linked PRs"}
   ], "verdict": "accept"},
  {"item": "https://github.com/bk-squared/rfx/issues/2449",
   "checks": [
     {"name": "Repo is active", "grade": "pass", "evidence": "Latest commit 2026-11-07 (rfx-agent[bot])"},
     {"name": "Manageable scope", "grade": "pass", "evidence": "Body: require_isolated_s_drive covers only lumped/wire ports, so two driven ports give |S11| 1.60"},
     {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no linked PRs"}
   ], "verdict": "accept"}
]
```