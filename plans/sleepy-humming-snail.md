# Plan for converting Word docs to PDF

## Context
The user wants every Word document in
`/Users/my/Desktop/RA/杰青/2026Zhan/本子附件/Word`
duplicated as a same-named PDF inside
`/Users/my/Desktop/RA/杰青/2026Zhan/本子附件/PDF` without altering the
original `.docx` files. This is a filesystem operation (many files) and
we follow a conservative, reversible plan.

## Objective
Create PDFs with identical basenames (UTF-8 / Unicode-aware) for every
`.docx` in the Word directory, placing them in the PDF directory. Do not
modify or move any `.docx` files.

## Approach / Steps
1. Inspect source directory and list `.docx` files (dry-run). Verify how
   many files and sample names (handles spaces and Unicode).
2. Ensure output directory exists: run mkdir -p (quoted path to preserve
   spaces and Unicode).
3. Confirm a PDF converter is available (prefer: libreoffice). If
   libreoffice is not installed, report this and offer an installation
   command (do not install automatically without permission).
4. Do a small sample conversion (1–3 files) to validate conversion quality
   and filename correctness (Unicode, fonts, images).
5. If samples look correct, run the full conversion in a loop. Quote all
   paths when invoking the converter to avoid issues with spaces/Unicode.
6. Verify: compare number of `.docx` files to number of generated
   `.pdf` files and check for any missing basenames.
7. Manually open 1–3 sample PDFs (Preview) so the user can confirm
   visual integrity.
8. Leave original `.docx` files untouched.

## Important notes / safety
- All shell commands MUST quote paths to handle spaces and Unicode.
- This will only create new `.pdf` files under the `PDF` directory. If
  a PDF with the same name already exists it will be overwritten by
  libreoffice; if you want to avoid overwriting, ask and we will run a
  safeguarded script that skips existing PDFs or appends a suffix.
- We will not modify or delete any files in `Word`.

## Commands (examples to run when executing plan)
Replace <WORD_DIR> and <PDF_DIR> with the exact paths below (they are
already the user's paths):

WORD_DIR="/Users/my/Desktop/RA/杰青/2026Zhan/本子附件/Word"
PDF_DIR="/Users/my/Desktop/RA/杰青/2026Zhan/本子附件/PDF"

# 1) Dry-run: list files and count
find "$WORD_DIR" -maxdepth 1 -type f -name '*.docx' -print0 | xargs -0 -I{} basename "{}"

# 2) Make the PDF dir (idempotent)
mkdir -p "$PDF_DIR"

# 3) Check libreoffice availability
command -v libreoffice || command -v soffice

# 4) Sample conversion (first 2 files)
for f in "$WORD_DIR"/*.docx; do [ -e "$f" ] || break; echo "Converting: $f"; libreoffice --headless --convert-to pdf --outdir "$PDF_DIR" "$f"; break; done

# 5) Full conversion loop (safe, quoted paths)
for f in "$WORD_DIR"/*.docx; do
  [ -e "$f" ] || continue
  libreoffice --headless --convert-to pdf --outdir "$PDF_DIR" "$f"
done

# 6) Verification: counts and missing PDFs
docx_count=$(find "$WORD_DIR" -maxdepth 1 -type f -name '*.docx' | wc -l)
pdf_count=$(find "$PDF_DIR" -maxdepth 1 -type f -name '*.pdf' | wc -l)
echo "docx: $docx_count  pdf: $pdf_count"

# 7) Report any missing basenames
for f in "$WORD_DIR"/*.docx; do
  [ -e "$f" ] || continue
  base=$(basename "$f" .docx)
  if [ ! -f "$PDF_DIR/$base.pdf" ]; then
    echo "MISSING PDF for: $base"
  fi
done

# 8) Open a couple samples for manual inspection (macOS Preview)
ls -1 "$PDF_DIR" | head -n 3 | while read p; do open -a Preview "$PDF_DIR/$p"; done

## Fallbacks / Alternatives
- If libreoffice is not available, options include:
  - Ask the user to install LibreOffice (e.g., `brew install --cask libreoffice`) or
  - Use Microsoft Word via AppleScript/Automator (requires Word app and
    scripting; more complex and interactive). Do not attempt this
    without user confirmation.

## Verification checklist (post-run)
- [ ] docx_count == pdf_count
- [ ] No "MISSING PDF" messages
- [ ] A few sample PDFs open correctly and visually match the DOCX
- [ ] Original `.docx` timestamps and contents unchanged

## Files touched
- Read-only (source): /Users/my/Desktop/RA/杰青/2026Zhan/本子附件/Word/*.docx
- New files (output): /Users/my/Desktop/RA/杰青/2026Zhan/本子附件/PDF/*.pdf
- Plan file updated: /Users/my/.claude/plans/sleepy-humming-snail.md

## Next step
If this plan looks good, I will exit plan mode and request your
permission to run the commands. I will first run the dry-run and sample
conversion. If you prefer a non-overwriting run, tell me and I will use
an alternate loop that skips existing PDFs or writes with a suffix.

