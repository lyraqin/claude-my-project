---
name: econometric-spec-review
description: Reviews econometric and statistical specifications across multiple platforms (R, Python, MATLAB, Stata, LaTeX, Word, Quarto). Use when user shares regression or analysis code, asks to "check model spec", "review estimation", or "validate regressions". Checks standard errors, clustering, fixed effects, omitted covariates, functional form, and replication commands.
argument-hint: "[file path in papers/ or filename]"
allowed-tools: ["Read", "Grep", "Glob", "Write", "Task"]
disable-model-invocation: true
---

# Econometric Specification Review (Multi-Language)

Perform a structured review of econometric and statistical specifications in academic manuscripts or analysis scripts. Supports Python, R, MATLAB, Stata `.do`, LaTeX, Word `.docx`, and Quarto `.qmd`. Detects common issues in applied economics, finance, and quantitative social sciences research.

## Instructions

Step 1: **Locate the manuscript or script**
- Accept `.R`, `.py`, `.m` (MATLAB), `.do` (Stata), `.tex`, `.docx`, `.qmd` files in `data/`
- Example: `data/firm_innovation.R` or `data/panel_analysis.do`

Step 2: **Extract regression or analysis commands**
- Python: `statsmodels`, `linearmodels`, `sklearn.linear_model`, `ols` or `glm`
- R: `lm`, `glm`, `felm`, `plm`
- MATLAB: `regress`, custom model functions
- Stata: `regress`, `xtreg`, `areg`, `mixed`, `reghdfe`
- LaTeX / Word / Quarto: identify displayed equations and description of models
- Glob for multiple occurrences, read in order

Step 3: **Check standard errors**
- Ensure robust, clustered, or bootstrap standard errors are reported
- Flag cases where standard errors may be inconsistent with panel or clustering structure

Step 4: **Check fixed effects / panel structure**
- Verify appropriate inclusion of fixed effects
- Identify potential omitted variables that bias estimates
- Flag multi-level or hierarchical structures not accounted for

Step 5: **Check functional form and covariates**
- Identify missing control variables or transformations
- Flag potential endogeneity or non-linear relationships
- Suggest alternative specifications if needed

Step 6: **Check replication and reproducibility**
- Python/R/MATLAB: verify random seeds, saved models, or output scripts
- Stata: ensure `esttab`, `outreg`, or `.do` reproducibility commands present
- LaTeX / Quarto: ensure model descriptions match code in appendix or scripts

Step 7: **Generate structured report**
- Save to `quality_reports/econ_spec_[sanitized_name].md`
- Include:
  - Regression/analysis checked
  - Issues found
  - Suggested fixes
  - Severity (High / Medium / Low)

## Examples

### Example 1: Python Script Review
**Context:** User wants to verify regression code in Python
**User says:** "Check my Python model specification"
**Actions:**
1. Read `papers/experiment.py`
2. Extract `statsmodels` or `linearmodels` commands
3. Check standard errors, fixed effects, covariates
4. Produce report `quality_reports/econ_spec_experiment.md`
**Result:** List of specification issues with suggested corrections

### Example 2: MATLAB / R Script Review
**Context:** User submits MATLAB or R script
**User says:** "Verify regression specification"
**Actions:**
1. Read `papers/panel_analysis.m` or `papers/panel_analysis.R`
2. Identify all regression or model commands
3. Validate standard errors, fixed effects, and covariate inclusion
4. Save report in `quality_reports/econ_spec_panel_analysis.md`
**Result:** Summary of specification and replication issues

### Example 3: LaTeX / Word / Quarto Manuscript
**Context:** User provides manuscript for econometric check
**User says:** "Check model specs in my paper"
**Actions:**
1. Read `papers/firm_innovation.tex` or `.docx` or `.qmd`
2. Extract regression formulas, equations, or model descriptions
3. Compare described specifications with recommended practice
4. Generate report `quality_reports/econ_spec_firm_innovation.md`
**Result:** Highlighted potential specification and reporting issues

## Troubleshooting

**Error:** Regression command not detected
**Cause:** Non-standard function or commented-out code
**Solution:** Verify code syntax; use conventional commands

**Error:** File not found
**Cause:** Incorrect path or file missing in `data/`
**Solution:** Confirm file exists, path relative to `data/`

**Error:** Standard error type unclear
**Cause:** No robust/clustered option used
**Solution:** Flag in report and suggest proper specification
