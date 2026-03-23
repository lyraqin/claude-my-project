# Plan: Analyze Writing Logic of "2024 - Municipal finance shapes urban climate action and justice.pdf"

Date: 2026-03-10
Author: glm-5 (Claude Code)

## Context
The user wants a detailed analysis of the writing logic for "2024 - Municipal finance shapes urban climate action and justice.pdf" at the paragraph and sentence level. This is a research task to understand how the paper is structured, identify logical patterns, and assess the flow of arguments.

## Outputs
- `quality_reports/municipal_finance_analysis_2026-03-10.md` — Human-readable report
- `quality_reports/municipal_finance_analysis_data_2026-03-10.json` — Structured JSON with paragraph/sentence-level metadata
- `quality_reports/municipal_finance_analysis_table_2026-03-10.csv` — Flat table for spreadsheet viewing

## Approach

### Phase 1: Text Extraction
Use Python to extract text from the PDF:
- Try `pdfplumber` first for layout-aware extraction (preserves paragraphs and tables)
- Fallback to `pypdf` if needed
- If the PDF is scanned (images), use `pdf2image` + `pytesseract` (OCR)
- User has approved installing poppler if needed for higher-fidelity extraction

### Phase 2: Text Segmentation
- Segment into paragraphs using heuristics (empty lines, line breaks)
- Segment into sentences using spaCy or NLTK sentence tokenizer
- Detect the paper's language (likely English) to use appropriate tokenizer

### Phase 3: Logic Analysis (Per Paragraph/Sentence)
Apply structured tags:
- **Paragraph-level:** topic_sentence, background, motivation, method, results, argument, conclusion, transition
- **Sentence-level:** claim, evidence, method_description, result_description, assumption, weak_inference, transition

Generate for each unit:
- Main idea summary
- Logical role
- Whether it supports previous conclusions
- Any logical gaps or unsupported assumptions
- Suggestions for clarification or improvement

### Phase 4: Aggregation & Reporting
- Count issue types (High/Medium/Low severity)
- Generate "Items needing attention" list (by severity)
- Create a one-page executive summary with key findings and recommendations

### Phase 5: Save Outputs
All analysis files go to `quality_reports/` following constitutional governance rules.

## Critical Files
- Source PDF: `/Users/my/Desktop/RA/LeiLei/2024 - Municipal finance shapes urban climate action and justice.pdf`
- Output directory (read-only for analysis): `quality_reports/`

## Dependencies
- Python: `pdfplumber` or `pypdf`, `spaCy` (or `nltk`), `langdetect`
- Optional for OCR: `pdf2image`, `pytesseract`
- System: User approved `brew install poppler` if needed

## Verification Steps
1. Verify extracted page count matches actual PDF page count
2. Verify paragraph count is reasonably accurate (spot-check manually)
3. User samples 2-3 paragraphs to confirm analysis vs. original text

## Non-Negotiable Rules
- Follow `/Users/my/.claude/rules/constitutional-governance.md` — do not modify source files in `papers/`
- All derived work must go to `quality_reports/`
- No hallucinated citations or invented data
