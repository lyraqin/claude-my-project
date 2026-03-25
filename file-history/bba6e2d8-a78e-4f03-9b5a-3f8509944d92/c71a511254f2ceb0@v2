Context:
- The repository contains an academic workflow template where `CLAUDE.md` currently stores placeholders rather than the concrete guidance future instances need.
- `README.md`, `.claude/rules/`, and templates already document the multi-agent, plan-first workflow, the 3-pass XeLaTeX+Quarto build pipeline, the quality gate expectations, and where to place outputs versus sources.
- We need a new CLAUDE.md that summarizes the real commands, architecture, and governance so that future future CLAUDE.md consumers can get up to speed without replacing placeholders.

Approach:
1. Review the README and existing governance files to capture the canonical build/deploy commands, the directory roles (papers vs output vs scripts vs templates), and the quality/plan workflow (plan-first rules, session logs, orchestrator).
2. Rewrite `CLAUDE.md` to include those commands under a "Commands" section (LaTeX compilation steps, Quarto deploy script, quality score script, single-test command), a "Project Architecture" section that explains the Beamer slides + Quarto reveal, the `.claude` governance/config directories, `scripts/`, and the guided location for outputs (`quality_reports/`, `output/`, `docs/`), and a "Workflow Governance" section that references the key rules agents must read (plan-first, orchestrator, session logging, templates for specs/plans/quality reports).
3. Link to `README.md` and the guide/QA locations for more detail so a future agent knows where to dig deeper.
4. Keep placeholder-specific sections minimal (ex: no mention of `[YOUR PROJECT NAME]`), focusing on actual workflow commands and references.

Files to modify:
- CLAUDE.md (replace placeholder content with the concrete guidance described above)

Verification:
- Re-read new CLAUDE.md to confirm it lists the required commands, explains the directory structure (Slides/Quarto/scripts/.claude/quality_reports), and cites the governance documents and quality rules.
- Ensure the file references README + guide as sources of further detail without re-hashing everything.
