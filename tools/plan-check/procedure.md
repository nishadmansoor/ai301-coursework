# Procedure: how this skill grades a plan package

## Read order

1. Read the issue/thread evidence identified by the evidence guide and note the
   issue target, relevant thread requirements, and repository conventions.
2. Read the reproduction evidence before reading the proposed plan. Record the
   reproduced environment, commands or inputs, observed result, and the failure
   location or behavior established by the reproduction.
3. Read the repo-facts block and record repository-specific conventions,
   relevant files, available tests, and facts needed to judge the proposed
   scope or implementation.
4. Read the complete plan, including the diagnosis, scope, files to touch,
   approach, test plan, risks and unknowns, quoted reproduction evidence, and
   Deviations section if present.
5. Read the draft plan comment and compare it with the plan. Record any
   differences that would make the posted comment materially different from
   the plan being graded.
6. Keep the reproduction evidence as the baseline for judging the diagnosis,
   cause-targeting, and test plan. Do not let the proposed fix redefine what
   the reproduction established.

## Evidence gathering

1. For the Diagnosis check, locate the plan's diagnosis and quoted
   reproduction evidence. Compare them with the reproduction's observed
   result and failure location. Record whether the diagnosis is consistent
   with the evidence and whether its stated cause is established, plausible,
   or contradicted.
2. For the Scope check, locate the plan's explicit scope statement and files
   to touch. Compare them with the issue target, reproduction evidence, and
   repo-facts block. Record what the plan changes, what it explicitly does
   not change, and any unrelated work included.
3. For the Cause-targeting check, locate the approach and files-to-touch list.
   Compare the proposed change with the diagnosed failure mechanism and the
   relevant failure path established by the reproduction. Record whether the
   plan targets that mechanism/path or merely suppresses the symptom.
4. For the Executability check, locate the approach and implementation steps.
   Compare them with the files-to-touch list and repo-facts block. Record
   whether another developer has enough direction to begin the work. A
   bounded investigation step is acceptable when the plan explains what will
   be investigated and how the result will determine the implementation.
5. For the Test plan check, locate the plan's test commands, inputs, expected
   results, and regression checks. Compare them with the original
   reproduction commands and observed failure. Record the observable result
   that would demonstrate the bug is fixed and note relevant controls or
   regression behavior when applicable.
6. For the Unknowns and risks check, locate the plan's risks and unknowns and
   compare them with claims made in the diagnosis, scope, approach, and test
   plan. Record material assumptions that are either acknowledged with a
   resolution path or presented as established facts without evidence.
7. For the Thread and conventions check, locate the draft comment and compare
   it with the issue/thread highlights and repo-facts block. Record whether it
   accurately represents the plan and follows relevant repository and
   coordination conventions.

## Check execution

1. Grade the Diagnosis check first because it establishes the evidence-supported
   problem and any reasonable hypothesis that the remaining checks must address.
2. Grade Scope and Cause-targeting next. Use the reproduced failure as the
   baseline rather than assuming that the plan's proposed implementation is
   correct.
3. Grade Executability after Scope and Cause-targeting. Pass when the plan
   provides enough direction to begin the work or a bounded investigation that
   will determine the remaining implementation detail.
4. Grade Test plan after Diagnosis and Executability. The test must exercise the
   real reproduced behavior and state an observable expected result; it does
   not need to eliminate every possible implementation uncertainty before
   building begins.
5. Grade Unknowns and risks after reading the other plan sections. Do not fail
   an explicitly acknowledged unknown merely because it remains unresolved;
   fail when material uncertainty is hidden, contradicted, or left without a
   reasonable resolution path.
6. Grade Thread and conventions last, using the issue/thread evidence and
   repo-facts block.
7. If evidence required by a check is genuinely absent, grade that check
   `unclear` rather than inferring a favorable result.
8. Do not award a pass because a plan section exists or because the writing is
   detailed. Grade the outcome described by the check's pass condition.
9. Do not require wording, headings, section length, or formatting unless the
   requirement is itself a repository or thread convention relevant to the
   check.

## Verdict assembly

1. Apply the verdict rule in rubric.md to all seven required checks.
2. Treat every `unclear` result as a fail.
3. Accept only when every required check passes.
4. Reject when any required check fails or is unclear.
5. For the final result, identify the failed or unclear required check that
   determines the verdict and summarize the evidence supporting that grade.
6. If multiple required checks fail, report the most direct deciding failures
   rather than replacing them with a general statement that the plan is weak.
