---
name: review-paper
description: Comprehensive academic manuscript review covering argument structure, identification, econometric specification, citation completeness, writing quality, and potential referee objections
disable-model-invocation: true
argument-hint: "[paper filename in papers/ or path to .docx/.tex/.pdf/.qmd]"
allowed-tools: ["Read", "Grep", "Glob", "Write", "Task"]
---

# Manuscript Review Skill

Produce a thorough, constructive review of an academic manuscript — the type of report a top-journal referee would provide.

**Input:** `$ARGUMENTS` — path to a manuscript in `papers/` (or absolute path). Supports `.docx`, `.tex`, `.pdf`, or `.qmd`.

---

## Steps

1. **Locate the manuscript**
   - Direct path from `$ARGUMENTS`
   - Fallback: glob match within `papers/`
   - Raise error if not found

2. **Read the manuscript end-to-end**
   - For `.pdf`, process in 5-page chunks
   - For `.docx` / `.tex` / `.qmd`, read full text

3. **Evaluate across six dimensions**:
   1. Argument Structure
   2. Identification / Causal Claims
   3. Econometric / Statistical Specification
   4. Literature Positioning & Citations
   5. Writing Quality
   6. Presentation & Figures

4. **Generate 3–5 referee objections**
   - Focus on top-journal concerns
   - Highlight fatal or high-impact issues

5. **Produce structured review report**

6. **Save report to**: `quality_reports/paper_review_[sanitized_name].md`


---

## Review Dimensions

### 1. Argument Structure
- Research question clearly stated?
- Introduction motivates question effectively?
- Logical flow: question → method → results → conclusion?
- Conclusions supported by evidence?
- Limitations acknowledged?

### 2. Identification / Causal Claims
- Credibility of causal claim?
- Key identifying assumptions explicitly stated?
- Threats: omitted variables, reverse causality, measurement error?
- Robustness checks adequate?
- Estimator appropriate for research design?

### 3. Econometric / Statistical Specification
- Correct standard errors (clustered, robust, bootstrap)?
- Functional form appropriate?
- Sample selection issues?
- Multiple testing concerns?
- Point estimates economically meaningful?

### 4. Literature Positioning & Citations
- Key papers cited?
- Prior work characterized accurately?
- Contribution differentiated from existing work?
- Missing citations that a referee might flag?

### 5. Writing Quality
- Clarity, concision, and academic tone
- Consistent notation
- Abstract summarizes main contributions
- Tables and figures are self-contained

### 6. Presentation & Figures
- Tables and figures well-designed
- Notation consistent
- Typos, grammar, formatting checked
- Manuscript length appropriate for contribution

---

## Output Format

```markdown
# Manuscript Review: [Paper Title]

**Date:** [YYYY-MM-DD]
**Reviewer:** review-paper skill
**File:** [path to manuscript]

## Summary Assessment

**Overall recommendation:** [Strong Accept / Accept / Revise & Resubmit / Reject]

[2-3 paragraph summary: contribution, strengths, key concerns]

## Strengths

1. [Strength 1]
2. [Strength 2]
3. [Strength 3]

## Major Concerns

### MC1: [Title]
- **Dimension:** [Argument / Identification / Econometrics / Literature / Writing / Presentation]
- **Issue:** [Specific description]
- **Suggestion:** [How to address it]
- **Location:** [Section/page/table]

[Repeat for each major concern]

## Minor Concerns

### mc1: [Title]
- **Issue:** [Description]
- **Suggestion:** [Fix]

[Repeat]

## Referee Objections

### RO1: [Question]
**Why it matters:** [Why this could be fatal]
**How to address it:** [Suggested response or additional analysis]

[Repeat for 3-5 objections]

## Specific Comments

[Line-by-line or section-by-section, if needed]

## Summary Ratings

| Dimension | Rating (1-5) |
|-----------|-------------|
| Argument Structure | [N] |
| Identification | [N] |
| Econometrics | [N] |
| Literature | [N] |
| Writing | [N] |
| Presentation | [N] |
| **Overall** | **[N]** |


## Principles

- **Be constructive.** Every criticism should come with a suggestion.
- **Be specific.** Reference exact sections, equations, tables.
- **Think like a referee at a top-5 journal.** What would make them reject?
- **Distinguish fatal flaws from minor issues.** Not everything is equally important.
- **Acknowledge what's done well.** Good research deserves recognition.
- **Do NOT fabricate details.** If you can't read a section clearly, say so.
