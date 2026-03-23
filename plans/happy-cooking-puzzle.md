# Context
- Need to summarize four Google Scholar XML exports (MISQ, JMIS, ISR, MS) into a single Markdown report grouped by the agreed taxonomy.
- Source XML files are read-only; derived artifacts must live under `/Users/my/Desktop/RA/Junting/` per governance rules.
- Deduplication using DOI/title and keyword-based classification must be documented thoroughly for reproducibility.

# Files Involved
- Source XMLs (read-only):
  - `/Users/my/Desktop/RA/Junting/scholar-export-2026-03-20 MISQ.xml`
  - `/Users/my/Desktop/RA/Junting/scholar-export-2026-03-20 JMIS.xml`
  - `/Users/my/Desktop/RA/Junting/scholar-export-2026-03-20 ISR.xml`
  - `/Users/my/Desktop/RA/Junting/scholar-export-2026-03-20 MS.xml`
- New assets to create/modify:
  - `/Users/my/Desktop/RA/Junting/scripts/parse_scholar_exports.py` (parsing, normalization, dedup, classification, Markdown generation)
  - `/Users/my/Desktop/RA/Junting/organized-scholar-entries.md` (final grouped summary)
  - `/Users/my/Desktop/RA/Junting/tmp/duplicates_report.csv` (optional log for transparency)

# Constraints
- Do not edit the XML exports.
- Deduplicate entries by DOI (case-insensitive); when DOI is missing, normalize titles (lowercase, trim whitespace/punctuation) to identify duplicates.
- Preserve per-topic counts, note multi-topic overlaps, and flag missing DOI/PDF links in verification block.
- Use defined keyword triggers per topic; unmatched entries go under "Other / Uncategorized." If entry spans multiple topics, include it in each section with an "also listed under" note.
- All outputs (Markdown, script, logs) must remain within `/Users/my/Desktop/RA/Junting/`.

# Proposed Plan
1. Build a Python script at `/Users/my/Desktop/RA/Junting/scripts/parse_scholar_exports.py` that:
   - Reads each input XML as an Excel Spreadsheet 2003 document, maps headers to fields (Title, Authors, Journal, Year, Abstract/Notes, DOI/Open URL, PDF URL, etc.), and counts rows per file.
   - Normalizes content by trimming whitespace, collapsing abstract whitespace, standardizing DOI (include https://doi.org/ prefix when missing), and defining a primary URL (priority: DOI link → PDF URL → open-access URL).
   - Captures metadata (source file, row index) for each row to support the appendix and dedup reporting.
   - Deduplicates entries using a map keyed by DOI when available, else by normalized title, recording which raw entries collapsed for the verification block and optional duplicates log.
   - Applies keyword-trigger classification (case-insensitive over title + abstract) across the five topic buckets and tracks per-topic counts, multi-topic overlaps, and missing URL stats.
   - Selects five representative entries for the spot-check table (ensure they cover different topics) and records the keywords that triggered their classifications.
   - Writes `organized-scholar-entries.md` with:
     - Metadata header: date, per-file raw counts, total raw vs unique entries, dedup strategy, keyword rules, per-topic tallies, multi-topic count, missing DOI/PDF count.
     - Verification block summarizing counts and includes spot-check table (Title, source file/row, topic, triggering keywords).
     - Sections per topic (Website Experience & Design; AI / Automation-Driven Systems; Consumer / Trust Signals; Visual / Multimedia Interactions; Other / Uncategorized) with a short description and keyword list, followed by bullet entries formatted as: `- Title (primary link) — Authors. Journal (Year). DOI/PDF/Open link.` Extended info (notes/abstract, PDF) goes on the following indented lines. Multi-topic entries get `(also listed under: ...)` annotations.
     - Appendix listing canonical entries (one per unique record) with source file and row reference for traceability.
     - Verification block at top (raw counts, dedup summary, missing links, spot-check table).
   - Optionally saves duplicates log at `/Users/my/Desktop/RA/Junting/tmp/duplicates_report.csv` showing which rows were collapsed and why.
2. Run the script to produce `organized-scholar-entries.md`, ensuring Markdown conforms to the taxonomy and includes verification data.
3. Double-check that raw row counts match XML tables (e.g., script prints totals), unique counts reflect deduplication, per-topic tallies align with classification results, and the appendix references the original file/row for each entry.

# Classification Keywords (per instructions)
- Website Experience & Design → website, webpage, ux, "user experience", navigation, interface, layout, mobile, responsive, homepage, design
- AI / Automation-Driven Systems → ai, "machine learning", algorithm, automation, recommender, personalization, bot, "automated", nlp, "deep learning"
- Consumer / Trust Signals → trust, privacy, disclosure, reputation, review, rating, credibility, signal, "trustworthy", "information disclosure"
- Visual / Multimedia Interactions → image, video, visual, multimedia, ar, vr, augmented, 3d, infographic, visualisation, visualization
- Other / Uncategorized → entries matching none of the above
Matching is case-insensitive and performed on both Title and Abstract/Notes.

# Verification Plan
- Log raw row counts per XML export immediately after parsing to ensure all rows are read.
- Compare total raw rows vs deduplicated unique entries; include both numbers in the metadata header and verification block.
- Track counts per topic and number of entries assigned to multiple topics; include in verification block with multi-topic count.
- Record how many entries lack DOI and/or PDF links and mention in verification block (flag for missing links).
- Generate spot-check table (five varied entries) showing source file/row and the keywords that triggered each topic assignment.
- Ensure appendix lists each canonical entry along with its source file/row reference for traceability.

# Notes
- This task introduces a new automation script and derived Markdown summary; keep plan-first principles by saving documentation and verification outputs (e.g., duplicates log) under the RA/Junting directory structure.
- After implementing and verifying counts, return here and exit plan mode with a summary.