# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan fidelity | The complete diff and changed files read against the plan's stated scope, implementation steps, and any recorded deviation notes, using Plan fidelity in the evidence guide. | Pass if the diff implements the work promised by the plan without silently adding unrelated work or omitting planned work that the PR presents as completed. A difference from the original plan still passes when the deviation is recorded in the plan with what changed and why. An honestly disclosed limitation or deferred edge does not fail this check by itself. | required |
| Description fidelity | The PR title and description read against the actual diff, commits, plan, and recorded deviations, using Plan fidelity and Standards and comms in the evidence guide. | Pass if the title and description accurately describe what the diff actually does and do not claim behavior, scope, tests, or completeness that the package does not support. Disclosed limitations, deferred work, and recorded deviations pass when described honestly. | required |
| Behavior evidence | The PR's test evidence read against the plan's test plan, original reproduction evidence, and the behavior changed by the diff, using Test evidence in the evidence guide. | Pass if the evidence shows the relevant behavior was actually exercised and gives an observable before/after or equivalent result that demonstrates the claimed change. A command name or statement that testing was done without an observable outcome does not pass. | required |
| Repository checks | The test evidence read against the repository's stated test, lint, build, or validation requirements in the repo-facts block and the plan's test plan, using Test evidence in the evidence guide. | Pass if the applicable repository checks were actually run and their outcomes are visible in the evidence. If a stated check cannot be run, pass only when the limitation and its effect on confidence are explicitly disclosed rather than silently omitted. | required |
| Reviewable diff | The complete diff, changed files, and commits read against the planned change, using Diff quality in the evidence guide. | Pass if the diff contains the implementation and only supporting changes needed for that work, without unrelated cleanup, generated debris, debugging leftovers, accidental files, or unrelated hunks that would prevent a reviewer from isolating the intended change. | required |
| Repository standards | The PR title and description read against the repo-facts block's PR-template requirements, contribution policy, and disclosure requirements, using Standards and comms in the evidence guide. | Pass if every applicable repository requirement represented in the package is satisfied, including required PR-template information and any required AI-use disclosure. If a requirement does not apply, its absence does not fail the check. | required |

## Verdict rule

Accept only if every required check passes. Reject if any required
check fails or is unclear. Preferred checks, if any are added later,
never change the verdict. Treat `unclear` as fail because a PR that
cannot be verified from the available evidence is not ready to submit.
