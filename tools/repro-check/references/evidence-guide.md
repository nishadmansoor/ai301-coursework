# Evidence guide: where proof lives in a reproduction package

## Environment

**Where it lives:** In the eval bundle, inspect the `repo-facts` block and the
repro report's environment record. In live mode, inspect the environment
record in the student's draft repro report and compare it with the issue
description and repository documentation when relevant.

**What good looks like:** The environment details that matter to the issue
are identified and match the issue's target, or a meaningful difference is
explicitly called out. The evidence should be sufficient to tell whether the
reported behavior was tested under the relevant conditions.

## Steps

**Where it lives:** In the repro report's reproduction procedure. In live mode,
use the student's draft repro report; in eval mode, use the reproduction steps
in the package bundle.

**What good looks like:** A stranger can start from the stated starting state,
follow the commands or actions in order, and reach the reported test or
trigger without needing an unstated step that changes the result.

## Behavior shown

**Where it lives:** In the repro report's output excerpts, logs, screenshots,
or other artifacts, read against the issue description in the issue context.
In eval mode, use only the artifacts and issue context in the bundle.

**What good looks like:** The observed artifact demonstrates the behavior the
issue actually describes, including the relevant error, output, or result.
Evidence of a related or adjacent behavior does not establish the issue.

## Honesty

**Where it lives:** Compare the claim comment and repro report's conclusion
with the issue context and the supporting artifacts. In eval mode, use the
claim comment, repro report, issue context, and repo-facts block in the bundle.

**What good looks like:** The conclusion matches what the evidence actually
establishes. A report that honestly says the issue could not be reproduced,
when its evidence supports that conclusion, can pass; a confident claim of
reproduction or resolution that the artifacts do not support should fail.

## Comms

**Where it lives:** Inspect the claim comment and repro comment against the
issue context and the repository's stated contribution conventions or policy.
In eval mode, use the communication text and any repository-policy information
included in the package bundle. In live mode, also consider the Path Review
house rules and the student's voice guide.

**What good looks like:** The comments make specific, evidence-backed claims
about the issue and the student's own work. They do not replace the student's
own reproduction with another person's work, and they follow applicable
repository communication requirements, including any required AI-use
disclosure.
