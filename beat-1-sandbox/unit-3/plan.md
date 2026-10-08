# Plan: Fix JSON array fallback in output parser

## Diagnosis

Issue #69 occurs when `parse_review_output()` receives valid top-level JSON

that is an array rather than an object. The reproduction showed that

`json.loads(raw)` successfully parses the input into a Python list, but

`_parse_json_output()` assumes the parsed value is a dictionary and calls

`data.items()`. Because lists do not provide `.items()`, the parser raises

`AttributeError` instead of returning its normal `list[FeedbackSection]`

result.

The existing `test_json_array_fallback` test is marked `xfail` specifically

for issue #69 and uses a top-level JSON array containing two feedback strings.

The fix should make that existing case parse successfully without changing

the existing dictionary-based JSON behavior.

## Scope

### In scope

- Update `rag/generator/output_parser.py` so `_parse_json_output()` handles

top-level JSON arrays as well as JSON objects.

- Preserve the existing behavior for dictionary/object JSON.

- Update

`tests/unit/test_output_parser.py::TestOutputParser::test_json_array_fallback`

to test the intended successful array behavior and remove its issue #69

`xfail` marker.

- Run the focused regression test and the complete output-parser unit test

file.

### Out of scope

- Changes to plaintext parsing.

- Changes to JSON code-fence detection or raw JSON detection.

- Changes to the `FeedbackSection` dataclass.

- Changes to unrelated parser behavior or other modules.

## Files to touch

- `rag/generator/output_parser.py`

- Update `_parse_json_output()` to branch appropriately for a top-level

list while retaining the current dictionary parsing path.

- `tests/unit/test_output_parser.py`

- Remove the `xfail` from `test_json_array_fallback`.

- Add assertions that verify the two array entries are returned as

`FeedbackSection` objects with their feedback content preserved.

## Approach

1. Inspect the parsed value received by `_parse_json_output()` and add an

explicit list-handling path before the existing dictionary `.items()` loop.

2. For a top-level JSON array, convert the array entries into the existing

`FeedbackSection` return contract, preserving the feedback content and

avoiding assumptions that the parsed JSON must be a dictionary.

3. Preserve the existing dictionary/object path unchanged for current JSON

object inputs.

4. Handle the reproduced string-array case without causing another type

error, while keeping the parser's existing return type consistent.

5. Update the existing issue #69 test so it verifies successful parsing rather

   than expecting the current xfail behavior. The test should verify that the

   result is a list, contains two feedback sections, and preserves the two

   input feedback strings.

6. Run the focused JSON-array test first.

7. Run the complete `tests/unit/test_output_parser.py` suite to verify that

   existing object, plaintext, nested JSON, suggestions, and other parser

   behavior still passes.

## Test plan

### Original reproduction

Run the original issue #69 test:

```bash

pytest tests/unit/test_output_parser.py::TestOutputParser::test_json_array_fallback -v
```
Expected result after the fix: the test passes normally rather than being
reported as an expected failure, and the parser returns a list containing the
two array entries as FeedbackSection objects.

### Regression suite

Run:
```bash
pytest tests/unit/test_output_parser.py -v
```
Expected result: the output-parser unit tests pass, including the existing
JSON object, code-fence, plaintext, nested JSON, suggestions, and other
regression cases.

### Expected observable behavior

For input equivalent to:
  ["First feedback item", "Second feedback item"]
parse_review_output() should return a list of FeedbackSection objects
whose contents preserve the two feedback items, rather than raising
AttributeError: 'list' object has no attribute 'items'.

## Risks and unknowns

* The exact representation of array entries should follow the existing
FeedbackSection return contract rather than introducing a new return type.
* If array entries contain structured objects instead of strings, the
implementation must avoid assuming every item has string-only behavior.
The focused test will establish the intended behavior for the issue’s
reproduced string-array case.
* The main regression risk is changing existing dictionary JSON parsing while
adding list handling, so the full output-parser test file will be run after
the focused test.

## Quoted reproduction evidence

Reproduced on commit 2f4e82f52efbcfcc57d65b3fa5348672163ca088 with:
  tests/unit/test_output_parser.py::TestOutputParser::test_json_array_fallback

The reproduced failure was:
  AttributeError: 'list' object has no attribute 'items'

The failure path reached rag/generator/output_parser.py, where the parsed
top-level JSON array was passed to _parse_json_output() and the function
attempted to call .items() on it.

## Deviations

No deviations. The implementation followed the plan described in this file: the output
parser now handles top-level JSON arrays while preserving the existing
dictionary parsing behavior, and the existing JSON-array test was updated
to verify the resulting FeedbackSection objects. The focused test, full
parser test suite, lint, and typecheck all passed.
