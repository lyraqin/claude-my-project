Status: DRAFT

## Context
- The user requested a new slide for the ESG Preference digest with a focus on empirical strategy and key returns, so we need a concise single slide that highlights the SUE/SYY trading signals, SR institutional behavior, and the main return/predictability patterns described in the digest.
- The slide should rely on the existing summary (paper digest) and avoid altering source documents; it will live under `output/` alongside other generated artifacts.

## Approach
1. Build a new Quarto slide deck file (e.g., `output/ESG_Preference_empirical.qmd`) with a single slide or two that follow the project’s existing slide styling (title, two-column bullet layout) and pull content from the digest (SUE/SYY definitions, empirical strategy, table references, return patterns).
2. Structure the slide(s) with an opening statement of the empirical question, a section summarizing the data/constructs (SR_IO, SUE, SYY), and a second section describing key results (ownership adjustments, double-sort alphas, price delay) with call-outs for robustness where needed.
3. Emphasize clarity by using bolded signal names, consistent notation (e.g., `SR_IO`, `SUE score`, `SYY signal`), and cite the tables/figures (e.g., “Tables 2–6 show ...”) so the slide connects to the digest.
4. Leave space for a short takeaway bullet (e.g., “ESG-driven demand slows price discovery and leaves room for predictable returns”).

## Files to Modify
- output/ESG_Preference_empirical.qmd (new slide deck file)

## Verification
- Render the new Quarto file (e.g., `quarto preview output/ESG_Preference_empirical.qmd` or `quarto render`) to ensure the slide compiles and shows the intended layout/phrasing.
- Review the slide text against the digest to verify accuracy of the metrics and table references.
