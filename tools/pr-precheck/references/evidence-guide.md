# Evidence guide: where evidence lives in a PR package

Use this guide to locate the evidence required by rubric.md. In live
mode, inspect the working repository and its relevant GitHub issue or
PR materials. In eval mode, use only the supplied package bundle.
Never treat an unsupported claim as proof.

## Plan fidelity (harness category: silent-drift)

**Where it lives**

- The plan's scope, intended behavior, and files-to-touch list.
- The plan's `## Deviations` section, if present.
- The branch diff and changed-file list.
- The proposed PR title and description.
- In eval mode, the plan-context block, candidate diff, deviation notes,
  and candidate PR description.

**What good looks like**

Every substantive change fits the plan's stated boundary or is
explained in a deviation note. The diff's actual behavior agrees with
the PR description. An honestly documented and justified shortfall can
pass; unexplained changes, omissions, or inaccurate claims indicate
silent drift.

## Test evidence (harness category: not-tested)

**Where it lives**

- `test_evidence.md`, including reproduction steps and before-and-after
  observations.
- The test plan in `plan.md`, including commands, inputs, and expected
  results.
- Captured outcomes for relevant unit tests, integration tests, lint,
  type checks, and other applicable repository checks.
- In eval mode, the plan-context test plan and candidate package's
  test-evidence section.

**What good looks like**

The evidence identifies the behavior being tested, states the expected
result, and records the observed result or command outcome. Before-and-
after evidence makes the relevant behavior observable rather than
merely claiming that tests pass. If a check could not be run, the
limitation and reason are stated accurately; missing evidence must not
be represented as a successful result.

## Diff quality (harness category: unreviewable)

**Where it lives**

- The full branch diff against the default branch.
- The changed-file list and commit information.
- The plan's files-to-touch list and stated boundaries.
- In eval mode, the candidate diff and commit information in the bundle.

**What good looks like**

The intended fix is identifiable in the diff, and each substantive
change is within scope or explained by a documented deviation. Look
for debug leftovers, dead code, commented-out experiments, accidental
generated files, unrelated edits, and formatting churn that obscures
the fix. Do not fail a focused, reviewable change merely because it
could be shorter or more polished.

## Standards and comms (harness category: standards-wall)

**Where it lives**

- The repository's `.github/PULL_REQUEST_TEMPLATE.md`.
- `docs/CONTRIBUTING.md` and other applicable repository instructions.
- Relevant requirements or maintainer directions in the issue thread.
- The draft PR title and description, including required sections and
  AI-use or other disclosures.
- In eval mode, the repo-facts block's template asks and stated policy,
  plus the candidate PR description.

**What good looks like**

The description addresses applicable required template sections with
truthful, relevant content, follows repository instructions, identifies
the issue as required, and includes required disclosures. A section
that genuinely does not apply can say so with a reason. Boilerplate,
omitted required sections, missing required disclosure, or ignored
explicit instructions indicate a standards failure. Claims that the
description makes about what the diff implements belong under plan
fidelity.
