---
name: paper-digest
description: Generate a structured research digest from academic papers. Use when user asks to "summarize a paper", "digest a paper", "extract key contributions", or when preparing literature reviews, replication, or slides from papers in papers/. Supports .pdf, .docx, .tex, .qmd, and .md papers.
argument-hint: "[paper filename in papers/]"
allowed-tools: ["Read", "Grep", "Glob", "Write", "Edit", "Bash"]
disable-model-invocation: true
---

# Paper Digest Skill

Create a **structured research digest** from an academic paper.

The digest extracts the **core theoretical contribution, empirical strategy, and main results** in a standardized format to support:

- literature reviews
- econometric evaluation
- slide preparation
- replication planning

All digests are saved to:

```
quality_reports/paper_digest_[papername].md
```

Source papers in `papers/` are **read-only** and must not be modified.

---

# Supported Input Types

The skill can process:

| File Type | Typical Use |
|-----------|-------------|
| `.pdf` | journal articles, working papers |
| `.docx` | drafts or working manuscripts |
| `.tex` | LaTeX source |
| `.qmd` / `.md` | Quarto or markdown papers |

---

# Workflow

## Step 1 — Locate Paper

Search for the paper inside:

```
papers/
```

Use `Glob` to find matching filenames.

Example:

```
papers/fed_facial_cues.pdf
```

If multiple matches exist, ask the user to confirm the target file.

---

## Step 2 — Safe Reading Strategy

For **large PDFs**:

1. Inspect file size and page count
2. Read sections progressively rather than loading the entire file
3. Focus first on:
   - Abstract
   - Introduction
   - Model / Theory
   - Data
   - Empirical Results
   - Conclusion

Appendix and references should only be processed if needed.

---

## Step 3 — Extract Core Components

Extract the following key elements.

### Paper Metadata

- Title
- Authors
- Year
- Journal / Working Paper
- Research field (e.g., asset pricing, corporate finance)

### Research Question

What is the main question the paper answers?

Describe in **1-2 sentences**.

### Main Contribution

Identify the **core novelty**.

Examples:

- new theoretical mechanism
- new dataset
- new empirical identification
- new econometric method

### Theoretical Framework (if applicable)

Summarize:

- model structure
- key assumptions
- equilibrium intuition
- comparative statics

If the paper has no theory, write:

```
No formal theoretical model.
```

### Data

Describe:

- dataset source
- sample period
- sample size
- key variables

Example:

```
U.S. firm-level panel data from 1995-2022.
```

### Empirical Strategy

Explain the identification approach.

Examples:

- difference-in-differences
- instrumental variables
- regression discontinuity
- event study
- panel fixed effects

Include regression form if present.

Example:

```
Y_it = beta*X_it + gamma*Z_it + alpha_i + tau_t + epsilon_it
```

### Main Results

Summarize:

- key findings
- direction of effects
- approximate magnitude (if available)

Example:

```
A one-standard-deviation increase in climate risk disclosure reduces cost of capital by ~2%.
```

### Robustness Checks

List important robustness tests.

Examples:

- alternative clustering
- placebo tests
- subsample analysis
- alternative variable definitions

### Limitations

Identify potential weaknesses:

- external validity
- measurement issues
- identification assumptions
- limited data coverage

### Relation to Literature

Explain how the paper relates to:

- major existing literature
- competing theories
- related empirical findings

---

## Step 4 — Research Relevance

Explain why the paper matters for the **current project**.

Example:

```
Relevant for research on climate risk and asset pricing because it provides a firm-level disclosure measure that can proxy for climate mitigation efforts.
```

---

## Step 5 — Save Digest

Save the final structured digest to:

```
quality_reports/paper_digest_[papername].md
```

Example:

```
quality_reports/paper_digest_fed_facial_cues.md
```

---

# Output Format

```markdown
# Paper Digest

**Paper:** [Title]
**Authors:** [Authors]
**Year:** [Year]
**Source File:** papers/[filename]

---

# Research Question

[1-2 sentence description]

---

# Main Contribution

[Explain novelty]

---

# Theoretical Framework

[Model intuition if present]

---

# Data

Dataset description.

---

# Empirical Strategy

Identification method and regression specification.

---

# Main Results

Key empirical findings.

---

# Robustness Checks

List robustness exercises.

---

# Limitations

Potential weaknesses or open questions.

---

# Relation to Literature

How the paper fits within the literature.

---

# Relevance to Current Project

Why this paper matters for the research workflow.
```

---

# Examples

## Example 1 - Literature Review Preparation

**User says:**

```
digest the paper papers/climate_risk_disclosure.pdf
```

**Actions**

1. Read the paper safely
2. Extract contributions and empirical strategy
3. Save digest

**Result**

```
quality_reports/paper_digest_climate_risk_disclosure.md
```

---

## Example 2 - Slide Preparation

**User says**

```
prepare slides for papers/fed_facial_cues.pdf
```

Claude should first:

```
run paper-digest
```

Then `create-slides` can use the structured digest.

---

# Troubleshooting

### Error: File not found

**Cause**

Paper not located in `papers/`.

**Solution**

Confirm filename or place the file inside `papers/`.

---

### Error: PDF too large

**Cause**

Large PDFs exceed processing limits.

**Solution**

Read sections incrementally or split into smaller page ranges.

---

### Error: Missing empirical specification

**Cause**

Paper may be theoretical.

**Solution**

Document theoretical model instead.

---

# Integration Notes

This skill is the **first step** in the academic workflow pipeline:

```
paper-digest -> lit-review -> econometric-review -> create-slides
```

Benefits:

- PDFs are converted to structured knowledge once
- Downstream skills can reuse the digest without re-reading the PDF
- Maintains consistency across literature reviews, replication, and teaching materials
