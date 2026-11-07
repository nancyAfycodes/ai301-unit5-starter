# Search strategy: where your scout looks, and why

## Queries

<!-- Each query traces to a sentence in your fit profile (scope.md).
Test each one in your terminal before the scout runs it. -->

<!-- From profile: "comfortable with Python, willing to work in JavaScript as a way to improve" -->
gh search issues --language python --language javascript --label "good first issue" --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

<!-- From profile: "want to get better at debugging" -->
gh search issues --language python --language javascript --label bug --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

<!-- From profile: "get better at debugging and larger codebases" -->
gh search issues --language python --language javascript --label "tier-2" --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

<!-- From profile: "willing to work in JavaScript" (frontend work often involves JS) -->
gh search issues --language python --language javascript --label frontend --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

## Ranking filters

Apply these rules in order to rank results from all queries:

1. **Drop any issue with >5 comments** — if `commentsCount` is > 5, skip it. High comment counts often mean the issue is already being discussed or claimed in comments (this repo uses comment claims, not assignees).
2. **Prefer bugs** — issues with the `bug` label rank higher. This aligns with your goal to get better at debugging.
3. **Prefer debugging-related labels over CI/infrastructure** — if an issue has `bug`, `safety`, `ingestion`, or `rag` labels, rank it higher than `devops`, `enhancement`, or `api` alone. This filters out feature work mislabeled as bugs.
4. **Prefer tier-2 and tier-3 over tier-1** — issues with `tier-2` or `tier-3` labels rank higher than `tier-1`. These represent larger codebases.
5. **Fewest comments first** — sort by `commentsCount` ascending. Ties go to issues updated more recently.

## How many to grade

Grade the top **5** ranked results per scan.