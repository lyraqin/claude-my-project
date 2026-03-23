---
name: lit-review
description: Structured literature search, synthesis, citation extraction, and gap identification for academic projects
disable-model-invocation: true
argument-hint: "[topic, paper title, or research question]"
allowed-tools: ["Read", "Grep", "Glob", "Write", "WebSearch", "WebFetch"]
---

# Literature Review Skill

Conduct a structured literature review for the given topic or research question.

**Input:** `$ARGUMENTS` — topic, paper title, research question, or phenomenon to investigate.

---

## Steps

1. **Parse the query** from `$ARGUMENTS`.
   - If a specific paper is named, use it as an anchor.
   - If a general topic, treat it as a research area.

2. **Search for relevant literature** using available resources:
   - Local project papers: `papers/`
   - Read any existing .bib file for papers already in the project (if available)
   - External search: `WebSearch` for recent publications (if available)
   - Repository access: `WebFetch` to working papers or preprints (if available)
   - When searching the web: Use the web search tool. Return results as citations.


3. **Organize findings** into categories:
   - **Theoretical contributions:** models, frameworks, mechanisms
   - **Empirical findings:** key results, effect sizes, data sources
   - **Methodological innovations:** estimators, identification strategies, inference methods
   - **Open debates:** unresolved disagreements in the literature

4. **Identify gaps and opportunities**:
   - Unanswered research questions
   - Data or methods that could address gaps
   - Conflicting findings in the literature

5. **Extract citations** in BibTeX format for all discussed papers.

6. **Save the report** to: quality_reports/lit_review_[sanitized_topic].md


- Example: `topic = "climate risk"` → `quality_reports/lit_review_climate_risk.md`

---

## Output Format

```markdown
# Literature Review: [Topic / Query]

**Date:** [YYYY-MM-DD]
**Query:** [Original query from user]

## Summary

[2-3 paragraph overview of the literature, key trends, and major debates]

## Key Papers

### [Author (Year)] — [Short Title]
- **Main contribution:** [1-2 sentences]
- **Method:** [Identification strategy / data]
- **Key finding:** [Result, effect size if available]
- **Relevance:** [Importance for project]

[Repeat for 5-15 papers, ordered by relevance]

## Thematic Organization

### Theoretical Contributions
[Discussion grouped by themes or frameworks]

### Empirical Findings
[Compare results, highlight consensus/disagreements]

### Methodological Innovations
[Notable techniques, estimators, approaches]

## Gaps and Opportunities

1. [Gap 1 — what's missing and why it matters]
2. [Gap 2]
3. [Gap 3]

## Suggested Next Steps

- [Concrete actions: read more papers, gather data, try methods]

## BibTeX Entries

```bibtex
@article{...}


---

## Important

- Be honest about uncertainty; flag unverifiable citations
- Prioritize recent work (last 5–10 years) unless seminal papers are critical
- Distinguish working papers vs published papers
- Do NOT fabricate citations; leave notes for user verification
- Use **papers/** as authoritative local source
- Save outputs only to **quality_reports/** for traceability
- Maintain structured, actionable synthesis to support research planning

---

## Integration Notes

- Compatible with `review-paper` skill for deeper manuscript assessment
- Supports batch or single-topic reviews
- Sanitized filenames prevent overwriting
- Structured output facilitates later multi-agent workflows or report aggregation
