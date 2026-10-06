# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

I am a student contributor learning through hands-on open-source work. When I comment on an issue, I am investigating a specific reported behavior and sharing what I can verify from my own reproduction attempt. Readers can expect me to be friendly, specific, and clear about what I observed versus what I have not confirmed.

## Rules I write by

### Rule: Say only what I verified

I separate what I observed from what I think may be happening. I do not present an assumption or possible cause as a confirmed fact.

- Wrong: "The bug is caused by the faithfulness checker not handling short claims."
- Right: "I reproduced the reported behavior with a short claim; I have not confirmed the underlying cause."

### Rule: Claim the investigation, not the fix

When claiming an issue, I say what I plan to investigate and report back on. I do not promise that I will fix it, predict the result, or give a completion date before doing the work.

- Wrong: "I'll fix this issue by tomorrow."
- Right: "I'd like to reproduce this issue. I'll test the reported behavior and post my environment, steps, and results here."

### Rule: Make the result specific

I name the behavior I tested and what actually happened instead of using vague statements such as "it worked," "same issue," or "confirmed."

- Wrong: "I tested this and got the same problem."
- Right: "I followed the reported steps and observed the same error after submitting the input; I included the output from my run below."

### Rule: Be honest when I cannot reproduce

A failed reproduction attempt is still useful evidence. I report the conditions I tested and what happened instead of forcing the result to match the issue.

- Wrong: "Confirmed the bug," when my run did not show the reported behavior.
- Right: "I wasn't able to reproduce the reported behavior in the environment below. I followed the listed trigger, but my run completed without the reported error."

### Rule: Respect the repository's communication rules

Before posting, I check the repository's contribution instructions, templates, and disclosure requirements and follow any that apply to my comment.

- Wrong: "Here is my reproduction report," while omitting a disclosure the repository explicitly requires.
- Right: "Here is my reproduction report," with the repository's required disclosure included when applicable.

### Rule: Make the PR title earn the review

I use the title to name the specific behavior or change the PR actually
delivers. I do not use a vague title or claim broader work than the
diff contains.

- Wrong: "Fix issue and improve validation"
- Right: "Handle empty input in the faithfulness checker"

### Rule: Make the description match the diff

I describe what the submitted diff actually changes, not what I hoped
to build or what the original plan predicted. If implementation
changed from the plan, I describe the implemented result and make sure
the deviation is recorded.

- Wrong: "This PR implements the planned validation flow," when the
  diff omits part of that flow or adds unmentioned behavior.
- Right: "This PR adds the validation path described in the plan. The
  helper change needed during implementation is recorded as a
  deviation in plan.md."

### Rule: Disclose shortfalls without hiding or apologizing for them

If a test could not run, an edge case is deferred, or the implementation
has another known limitation, I state that directly and describe what
the available evidence does show. I do not turn a limitation into a
claim of complete coverage or bury it in apologetic language.

- Wrong: "Everything works," when one required environment was not
  available to test.
- Right: "The targeted reproduction now passes and the repository test
  suite passes. I could not run the optional platform-specific check
  in my environment."

## Things I never post

- A promise that I will fix an issue before I have investigated it.
- A deadline or completion date I cannot guarantee.
- A claim that I reproduced something when my evidence does not show it.
- A guessed root cause presented as fact.
- "Same as above" or another piggyback reproduction without my own evidence.
- A comment that ignores an applicable repository template, contribution rule, or required AI-assistance disclosure.
- A PR title that promises broader work than the diff contains.
- A PR description that hides a deviation, deferred edge, or known
  limitation.
- A claim of test coverage or successful behavior that the captured
  evidence does not show.
