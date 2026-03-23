# Constitutional Governance Template

This document defines **non-negotiable principles** governing how Claude interacts with this research repository.

These rules ensure **research reproducibility, file structure consistency, and academic quality**.


---

# Article I: Source of Truth Principle

**Primary artifacts must always be respected.**

Repository hierarchy:

| Artifact | Role |
|--------|------|
| `papers/` | Authoritative research sources (PDF, LaTeX, notes, word) |
| `output/` | Generated artifacts (slides, drafts, figures) |
| `quality_reports/` | Review outputs, proofreading logs, analysis reports |
| `templates/` | Reusable templates and notation registries |
| `scripts/` | Replication and analysis code |

**Rule:**

Claude must **never overwrite source material in `papers/`**.

Derived work must always go to: `output/quality_reports/`

**Why this matters**

Prevents corruption of source documents and preserves research provenance.

---

# Article II: Plan-First Threshold

Tasks involving:

- more than **3 files**
- more than **30 minutes of work**
- multi-step academic workflows

must **enter plan mode before execution.**

Examples:

- literature review
- slide creation
- replication workflow
- empirical model review

Claude should first propose:
- Task breakdown
- Files involved
- Output locations

**Exceptions**

Quick fixes:

- typo corrections
- small code edits
- formatting changes


---

# Article III: Reproducibility Standard

All empirical claims must be **replicable**.

If econometric models are discussed, Claude must verify:

- model specification
- standard errors
- fixed effects
- identification strategy
- replication commands

Supported languages: `R`, `Python`, `MATLAB`, `Stata (.do)`

Replication scripts should be stored in:`scripts/`
Derived figures should be stored in: `output/figures/`

**Why this matters**

Academic credibility depends on replicable results.

---

# Article IV: Quality Gate

Generated outputs must pass quality review before being considered complete.

Quality checks include:

- grammar and proofreading (`proofreader`)
- econometric specification review
- citation validation (`validate-citations`)
- slide readability checks

Reports must be saved to: `quality_reports/`


Claude should recommend running quality agents when appropriate.

---

# Article V: Directory Discipline

Claude must respect repository structure.

| Folder | Purpose |
|------|--------|
| `papers/` | Input materials |
| `output/` | Generated content |
| `quality_reports/` | Reviews and validation reports |
| `templates/` | reusable templates |
| `scripts/` | code and replication |

Rules:

- Never mix generated output into `papers/`
- Never store temporary analysis in root directory
- Always log review outputs in `quality_reports/`

---

# User Preferences (Flexible)

The following can change per project:

- citation style (APA / Chicago / journal-specific)
- plotting style and color palettes
- slide formatting choices
- notation preferences
- figure generation language (R / Python)

Claude should ask the user when uncertain.

---

# Amendment Process

When deviating from a rule, ask:

> "Is this a **permanent amendment** to Article X or a **one-time exception**?"

Permanent amendments must update this document.

Session logs should record: `[CONSTITUTIONAL AMENDMENT]`

---

# Review Cadence

Review these rules:

- every **10 research sessions**
- or when repository structure changes

Questions:

- Are rules still helping workflow?
- Are they violated frequently?
- Should new patterns become constitutional rules?

