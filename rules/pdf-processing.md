---
paths:
  - "papers/**/*.pdf"
---

# PDF Processing Rule

Large PDFs should be processed safely to avoid token limits and memory overload.

Claude should **never attempt to read an entire PDF file at once.**

---

# Processing Strategy

When a PDF is uploaded to `papers/`:

1. **Inspect the file first**

Check file size and page count.

Example tools: `pdfinfo paper.pdf`, `ls -lh paper.pdf`



If the PDF exceeds ~20 pages or is larger than ~10MB, chunking is recommended.

---

# Chunked Reading Protocol

For large PDFs:

1. Split the document into **small page ranges (3–5 pages)**.
2. Process **one chunk at a time**.
3. Extract key information progressively.

Typical workflow: `papers/paper.pdf
→ papers/paper_chunks/paper_p001-005.pdf
paper_p006-010.pdf
paper_p011-015.pdf`


Claude should build understanding **incrementally**, not by loading the entire paper into memory.

---

# Selective Deep Reading

After scanning chunks:

Claude should identify key sections:

- Introduction
- Model / Methodology
- Data
- Empirical Results
- Conclusion

Appendices and references should only be processed if necessary.

---

# Error Handling

If a PDF chunk cannot be processed:

1. Attempt smaller chunks (1–2 pages).
2. Skip problematic pages and continue.
3. Document missing sections in the analysis report.

---

# Research Workflow Integration

PDF processing supports these skills:

- `lit-review`
- `create-slides`
- `review-paper`

Extracted insights should be saved to: `quality_reports/`, `output/`


Source PDFs in `papers/` must remain unchanged.

---

# Key Principle
`papers/` is read-only source material.
All derived notes, summaries, and slides must go to: `quality_reports/`, `output/`