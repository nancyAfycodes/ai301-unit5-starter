# Search strategy: where your scout looks, and why

## Queries

<!-- From profile: "I'm comfortable with Python, but not necessarily JavaScript." -->
gh search issues "language:python" --label "good first issue" --no-assignee --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

<!-- From profile: "I want to get better at debugging and working with larger codebases." -->
gh search issues "language:python" --label bug --label "help wanted" --no-assignee --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

<!-- From profile: "I'm willing to work in JavaScript as a way to improve upon my skills and coding ability in JavaScript." -->
gh search issues "language:javascript" --label bug --no-assignee --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

## Ranking filters

Apply these rules in order to rank results from all queries:

1. **Drop any issue with an assignee.** If `assignees` is not empty, someone already has it.
2. **Drop any issue with more than 5 comments.** If `commentsCount` > 5, skip it. High counts often mean the issue is being discussed or claimed in comments.
3. **Drop any issue not updated in the last 90 days.** Use `updatedAt`. Stale issues are often abandoned or already fixed.
4. **Prefer bugs.** Issues with the `bug` label rank higher, which matches my goal of getting better at debugging.
5. **Prefer Python over JavaScript,** but keep at least two JavaScript issues in the top five so I still get the practice.
6. **Fewest comments first.** Sort by `commentsCount` ascending. Ties go to the more recently updated issue.

## How many to grade

5