# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Grounded diagnosis | The plan's stated cause read against the behavior, steps, and observed result in the repro evidence, using Diagnosis and grounding in the evidence guide. | Pass if the stated cause is consistent with and supported by the reproduced behavior; if the evidence does not establish the cause, the plan identifies it as a hypothesis or unknown rather than a confirmed fact. | required |
| Bounded scope | The plan's in-scope and not-in-scope statements and named files or areas, read against the issue context and repro evidence, using Scope in the evidence guide. | Pass if the plan proposes one bounded change directed at the reproduced problem and keeps unrelated cleanup, rewrites, features, or other drive-by work outside the change. | required |
| Cause-target alignment | The plan's proposed change read against its stated diagnosis and the repro evidence, using Diagnosis and grounding and Scope in the evidence guide. | Pass if the proposed change addresses the cause or code path supported by the evidence rather than only masking the reproduced symptom. If the cause is still a hypothesis, the plan includes verifying that hypothesis before depending on it for the change. | required |
| Executable plan | The plan's implementation steps, named files or areas, proposed approach, and order of work, read against the issue and repro evidence, using Executability in the evidence guide. | Pass if another contributor could begin implementing the proposed change without needing the author to explain the intended approach, because the plan identifies the relevant code or area, what will change, and how that work connects to the reproduced problem. | required |
| Decisive test plan | The plan's test plan read against the original reproduction steps, code path, and observed result, using Test plan in the evidence guide. | Pass if the proposed test exercises the relevant behavior and names an observable result that would determine whether the reproduced problem was fixed. A generic test-suite run alone does not pass unless it directly demonstrates that behavior. | required |
| Honest uncertainty | The plan's claims about cause, assumptions, risks, unknowns, and any deviations read against the issue and repro evidence, using Honesty in the evidence guide. | Pass if verified facts are distinguished from assumptions or unknowns, and unresolved questions that could affect the implementation are stated rather than presented as certainty. If a deviation has occurred, the plan records what changed and why. | required |
| Thread and conventions | The candidate plan comment read against the issue thread or thread highlights and the repo's stated contribution requirements in the repo-facts block, using Comms in the evidence guide. | Pass if the plan comment follows relevant maintainer guidance or constraints and complies with applicable repository requirements, including required templates or AI-use disclosures. | required |


## Verdict rule

Accept only if every required check passes. Reject if any required check fails or is unclear. Preferred checks, if any are added later, never change the verdict. Treat unclear as fail because a plan that cannot be verified from the available package evidence is not ready to post and build from.

