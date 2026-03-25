# MY Project Structure and Skills

This document summarizes the folder structure of this project and provides related files in Claude / Claude Code CLI.

---

## Project Structure
MY_Project/
├── CLAUDE.MD # Project guide, instructions
├── MEMORY.MD # memory, and shortcuts
├── agents/ # Task-specific agents
│ ├── proofreader.md # Proofreading agent
│ └── ...
├── skills/ # Workflow controllers
│ ├── proofread.md # Generic proofread skill for Word/LaTeX/Quarto
│ ├── review-paper.md # Manuscript review skill
│ ├── ...
│
├── papers/ # Source manuscripts / notes (.docx, .tex, .pdf, .qmd)
├── data/ # Source data / codes (.docx, .tex, .do, .ipynb)
├── output/ # Generated drafts (slides, Quarto drafts, figures)
├── quality_reports/ # Proofread reports, review logs, plans, literature reviews
├── templates/ # Report templates, notation registry
└── scripts/ # Optional automation scripts (e.g., batch processing)

