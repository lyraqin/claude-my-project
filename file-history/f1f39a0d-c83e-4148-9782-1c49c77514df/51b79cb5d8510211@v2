---
name: proofread
description: Run structured proofreading protocol on academic documents and generate quality reports without modifying source files.
argument-hint: "[filename | all]"
allowed-tools: ["Read", "Grep", "Glob", "Write", "Task"]
---

# Proofreading Controller
This skill orchestrates structured proofreading for academic documents.

Supported formats:
- .docx
- .tex
- .qmd
- .md


## File Selection
   - If `$ARGUMENTS` is a filename → review only that file.
   - If `$ARGUMENTS` is "all" → review all files in `papers/`.

## Workflow

For each selected file:

1. Read the file.
2. Invoke the `proofreader` agent.
3. Collect structured findings.
4. Save report to `quality_reports/`.

## Output Rules

- NEVER modify source files.
- One report per file.
- File name format:
  `quality_reports/<FILENAME>_report.md`
- For `.qmd` files:
  `quality_reports/<FILENAME>_qmd_report.md`



**IMPORTANT: Do NOT edit any source files.**
   Only produce the report. Fixes are applied separately after user review.


## Final Summary to User

After processing:

- Total issues per file
- Breakdown by category
- Count of High severity issues
- Highlight critical recurring problems
