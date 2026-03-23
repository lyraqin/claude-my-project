---
name: create-slides
description: Guided slide creation workflow from papers and materials. Ensures notation consistency, pedagogical quality, and structured output.
disable-model-invocation: true
argument-hint: "[Topic name or paper filename in papers/]"
allowed-tools: ["Read", "Grep", "Glob", "Write", "Edit", "Bash", "Task"]
context: fork
---

# Slide Creation Skill

Create high-quality academic slides from source papers, notes, or other materials.

**Workflow is collaborative and iterative:** user drives content selection and pedagogical goals; Claude acts as a thinking partner and quality controller.

---

## CONSTRAINTS (Non-Negotiable)

1. **Read the knowledge base first** (`templates/notation_registry.md`, previous session logs)

2. All new symbols must be checked against the notation registry
3. Motivation before formal definitions — never omit motivation
4. Every definition/example should appear within 1–2 slides
5. Maximum 2 colored boxes per slide
6. Avoid `\pause` or overlay commands unless project rules allow
7. Insert transition slides at major conceptual pivots
8. Thread at least 1 running empirical example through the lecture
9. Verify all citations against `papers/` and project bibliography
10. Work in batches of 5–10 slides — share iteratively, avoid bulk-dumping

---

## WORKFLOW

### Phase 0: Intake & Context
- Read `papers/` and knowledge base (`templates/notation_registry.md`)
- Inventory provided materials: `.docx`, `.tex`, `.qmd`, `.md`, R scripts, figures
- State pedagogical goal, get user confirmation before drafting

### Phase 1: Paper / Material Analysis
- Split papers or notes into digestible chunks
- Map paper notation → course/project notation
- Identify slide-worthy content
- Present content summary for user approval

### Phase 2: Structure Proposal
- Propose outline (e.g., 3-Part, 5-Act, or custom template)
- List required TikZ diagrams or R figures
- List new notation to introduce
- **Gate:** proceed only after user approves

### Phase 3: Draft Slides (Iterative)
- Draft slides in batches of 5–10
- Apply notation and formatting conventions
- Perform quality checks on each batch:
  - Correct notation usage
  - Motivation + worked examples
  - Slide length and readability

### Phase 4: Figures & Code
- R scripts follow project conventions (`scripts/`)
- TikZ diagrams stored in `output/figures/` or embedded in Beamer `.tex`
- Save intermediate objects (RDS, CSV) for later integration into Quarto

### Phase 5: Polish & Compile
- Full 3-pass compilation if using LaTeX / Beamer
- Run Devil's Advocate review (challenge assumptions, notation, flow)
- Optionally run domain-specific review (`proofread` / `review-paper`)
- Update notation registry (`templates/notation_registry.md`) and session logs (`quality_reports/`)

---

## Output Locations

| Type | Location |
|------|---------|
| Draft slides | `output/[Topic]/*.tex` or `output/[Topic]/*.qmd` |
| Figures | `output/figures/` |
| Session log | `quality_reports/session_[Topic].md` |
| Notation updates | `templates/notation_registry.md` |
| Quality reports | `quality_reports/` |

---


## Post-Creation Checklist

```
[ ] Lecture compiles without errors
[ ] No overfull hbox > 10pt
[ ] All citations resolve
[ ] Every definition has motivation + worked example
[ ] Max 2 colored boxes per slide
[ ] 2-3 Socratic questions embedded
[ ] Transition slides between sections
[ ] At least 1 running application threaded throughout
[ ] New notation added to knowledge base
[ ] Session log updated
[ ] Devil's Advocate run
```


---

## Integration Notes

- Compatible with `/proofread` and `/review-paper` skills for quality control
- Drafts saved incrementally in `output/` to allow batch review
- Structured workflow supports multi-agent pipelines and iterative pedagogical design
- Keeps **papers/** as authoritative source and **quality_reports/** as traceable outputs
