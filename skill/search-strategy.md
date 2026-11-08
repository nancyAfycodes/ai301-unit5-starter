# Search strategy: where your scout looks, and why

## Queries

<!-- From profile: "I'm comfortable with Python, but not necessarily JavaScript." -->
gh search issues "language:python" --label "good first issue" --no-assignee --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url,author,authorAssociation,createdAt

<!-- From profile: "I want to get better at debugging and working with larger codebases." -->
gh search issues "language:python" --label bug --label "help wanted" --no-assignee --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url,author,authorAssociation,createdAt

<!-- From profile: "For now I want to work in Python, and I'm avoiding issues that need in-depth knowledge of unfamiliar languages." -->
gh search issues "language:python" --label "good first issue" --label bug --no-assignee --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url,author,authorAssociation,createdAt

## Ranking filters

Apply these rules in order to rank results from all queries:

1. Drop any issue with an assignee.
2. Drop any issue with more than 5 comments.
3. Drop any issue not updated in the last 90 days.
4. Drop any issue whose title contains "Escrowed" or a "$" bounty amount.
5. Deprioritize tracking issues: titles that reference two or more issue numbers, like "(#237, #239, #240)".
6. Keep at most one issue per repository (repository.nameWithOwner), the best-ranked one.
7. Prefer bugs.
8. Prefer Python.
9. Fewest comments first. Ties go to the more recently updated issue.

## How many to grade

5