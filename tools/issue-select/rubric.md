# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer activity | Repo facts: last 5 default-branch commits and maintainer first-response sample; issue Comments showing Owner, Member, or Collaborator activity. | Pass if at least one non-bot default-branch commit occurred within 90 days of the capture date OR the maintainer first-response sample shows at least one Owner, Member, or Collaborator response within 30 days. A bot commit alone does not satisfy this check unless it merged a human PR. | required |
| Repository in use | Repo facts: archived status, latest release, and last push to any branch. | Fail if the repository is archived. Otherwise pass if either the latest release or last push occurred within 180 days of the capture date. | required |
| Newcomer-sized scope | Issue body and Comments, including maintainer statements about implementation scope, issue labels, opener association, linked/mentioned PR history, and prior contribution attempts. | Pass when the issue requests one bounded outcome. Count scope by independent outcomes, not by the number of files, listed steps, suggested implementation approaches, or apparent technical complexity. Multiple related edits that all produce the same outcome still count as one bounded contribution. Multiple possible causes or suggested fixes for one reported bug also remain one bounded outcome unless the issue explicitly requires them as independent deliverables. A terse issue may pass, especially when opened by a maintainer/collaborator or labeled good-first-issue. Fail when the issue is explicitly an umbrella/tracking issue containing separate independent work items, is a pure usage/support question, has unresolved design debate with no maintainer-set direction, a maintainer states that it requires changes to core internals, or its history shows at least two abandoned implementation attempts or closed unmerged PRs indicating recurring difficulty. | required |
| Issue unclaimed | Repo facts for this issue: assignees and linked PRs; Comments for claim statements or PR references. | Pass if there is no current assignee, no open linked or comment-mentioned PR implementing the issue, and no unresolved comment indicating another contributor is currently working on it. Closed unmerged PRs count as abandoned attempts rather than active claims. | required |
| Contribution policy | Repo facts contribution-policy line, including CONTRIBUTING.md, .github contributor documentation, dedicated AI policy files, and relevant PR/issue templates. | Fail only if the repository explicitly bans AI-generated or AI-assisted contributions. Pass if AI use is allowed with conditions such as disclosure, testing, understanding, or human review, or if no AI restriction is stated. | required |
| First-issue signal | Issue labels and issue body, including good-first-issue or equivalent newcomer labels. | Pass if the issue has a good-first-issue or equivalent newcomer-oriented label or a maintainer explicitly identifies it as suitable for a new contributor. Otherwise mark unclear. | preferred |

## Verdict rule

Accept if every required check passes. Reject if any required check fails. For required checks, unclear counts as fail. Preferred checks never change an accept or reject verdict; they are used only to rank accepted issues. An unclear preferred check does not reject an issue.

