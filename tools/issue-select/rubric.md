# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer activity | The last 5 default-branch commits under Repo facts | At least 1 of the last 5 commits was authored by a human maintainer within 60 days of the repo-facts capture date | required |
| Repo activity | The archived status and last push under Repo facts | The repo is not archived and its last push was within 60 days of the repo-facts capture date | required |
| Bounded newcomer scope | Issue body and comment thread | Passes if the issue identifies one specific bug, feature, or documentation change with a clear desired outcome. Multiple possible causes or implementation approaches do not by themselves make the issue fail. Reject only if the issue is explicitly an umbrella/tracking issue, a pure usage/support question, or a material requirement is unresolved such that the contributor cannot determine what outcome needs to be implemented | required |
| Issue availability | Issue assignees, linked PRs, and comment thread | Passes if there are no current assignees, no open linked PRs, and no evidence that another contributor or maintainer currently owns or is actively working on the issue. Reject if the thread shows repeated prior claims or work attempts by contributors and the issue remains unresolved after those attempts, indicating that the issue has a history of unsuccessful ownership or stalled work. Student claim comments do not cause failure by themselves | required |
| Contribution policy | Contribution policy under Repo facts, including any dedicated AI policy files and linked contributor documentation | Passes if the repository does not explicitly prohibit AI-assisted or AI-generated contributions; an AI-use disclosure, testing, review, or understanding requirement does not cause failure | required |

## Verdict rule

Accept an issue if every required check passes. Reject an issue if any required check fails. An unclear result on any required check counts as a failure. Preferred checks, if added later, never change the accept/reject verdict and are used only to rank accepted issues.