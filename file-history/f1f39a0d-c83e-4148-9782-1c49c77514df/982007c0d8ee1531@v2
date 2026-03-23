---
name: validate-citations
description: Cross-references in-text citations against bibliography entries. Use when user asks to "check citations", "validate references", or "ensure bibliography consistency" in .tex, .qmd, .md, or .docx manuscripts. Identifies missing entries, unused references, and formatting inconsistencies.
argument-hint: "[file path in papers/ or filename]"
allowed-tools: ["Read", "Grep", "Glob", "Write", "Task"]
disable-model-invocation: true
---

# Validate Citations

Ensures all in-text citations have corresponding entries in the bibliography and identifies unused references. Supports LaTeX, Quarto, Markdown, and Word documents.

## Instructions

Step 1: **Locate manuscript**
- Accept `.tex`, `.qmd`, `.md`, `.docx` files in `papers/`
- Example: `papers/firm_innovation.tex`

Step 2: **Extract in-text citations**
- LaTeX: commands like `\cite{}`, `\citet{}`, `\citep{}`
- Quarto / Markdown: `[@key]`
- Word (.docx): parse text for citation keys (e.g., `[Author,Year]`, `(Author, Year)`,`Author(Year)`)
- Build a list of all cited keys

Step 3: **Parse bibliography**
- Default: `Bibliography_base.bib` in project root
- Extract all BibTeX entries (`@article{key,`, `@book{key,`, etc.)
- Build list of all available keys

Step 4: **Cross-reference**
- **Missing in bib:** citations present in text but absent in bibliography (CRITICAL)
- **Unused in bib:** entries in bibliography never cited
- Check for DOI format correctness if present
- Highlight duplicates or inconsistent capitalization in keys

Step 5: **Generate report**
- Save to `quality_reports/citation_validation_[sanitized_name].md`
- Include:
  - File name
  - Missing citations
  - Unused references
  - Formatting issues
  - Suggested corrections

## Examples

### Example 1: LaTeX manuscript
**Context:** User wants to verify citations in manuscript.tex
**User says:** "Check citations in manuscript.tex"
**Actions:**
1. Read `papers/manuscript.tex`
2. Extract all `\cite{}` and `\citep{}` keys
3. Parse `Bibliography_base.bib`
4. Compare and identify missing / unused entries
5. Save report `quality_reports/citation_validation_manuscript.md`
**Result:** List of missing citations, unused references, and formatting issues

### Example 2: Quarto / Markdown
**Context:** User asks for citation check in Quarto slides
**User says:** "Validate citations in Lecture1.qmd"
**Actions:**
1. Read `papers/Lecture1.qmd`
2. Extract `[@key]` citations
3. Parse bibliography
4. Report missing/unused citations
**Result:** Clean, structured report in `quality_reports/`

### Example 3: Word Document
**Context:** User provides Word manuscript
**User says:** "Check citations in my paper.docx"
**Actions:**
1. Read text from `papers/paper.docx`
2. Extract bracketed citation keys `(Author, Year)`
3. Parse BibTeX file for corresponding keys
4. Report missing or unused citations
**Result:** Report saved in `quality_reports/citation_validation_paper.md`

## Troubleshooting

**Error:** Citation pattern not found
**Cause:** Non-standard or non-bracketed citation style
**Solution:** Add pattern to Step 2 extraction (e.g., `\citeauthor{}` or `(Author)`)

**Error:** Bibliography missing entries
**Cause:** Key absent in `Bibliography_base.bib`
**Solution:** Add missing entry manually, re-run skill

**Error:** Duplicate keys or inconsistent capitalization
**Cause:** Same citation used with different letter cases or duplicates
**Solution:** Normalize keys in BibTeX, ensure uniqueness
