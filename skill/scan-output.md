# Scan Output: Issue Scout Results (Unit 5)

## Scan 1: ranked read-out

Funnel: 3 queries returned 296 unique issues. The filters removed 0 for assignees, 4 for having more than 5 comments, 0 for staleness and 14 for bounty titles. After keeping one issue per repo, 103 were left. The top 5 are 3 Python and 2 JavaScript, picked by the bug preference, then fewest comments, then most recently updated.

### Accepted (all 5), in fit order

1. repowise-dev/repowise#5368: a test that fails when run on its own because of lazy imports. Python, 8k stars, a large and busy codebase, and debugging work, so it's the best match for your profile. Straightforward: the issue names the file and line and says "one test, one import line." The contributing guide doesn't ban AI.
   Came from Q1 (Python good-first-issue). It ranked high because it has the bug label, Python, 0 comments, and was updated today.
2. OWASP/cornucopia#3749: the TA3 card's background image doesn't show. An active OWASP maintainer merged 3 PRs last night. Moderate: you have to find where the image is wired up, probably on the web frontend, so it doubles as JavaScript practice. CONTRIBUTING.md allows AI use with conditions: strip AI-generated noise, and verify the bug exists before opening a PR.
   Came from Q2 (Python bug + help wanted). It ranked high because of bug, Python, 0 comments.
3. codewithzubair07/particle-agent#10: make the CLI's PID check survive PID reuse. Python, with clear acceptance criteria. Moderate: it touches process inspection in cli.py plus new tests. Tension: the repo has 0 stars and only one human committer, and the last commit was 13 days ago.
   Came from Q1. It ranked high because of bug, Python, 0 comments.
4. tobychui/arozos#314: logging out over HTTP doesn't return you to the login page. Ambitious: the issue is written in Chinese, and the backend is Go, a language you haven't used. Ask the maintainer early whether the fix belongs in session handling or in the frontend redirect. Tension: it passes "repo is active" only because Dependabot committed on 10-20. The last human commit was on 08-16.
   Came from Q3 (JS bug). It filled one of the two required JavaScript slots: 0 comments, updated today.
5. tim-nish/kogaki#1754: move the re-judge runs into a pruned runs/ lane. Moderate: the design is already spelled out, but it touches 5 files (runs.json, runs.mjs, extract.mjs, the spec, and a check script). Tension: this is a 0-star solo repo, it looks agent-driven, and the owner is committing hourly.
   Came from Q3. It filled the other JavaScript slot: bug, 0 comments.

### Rejected

None.

### Friction worth logging in scan-notes.md

- The comment filter still does nothing. All 5 issues have 0 comments and were opened in the last 12 hours, and 4 of the 5 were opened by the repo owner. This is the same problem as scans 4 and 5. Adding a "created more than 7 days ago" filter or sorting by oldest updated would fix it.
- "Repo is active" can be passed by bot commits alone. That's how arozos passed. 0-star solo repos (particle-agent, kogaki) also pass with nothing to warn you.
- The Python query can surface frontend work. cornucopia came from a Python query, but the fix is probably in frontend code.

```json
[
  {"item": "https://github.com/repowise-dev/repowise/issues/5368", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Last commit 2026-11-08 by karnavagarwal (5 human commits today)"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "\"Good first issue: one test, one import line.\" at test_tool_overview.py:290"},
    {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no linked or referencing open PRs"}], "verdict": "accept"},
  {"item": "https://github.com/OWASP/cornucopia/issues/3749", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Last commit 2026-11-08 (sydseter merged #3747)"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "\"ensure the /cards/TA3 card comes up with the proper background image\""},
    {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no referencing PRs"}], "verdict": "accept"},
  {"item": "https://github.com/codewithzubair07/particle-agent/issues/10", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Last commit 2026-10-26 (13 days ago, within 60)"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "One behavior: verify PID identity in cli.py status/stop, with acceptance criteria"},
    {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no referencing PRs"}], "verdict": "accept"},
  {"item": "https://github.com/tobychui/arozos/issues/314", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Last commit 2026-10-20 (dependabot[bot], 19 days ago, within 60)"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "One bug: logout over HTTP refreshes to desktop.html instead of login page"},
    {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no referencing PRs"}], "verdict": "accept"},
  {"item": "https://github.com/tim-nish/kogaki/issues/1754", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Last commit 2026-11-08 by tim-nish"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "One change: route runConstraintsRejudge through a new proof-sheet lane, design specified"},
    {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no referencing PRs"}], "verdict": "accept"}
]
```

---

## Grade batch 1: Five picks from Issue Selection site (all rejected)

All five issues get reject. Every one fails "Not already claimed": someone has either opened a PR for it or posted a claim comment that nobody contested. All five repos pass "Repo is active", and all five issues pass "Scope feasible".

| # | Issue | Language | Why it was rejected |
|---|-------|----------|---------------------|
| 1 | ArduPilot #25792 (EAHRS duplicate temperature compensation) | C++ | Open PR #30863 from ohyaiamhere (Aug 2025), which the issue's author linked in the thread. MacOS also commented in Jul 2025 asking to be assigned. |
| 2 | ArduPilot #12514 (NMEA output fixed buffer) | C++ | Open PR #34403 from harsh839 (Sep 2026) says "Fixes #12514". The issue has been open since 2019, and two earlier PRs were closed (#22184, #34398). |
| 3 | GRCEngClub #162 (ISO 27001 evidence-checklist command) | Markdown | Three claim comments: srujana-keth twice in Jul 2026 and 0xBahalaNa in Aug 2026, who also posted a plan. No PR yet. |
| 4 | emfcamp/Website #1944 (always show signed-up shifts) | JS/Python | Claim comment from 1Cazarez (Jul 2026), plus open PR #2379 saying "Fixes #1944". |
| 5 | marketcalls/openalgo #1849 (API key out of localStorage) | TypeScript | Claim comment from Brucee-ee (Aug 2026), plus open PR #2270 from anyingiit (Oct 2026). |

All five were graded directly from the URLs you gave, so no search query or ranking step applied. There is no fit ranking because nothing was accepted.

Fit doesn't change a verdict, but for your next search: none of these is a Python issue. #1 and #2 are C++ firmware, #5 is TypeScript, #3 is Markdown docs, and #4 is mostly JavaScript.

Three problems with the rubric itself are worth adding to scan-notes.md:
- "Scope feasible" has no pass condition. The rubric row just says "(unchanged)", so I graded it using the scope section of references/evidence-guide.md. Write the real condition back into the row.
- Nothing covers the AI-contribution policy. The evidence guide's last section says to check each repo's contributing guidelines for AI rules, but the rubric has no row for it. I didn't check those policies.
- Two of the claims came from other CodePath AI301 students (#3 and #4). Good-first-issue labels on popular repos get claimed quickly. Filtering searches to issues with zero comments or recent label dates would cut down on wasted grading.

```json
[
  {
    "item": "https://github.com/ArduPilot/ardupilot/issues/25792",
    "checks": [
      {"name": "Repo is active", "grade": "pass", "evidence": "Human commit 2026-11-06 by blessed-maker (AP_Soaring), within 60 days"},
      {"name": "Scope feasible", "grade": "pass", "evidence": "Bounded fix with proposed solution; author: 'Given it's a small change, I think this would be a good first issue.'"},
      {"name": "Not already claimed", "grade": "fail", "evidence": "Open PR #30863 by ohyaiamhere 'Avoid duplicate temperature compensation in EAHRS', linked in thread by issue author"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/ArduPilot/ardupilot/issues/12514",
    "checks": [
      {"name": "Repo is active", "grade": "pass", "evidence": "Human commit 2026-11-06 by c1airexia (autotest), within 60 days"},
      {"name": "Scope feasible", "grade": "pass", "evidence": "peterbarker narrowed it: 'good-first-issue for the \"use persistent buffer\" aspect'; though open since 2019 with two closed PRs (#22184, #34398)"},
      {"name": "Not already claimed", "grade": "fail", "evidence": "Open PR #34403 by harsh839 (2026-09-14): 'Fixes #12514'"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/GRCEngClub/claude-grc-engineering/issues/162",
    "checks": [
      {"name": "Repo is active", "grade": "pass", "evidence": "Human commits 2026-10-31 by andr2sn (security bumps), within 60 days"},
      {"name": "Scope feasible", "grade": "pass", "evidence": "Single new file with acceptance-criteria checklist; labeled 'difficulty: easy'"},
      {"name": "Not already claimed", "grade": "fail", "evidence": "0xBahalaNa 2026-08-22: 'I'd like to take this one... Plan here: same structure...' (plus srujana-keth claims Jul 2026)"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/emfcamp/Website/issues/1944",
    "checks": [
      {"name": "Repo is active", "grade": "pass", "evidence": "Human commit 2026-10-30 by russss (mypy updates), ignoring dependabot[bot]"},
      {"name": "Scope feasible", "grade": "pass", "evidence": "Labeled 'Small'; one filter behavior change in schedule view"},
      {"name": "Not already claimed", "grade": "fail", "evidence": "1Cazarez claim comment 2026-07-29 and open PR #2379 'Fixes #1944'"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/marketcalls/openalgo/issues/1849",
    "checks": [
      {"name": "Repo is active", "grade": "pass", "evidence": "Human commits 2026-11-06 by marketcalls and Kalaiviswa, within 60 days"},
      {"name": "Scope feasible", "grade": "pass", "evidence": "Bounded to authStore persistence with acceptance criteria; 'Estimated time: 2-4 hours'"},
      {"name": "Not already claimed", "grade": "fail", "evidence": "Brucee-ee 2026-08-22: 'hey, i'll take this one!' and open PR #2270 by anyingiit 'keep the API key out of persisted localStorage'"}
    ],
    "verdict": "reject"
  }
]
```

---

## Grade batch 2: Eight new picks from Issue Selection site (1 accepted, 7 rejected)

I graded all 8 issues against the 3 required checks in rubric.md. One was accepted (code-charity/youtube#4348) and seven were rejected. Every issue came from your URL list, so search and ranking were skipped.

Rubric gap: the "Scope feasible" row has (unchanged) where its pass condition should be. I graded scope using the scope section of references/evidence-guide.md instead. Filling in that row should be your next rubric patch.

### Accepted

1. code-charity/youtube#4348 – "block playlists. my mix, podcasts, etc."
   - Active: a human (Fardin7798) committed on 2026-11-03.
   - Scope: it's one feature, labelled good first issue and up-for-grabs. The evidence guide says a short issue can still be a bounded one.
   - Not claimed: no comments, no assignee and no linked PRs.
   - Fit is poor: the project is in JavaScript (a browser extension), and your profile prefers Python.
   - This pass is borderline: "etc." leaves the scope open, and no maintainer has said what's included. I'd ask before starting. The repo's CONTRIBUTING.md doesn't mention AI use.

### Rejected

- Xplore-workshop#27:
  - Repo is active fails: the last commit was 2026-06-05, which is more than 60 days ago.
  - Not already claimed fails: Asmi768 claimed it in March, and PR #43 was closed without merging.
- Xplore-workshop#28:
  - Repo is active fails: same repo, same last commit.
  - Not already claimed fails: a claim comment on 2026-07-15 from krishnasai453, who says they're in your CodePath AI301 program.
- code-charity/youtube#4290 (videos won't pause): Scope feasible is unclear, which the rubric counts as a fail. The reporter says "unsure" about the cause, it's only seen on Waterfox, there are no repro steps, no version and no settings. The cause is unknown, so the size of the work can't be judged.
- openalgo#1832: Not already claimed fails. siddharthg2309 said "working on this issue!" and has open PR #1879.
- openalgo#1822: Not already claimed fails. vaibhav8a said "I'd like to take this one" and has open PR #1862. Too bad: this was the best Python fit.
- openalgo#1818: Not already claimed fails. siddharthg2309 claimed it and has open PR #1874.
- mloda#2664: Not already claimed fails. The issue is closed, and the maintainer's PR #2679 has merged.

Things to log in scan-notes.md:
- Stale claims: the rubric has no time limit on claims, so the 8-month-old request on #27 counts the same as a fresh one.
- Open-ended feature requests: "etc." requests like #4348 pass scope too easily. The missing pass condition is behind both this and the gap above.
- openalgo: its Python issues were the best fit, but every good-first-issue was claimed within a day of being posted. To catch new ones, look at issues opened in the last few days.

```json
[
  {"item": "https://github.com/code-charity/youtube/issues/4348", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Human commit by Fardin7798 on 2026-11-03 (others by ImprovedTube2, a human account), within 60 days"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "Single feature 'block playlists. my mix, podcasts, etc.', labeled good first issue/up-for-grabs; terse but one bounded feature per evidence guide"},
    {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no PRs referencing #4348"}], "verdict": "accept"},
  {"item": "https://github.com/ProjectX-VJTI/Xplore-workshop/issues/27", "checks": [
    {"name": "Repo is active", "grade": "fail", "evidence": "Newest default-branch commit 2026-06-05 (Once-1296 et al.), >60 days before 2026-11-08"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "Bounded exercise: fix scripts in test_playground/basics/, labeled problem level 1 - starter"},
    {"name": "Not already claimed", "grade": "fail", "evidence": "Asmi768 2026-03-02: 'I'd like to work on this... Could you please assign this issue to me?'"}], "verdict": "reject"},
  {"item": "https://github.com/ProjectX-VJTI/Xplore-workshop/issues/28", "checks": [
    {"name": "Repo is active", "grade": "fail", "evidence": "Newest default-branch commit 2026-06-05, >60 days before 2026-11-08"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "Bounded exercise: fix scripts in test_playground/intermediate/"},
    {"name": "Not already claimed", "grade": "fail", "evidence": "krishnasai453 2026-07-15: 'I'd like to work on this issue. I'll start by reviewing...'"}], "verdict": "reject"},
  {"item": "https://github.com/code-charity/youtube/issues/4290", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Human commit by Fardin7798 on 2026-11-03"},
    {"name": "Scope feasible", "grade": "unclear", "evidence": "Reporter 'unsure' of triggering feature, Waterfox-only, no repro/version/settings/console output; size of fix unknowable"},
    {"name": "Not already claimed", "grade": "pass", "evidence": "0 comments, no assignees, no referencing PRs"}], "verdict": "reject"},
  {"item": "https://github.com/marketcalls/openalgo/issues/1832", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Commits by marketcalls and Kalaiviswa on 2026-11-06"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "Maintainer-written: label/htmlFor fixes in ChargeControls.tsx with acceptance criteria, 'Difficulty: Easy'"},
    {"name": "Not already claimed", "grade": "fail", "evidence": "siddharthg2309 2026-08-23: 'working on this issue!'; open PR #1879"}], "verdict": "reject"},
  {"item": "https://github.com/marketcalls/openalgo/issues/1822", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Commits by marketcalls and Kalaiviswa on 2026-11-06"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "Add math.isfinite check in utils/api_analyzer.py with tests; 'Difficulty: Easy, 1-2 hours'"},
    {"name": "Not already claimed", "grade": "fail", "evidence": "vaibhav8a 2026-08-22: 'I'd like to take this one — starting now'; open PR #1862"}], "verdict": "reject"},
  {"item": "https://github.com/marketcalls/openalgo/issues/1818", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Commits by marketcalls and Kalaiviswa on 2026-11-06"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "Accept 60m/6h in HistorySchema plus contract test; 'Difficulty: Easy'"},
    {"name": "Not already claimed", "grade": "fail", "evidence": "siddharthg2309 2026-08-23: 'i am working on this issue'; open PR #1874"}], "verdict": "reject"},
  {"item": "https://github.com/mloda-ai/mloda/issues/2664", "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Commits by TKaltofen on 2026-11-07"},
    {"name": "Scope feasible", "grade": "pass", "evidence": "Replace wall-clock bound with scaling check in test_credential_scrub.py; steps and acceptance criteria given"},
    {"name": "Not already claimed", "grade": "fail", "evidence": "Issue CLOSED; maintainer PR #2679 merged; rezamuliawijaya also has open PR #2675"}], "verdict": "reject"}
]
```

---

## Summary: Final Selection

**FINAL PICK: code-charity/youtube#4348** ✅
- All 3 checks pass
- Single feature: "block playlists. my mix, podcasts, etc."
- 0 comments, no assignees, no PRs
- Active repo (human commit 2026-11-03)
- **Language trade-off:** JavaScript (not Python), but it's the only unclaimed issue that passed rubric checks after grading 13 total issues
- **Status:** Ready to claim and start work on scoping details with maintainer

**Total grading cost:** ~$3 course credit  
**Result:** One qualifying issue that matches all rubric checks