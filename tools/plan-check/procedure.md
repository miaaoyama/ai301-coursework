# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

1. In eval mode, read the issue context and repo-facts block first. Record the reported problem, any maintainer constraints or requests, and any repository contribution requirements that apply.

2. Read the repro-evidence block next. Record the reproduction steps, the behavior that was actually observed, and what the evidence does and does not establish about the cause.

3. Read the candidate plan after the issue and reproduction evidence. Record its stated diagnosis, scope, proposed implementation approach, test plan, assumptions or unknowns, and any deviations.

4. Read the candidate plan comment last. Record whether it accurately represents the proposed work and whether it responds to relevant thread guidance and repository conventions.

5. In live mode, after the scope and voice-guide steps required by SKILL.md, use the same order: issue thread and repository rules, posted reproduction evidence, draft plan, then draft plan comment.

Read the issue and reproduction evidence before the candidate plan so the plan's claims are judged against the existing evidence rather than allowing the plan's explanation to shape the interpretation of that evidence.

## Evidence gathering

1. Diagnosis and grounding: From the repro evidence, record the observed behavior and any facts that support or limit a causal explanation. From the candidate plan, record the stated cause. Use the Diagnosis and grounding section of the evidence guide to compare them.

2. Scope: Record the plan's in-scope work, not-in-scope boundaries, and named files or areas. Compare them with the issue and reproduced problem using the Scope section of the evidence guide.

3. Executability: Record the implementation steps, relevant files or code areas, proposed approach, and order of work. Use the Executability section of the evidence guide to determine whether another contributor has enough information to begin.

4. Test plan: Record the original reproduction steps and observed result, then record the plan's proposed test and expected observable result. Use the Test plan section of the evidence guide to determine whether the proposed test would demonstrate that the reproduced behavior changed.

5. Honesty: Record statements presented as verified facts separately from hypotheses, assumptions, risks, unknowns, and deviations. Compare those claims with the issue and repro evidence using the Honesty section of the evidence guide.

6. Comms: Record relevant maintainer guidance or constraints from the issue thread and applicable contribution requirements from the repo-facts block. Compare those with the candidate plan comment using the Comms section of the evidence guide.

7. Gather each fact once and reuse it for checks that rely on the same evidence. Do not infer missing evidence or use information outside the package in eval mode.

## Check execution

1. Grade the checks in the order they appear in rubric.md: Grounded diagnosis, Bounded scope, Cause-target alignment, Executable plan, Decisive test plan, Honest uncertainty, then Thread and conventions.

2. For each check, use only the evidence gathered for the evidence families named by that rubric row. Apply the pass condition exactly as written in rubric.md rather than adding a new requirement during grading.

3. Grade a check pass when the gathered evidence satisfies its pass condition. Grade it fail when the evidence shows that the pass condition is not satisfied.

4. Grade a check unclear when the evidence needed to decide the check is genuinely absent or insufficient. Do not infer missing facts, assume unstated intent, or turn an absence of evidence into evidence that the condition passed.

5. Record one specific fact or short quote that decided each grade. Do not use conclusions such as "looks good" as evidence.

6. Reuse previously gathered evidence when a later check depends on the same facts. Re-read the package only when the evidence needed for that check was not already recorded; do not change an earlier grade merely because a later check produces a different judgment.

## Verdict assembly

1. After all checks have been graded, apply the verdict rule from rubric.md exactly as written.

2. Return accept only when every required check has a grade of pass.

3. Return reject when any required check has a grade of fail or unclear. Preferred checks, if any are added later, do not change the verdict.

4. For every check, include its name, grade, and one specific fact or short quote from the gathered evidence that decided the grade.

5. For a rejecting verdict, make the evidence for each failing or unclear required check explicit so the reason the package is being held can be identified. For an accepting verdict, retain the deciding evidence for every required check.

6. Produce the final output in the JSON structure required by SKILL.md, using only accept or reject for the verdict. The fenced JSON block must be valid and must be the final content in the output.
