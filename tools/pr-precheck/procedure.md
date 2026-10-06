# Procedure: how this tool grades a PR package

## Read order

1. In eval mode, read the issue context and repo-facts block first.
   Record the reported problem, relevant maintainer instructions, the
   repository's PR-template requirements, contribution requirements,
   required checks, and any disclosure policy that applies.

2. Read the plan-context block before reading the candidate PR. Record
   the plan's stated scope and boundary, implementation steps, test
   plan, expected observable result, and any recorded deviation notes.

3. Read the original reproduction evidence associated with the plan.
   Record the behavior that was reproduced, the relevant steps, and
   the observed result so later test evidence can be compared with the
   behavior the change was intended to fix.

4. Read the candidate PR's commit list and complete diff. Record every
   changed file and the purpose visible in each changed hunk. Compare
   these facts with the plan only after recording what the plan
   promised.

5. Read the candidate PR's test evidence after the diff. Record what
   behavior was exercised, the commands or checks that were run, and
   the observable outcomes shown.

6. Read the candidate PR title and description last. Record the scope,
   behavior, testing, completeness, limitations, and deviations that
   the PR claims. Reading the description last prevents its summary
   from shaping the interpretation of what the diff and evidence
   actually show.

7. In live mode, after the scope and voice-guide steps required by
   SKILL.md, use the same order: issue and repository requirements,
   `plan.md` with deviation notes, original reproduction evidence,
   complete branch diff and commits, captured test evidence, then the
   draft PR title and description.

## Evidence gathering

1. Plan fidelity: Record the plan's promised scope, boundary,
   implementation work, and deviation notes. Record every changed file
   and the relevant work shown by the diff. Pair each meaningful diff
   change with the planned work or a recorded deviation. Also record
   planned work that the PR presents as completed but that is not
   visible in the diff.

2. Description fidelity: Record the PR title and description's claims
   about scope, behavior, testing, completeness, limitations, and
   deviations. Compare each material claim with the diff, test
   evidence, plan, and recorded deviation notes. Record unsupported or
   contradictory claims.

3. Test evidence: Record the behavior and expected result named by the
   plan's test plan and original reproduction evidence. Then record
   what the PR evidence actually exercised and the observable outcome.
   Separately record every applicable repository test, lint, build, or
   validation requirement and whether its outcome is shown.

4. Diff quality: Record changed files and hunks that implement or
   directly support the planned change. Separately record unrelated
   cleanup, accidental files, debugging output, dead code,
   commented-out blocks, unnecessary formatting churn, or other
   unrelated changes that make the intended work harder to isolate.

5. Standards and comms: Record every applicable requirement from the
   repository's PR template, contribution instructions, stated policy,
   disclosure requirements, and relevant explicit maintainer
   direction. For each requirement, record where the candidate PR
   satisfies it or whether it is absent. Do not require content for a
   requirement that clearly does not apply.

6. Gather each fact once and reuse it for checks that depend on the
   same evidence. In eval mode, do not infer missing facts or use
   information outside the package.

## Check execution

1. Grade the checks in the order they appear in `rubric.md`: Plan
   fidelity, Description fidelity, Behavior evidence, Repository
   checks, Reviewable diff, then Repository standards.

2. For each check, use only the evidence identified by that rubric row
   and gathered from the corresponding evidence-guide family. Apply
   the written pass condition exactly; do not add requirements because
   a package feels incomplete or unusual.

3. Grade `pass` when the gathered evidence satisfies the complete pass
   condition. Grade `fail` when the available evidence shows that the
   pass condition is not satisfied.

4. Grade `unclear` when evidence required to decide the check is
   genuinely absent or insufficient. Do not assume an unstated test
   passed, an unmentioned change was intended, or a missing repository
   requirement was satisfied.

5. An honestly disclosed limitation, deferred edge, failed optional
   attempt, or recorded plan deviation does not fail a check merely
   because the outcome is imperfect. Grade the check according to
   whether the package satisfies that check's stated pass condition
   and represents the shortfall honestly.

6. Record one specific fact or short quote that decided each check's
   grade. Do not use conclusions such as "looks good" or "seems
   correct" as evidence.

7. Reuse previously gathered evidence for later checks. Re-read the
   package only when evidence required by the current check was not
   already recorded.

## Verdict assembly

1. After all checks have been graded, apply the verdict rule in
   `rubric.md` exactly as written.

2. Return `accept` only when every required check is `pass`.

3. Return `reject` when any required check is `fail` or `unclear`.
   Preferred checks, if any are added later, never change the verdict.

4. Include every rubric check in the output with its name, grade, and
   one specific fact or short quote that decided the grade.

5. For a rejecting verdict, identify the first required check in
   rubric order whose grade is `fail` or `unclear` as the deciding
   check. Use that check's recorded evidence as the primary reason for
   the hold in the readable summary. If additional required checks
   fail or are unclear, report their evidence as additional reasons.

6. For an accepting verdict, retain the deciding evidence for every
   required check and state that all required checks passed.

7. Produce the final output using the exact JSON structure required by
   `SKILL.md`. Use only `accept` or `reject` for the verdict. The
   fenced JSON block must be valid and must be the final content in
   the output, with nothing after it.
