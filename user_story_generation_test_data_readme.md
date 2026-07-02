# User Story Generation Test Data

Generated: 2026-07-02 03:55:59Z
Schema version: 1.0

## Purpose
This dataset tests a user-story generation model across three behaviors:

1. **Question generation** before a report is produced.
2. **Report generation** using problem statements and PO answers.
3. **Post-report gap handling/regeneration** where the PO may answer none, a few, or all open questions.

## Files
- `user_story_generation_test_data.xlsx`: human-readable test workbook with scenarios, test cases, expected question slots, report assertions, gap cycles, and scoring rubric.
- `user_story_generation_test_data.jsonl`: machine-readable records, one test case per line.

## How to use
For question-generation tests, feed the model the `problem_statement` and any `conversation_so_far`, then score its next questions against `expected_question_slot_ids` and the Question Slots sheet.

For report-generation tests, feed the problem statement and PO answers, then score the report against the Report Assertions and Rubric sheets.

For regeneration tests, feed the draft report plus `gap_answers`; verify that answered gaps are integrated into relevant sections and unanswered gaps remain open.

## Key regression target
The French complaint scenario includes an intentionally important trap: the initial transcript asks about missing/invalid account numbers, but the PO has not answered yet. A high-quality model should keep that as an Open Item or clearly labeled assumption, not treat it as a confirmed requirement.
