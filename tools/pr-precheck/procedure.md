# Procedure: how this tool grades a PR package

## Read order

1. In live mode, read `scope.md` first and confirm that the package
   belongs to the specified repository. Stop if the repository is out
   of scope or the repository field is an unfilled placeholder.
2. Read the issue thread and repository facts available in the package.
   In live mode, inspect the issue, `.github/PULL_REQUEST_TEMPLATE.md`,
   and `docs/CONTRIBUTING.md` when present. Record the issue's intended
   behavior, relevant maintainer instructions, required PR sections,
   and applicable contribution or disclosure rules.
3. Read the complete plan, including its scope, intended behavior,
   files to touch, test plan, and any `## Deviations` section. Record
   what the change is supposed to do, what is outside its boundary,
   and any justified or incomplete work already disclosed.
4. Read the complete branch diff and changed-file list against the
   default branch. In live mode, use `git diff main...HEAD` and inspect
   the relevant changed files. Record what actually changed and whether
   the diff contains unrelated edits or leftover debris.
5. Read the test evidence and compare it with the plan's test plan and
   reproduction steps. Record the commands run, inputs, expected
   behavior, observed before-and-after behavior, and the outcomes of
   relevant repository checks.
6. Read the draft PR title and description. Compare every substantive
   claim about the change and its test results with the diff and test
   evidence. Compare the description with applicable template sections,
   repository instructions, and disclosure requirements.
7. In eval mode, use only the supplied package bundle for all these
   steps. Do not fetch external evidence or fill gaps with assumptions.

## Evidence gathering

1. For Silent drift, compare the plan's scope and intended behavior
   with the diff's changed files and actual implementation. Check
   whether omissions or additions are explained in `## Deviations`.
   Compare the draft title and description with the diff. Record each
   material mismatch, unexplained omission, or inaccurate claim.
2. For Not tested, compare `test_evidence.md` with the plan's test plan
   and reproduction steps. Identify the behavior under test, expected
   result, actual result, and recorded command outcome. Inspect relevant
   unit, integration, lint, type-check, or other repository checks when
   evidence is available. Record missing evidence and any disclosed
   reason a check could not be run.
3. For Unreviewable, inspect the diff and changed-file list against the
   plan's boundary. Identify debug leftovers, dead code, commented-out
   experiments, accidental generated files, unrelated changes, or
   formatting churn that obscures the fix. Record whether the intended
   change remains identifiable and whether each substantive change is
   in scope or explained by a deviation.
4. For Standards wall, compare the draft PR description with the
   repository's template, contributing instructions, and applicable
   maintainer directions. Record which required sections are answered,
   whether the issue is identified, whether testing claims are truthful,
   and whether required AI-use or other disclosures are present.
   Treat a description's inaccurate claims about the diff as Silent
   drift rather than counting the same mismatch only as a communication
   problem.
5. For every check, record the specific observation or short quote that
   supports the grade. Distinguish missing evidence from evidence that
   demonstrates a failure. Do not treat a claim in the description as
   proof that the claimed work or test occurred.

## Check execution

1. Grade Silent drift first. Decide whether the diff and description
   match the plan and its documented deviations. A justified and
   honestly disclosed shortfall may pass if the remaining work and
   limitations are represented accurately.
2. Grade Not tested next. Decide whether the available evidence
   demonstrates relevant behavior and reports the outcomes of checks
   that were run. Do not accept an unsupported claim that tests passed.
   Do not automatically reject an honestly disclosed limitation solely
   because a check could not be run; apply the rubric's pass condition.
3. Grade Unreviewable next. Decide whether the diff is reviewable and
   whether unrelated changes or debris materially obscure the intended
   fix. Do not fail a change merely because it could be shorter or
   more polished.
4. Grade Standards wall last. Decide whether applicable repository
   requirements, template asks, maintainer instructions, and required
   disclosures have been addressed with truthful content.
5. Apply the pass condition in `rubric.md` to the observed outcome of
   each check. Do not award a pass just because a file or section
   exists, and do not invent requirements that are absent from the
   rubric or applicable repository instructions.
6. If evidence is genuinely insufficient to decide a check, grade it
   `unclear`. Do not infer a favorable result from missing evidence.
   Follow the rubric's explicit rule for how `unclear` affects the
   verdict.
7. Keep grades distinct when one fact is relevant to more than one
   check. For example, a misleading description claim belongs under
   Silent drift; missing required template content belongs under
   Standards wall. Explain each grade with its own relevant evidence.

## Verdict assembly

1. Apply the verdict rule in `rubric.md` to all four checks in rubric
   order: Silent drift, Not tested, Unreviewable, Standards wall.
2. Accept only when every required check passes. Reject if any required
   check fails or remains unclear under the rubric's uncertainty rule.
3. If more than one required check fails or is unclear, identify the
   first failing required check in rubric order as the primary deciding
   check. The readable summary may also report other failed checks.
4. For each check, provide its name, grade, and one-line evidence
   describing the observation that determined the grade. Do not claim
   that commands, tests, or reviews succeeded unless the package
   contains evidence of that outcome.
5. End with the exact JSON schema required by `SKILL.md`, using the
   PR URL or bundle identifier as `item`, all four checks in rubric
   order, and the binary `accept` or `reject` verdict. The final fenced
   JSON block must be valid, and nothing may follow it.
