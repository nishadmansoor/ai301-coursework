# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

nishadmansoor


**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69#issuecomment-6049286338 

## Plan

Issue #69 is caused by the JSON output parser assuming that every successfully decoded JSON value is a dictionary. A top-level JSON array is decoded as a Python list, which reaches _parse_json_output() and causes data.items() to raise AttributeError.

Based on my reproduction above (commit `2f4e82f`, run with `pytest tests/unit/test_output_parser.py::TestOutputParser::test_json_array_fallback --runxfail -v`), the parser raises `AttributeError: 'list' object has no attribute 'items'` when given a top-level JSON array.

I plan to update `rag/generator/output_parser.py` to handle top-level JSON arrays while preserving the existing dictionary parsing behavior. Each array entry will be converted into one FeedbackSection, using an indexed section name, the entry converted to a string for content, and the existing confidence/suggestions contract. I will update the existing `test_json_array_fallback` test in `tests/unit/test_output_parser.py` to remove its xfail marker and verify that the array entries are returned through the normal `FeedbackSection` contract.

I will first run the focused JSON-array test, then the complete `tests/unit/test_output_parser.py` suite to check for regressions in the existing JSON object, plaintext, nested JSON, and other parser behavior. I will also run the repository lint and typecheck commands.

The scope is limited to the output parser and its existing unit test. I am not changing plaintext parsing, JSON detection, the `FeedbackSection` dataclass, or unrelated modules.

---

## Your branch

fix/69-json-array-fallback

**Evidence**

### Before the fix

Reproduction environment:

- Commit: `2f4e82f52efbcfcc57d65b3fa5348672163ca088`

- Python: `3.13.11`

- pytest: `9.1.1`

Command:

```bash

pytest tests/unit/test_output_parser.py::TestOutputParser::test_json_array_fallback --runxfail -v
```
Input used by the test:
raw_output = json.dumps(["First feedback item", "Second feedback item"])

Observed result:
AttributeError: 'list' object has no attribute 'items'

The failure occurred in rag/generator/output_parser.py when the top-level JSON array was passed to _parse_json_output() and the function attempted to call .items() on the resulting Python list. 

After the fix
Focused regression test:
```bash
pytest tests/unit/test_output_parser.py::TestOutputParser::test_json_array_fallback -v
```
Result:
1 passed

The test now verifies that the JSON array is returned as a list of two FeedbackSection objects and that the two feedback strings are preserved. 

Full parser test suite:
```bash
pytest tests/unit/test_output_parser.py -v
```

Result:
19 passed

Full unit test suite:
```bash
make test-unit
```

Result:
376 passed, 52 xfailed, 2 warnings

Lint:
```bash
make lint
```
Result:
All checks passed

Typecheck:
```bash
make typecheck
```
Result:
Success: no issues found in 76 source files


## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**
-Run 1: 15/20 agreement.
-Run 2: 19/20 agreement.

**Package analysis**

`pkg-05`: My rubric decided `accept`, while the gold label was `reject`. I accepted the package because the revised Unknowns and risks check allowed material uncertainty when it was explicitly acknowledged and the plan provided a bounded way to resolve it. The gold label rejected the package, so this was the one false accept in the final 19/20 run.

**Check rationale**

The diagnosis check in the final rubric reads:

> The diagnosis is consistent with the reproduced behavior and identifies a plausible cause or failure mechanism supported by the evidence. A cause may remain a hypothesis when the plan makes that uncertainty clear and gives a reasonable way to investigate it. The diagnosis must not contradict the reproduced evidence.

I revised this check to avoid requiring the exact root cause to be proven when the reproduction only establishes a failure mechanism. The revised wording still requires the diagnosis to be consistent with the evidence, prohibits contradictions, and requires a reasonable investigation path when the cause remains a hypothesis. This change made the rubric less strict about uncertainty and contributed to the improvement from 15/20 to 19/20.

**Trade-offs**

The revised rubric became more permissive about uncertainty in a diagnosis. This improved agreement from 15/20 to 19/20, but it also produced one false accept: `pkg-05`, which my rubric accepted while the gold label rejected. I accepted this trade-off because the rubric still requires the diagnosis to be consistent with the reproduction, explicitly acknowledge uncertainty, and provide a bounded way to investigate an unresolved cause.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
