# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## Project Overview

**Academic workflow system** for manuscript preparation, proofreading, and research support. Focus areas: sustainable finance, digital finance, corporate finance, and asset pricing.

---

## Architecture

```
~/.claude/
├── agents/      # Domain-specific executors (proofreader.md)
├── skills/      # Workflow controllers (proofread, review-paper, lit-review, create-slides, etc.)
└── rules/       # Governance (constitutional-governance.md, plan-first-workflow.md)

papers/          # Source manuscripts — IMMUTABLE, never overwrite directly
output/          # Generated drafts (LaTeX, slides)
quality_reports/ # Proofread reports, review logs, plans, session logs
templates/       # Report templates (quality-report.md, skill-template.md)
```

**Critical constraint:** `papers/` is the single source of truth. Claude must NEVER directly overwrite files inside `papers/`.

---

## Available Skills

| Skill | Purpose | Output Location |
|-------|---------|-----------------|
| `/proofread [file\|all]` | Structured grammar, typo, consistency scan | `quality_reports/<filename>_report.md` |
| `/review-paper [file]` | Referee-style manuscript review (6 dimensions) | `quality_reports/paper_review_<name>.md` |
| `/lit-review [topic]` | Literature synthesis, gap identification, BibTeX extraction | `quality_reports/lit_review_<topic>.md` |
| `/create-slides [topic]` | Generate Beamer/Quarto slides from manuscript | `output/[Topic]/*.tex` or `output/[Topic]/*.qmd` |
| `/research-ideation [topic]` | Generate research questions, hypotheses, empirical strategies | `quality_reports/research_ideation_<topic>.md` |
| `/validate-citations [file]` | Cross-reference citations against bibliography | `quality_reports/citation_validation_<name>.md` |
| `/econometric-spec-review [file]` | Review regression specs (R, Python, Stata, MATLAB) | `quality_reports/econ_spec_<name>.md` |

---

## Workflow Principles

1. **Plan first** — Enter plan mode for non-trivial tasks (>3 files, >30 min); save plans to `quality_reports/plans/`
2. **Verify after** — Compile/render and confirm output at end of every task
3. **Quality gates** — Nothing ships below 85/100 (submission-ready threshold)
4. **Learn tags** — When corrected, append `[LEARN:category] wrong → right` to MEMORY.md
5. **Context survival** — Save session logs before auto-compression; resume by reading latest plan + git log

---

## Quality Standards

| Severity | Definition |
|----------|------------|
| **High** | Changes meaning, grammatical incorrectness, incorrect citation, logical inconsistency |
| **Medium** | Clarity issue, style weakness, inconsistent terminology |
| **Low** | Minor polish, readability improvement |

---

## Report Requirements

All reports must include:
- File name and total issue count
- Severity breakdown (High/Medium/Low)
- Structured table of findings with locations
- Specific suggested fixes (no vague comments)
- No paragraph rewrites unless explicitly requested

---

## Agents

| Agent | Purpose | Trigger |
|-------|---------|---------|
| `proofreader` | Grammar, typos, overflow, consistency scan | Invoked by `/proofread` skill |

---

## Non-Negotiables

- No hallucinated citations
- No invented data
- No vague academic clichés
- No unstructured output
- No silent file edits in `papers/`

Claude operates as **academic collaborator**, not casual assistant.
