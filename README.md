# 📦 MY Project Structure and Skills

![Project Status](https://img.shields.io/badge/status-active-success)
![Maintained](https://img.shields.io/badge/maintained-yes-blue)
![Made with Claude](https://img.shields.io/badge/powered%20by-Claude-orange)

This repository defines a structured workflow for academic writing, proofreading, and research automation using **Claude / Claude Code CLI**.

---

## 📑 Table of Contents

* [📦 Project Overview](#-project-overview)
* [📁 Project Structure](#-project-structure)
* [🧠 Agents](#-agents)
* [⚙️ Skills](#️-skills)
* [📄 Data & Outputs](#-data--outputs)
* [🚀 Usage](#-usage)
* [🧩 Customization](#-customization)
* [📌 Notes](#-notes)

---

## 📦 Project Overview

This project organizes research workflows into modular components:

* **Agents** → task-specific roles (e.g., proofreading)
* **Skills** → reusable workflows and pipelines
* **Data & Papers** → research inputs
* **Outputs** → generated results and drafts

Designed for:

* Academic writing
* Paper reviewing
* Research automation
* Reproducible workflows

---

## 📁 Project Structure

```
MY_Project/
├── CLAUDE.MD            # Project guide and instructions
├── MEMORY.MD            # Memory and shortcuts
│
├── agents/              # Task-specific agents
│   ├── proofreader.md   # Proofreading agent
│   └── ...
│
├── skills/              # Workflow controllers
│   ├── proofread.md     # Generic proofread skill
│   ├── review-paper.md  # Manuscript review skill
│   └── ...
│
├── papers/              # Source manuscripts / notes
│                         # (.docx, .tex, .pdf, .qmd)
│
├── data/                # Source data / code
│                         # (.docx, .tex, .do, .ipynb)
│
├── output/              # Generated drafts
│                         # (slides, Quarto drafts, figures)
│
├── quality_reports/     # Reports, logs, literature reviews
│
├── templates/           # Templates and notation registry
│
└── scripts/             # Automation scripts
                          # (e.g., batch processing)
```

---

## 🧠 Agents

Agents are **task-specific AI roles**.

Example:

* `proofreader.md` → handles grammar, clarity, academic tone

You can extend:

* Reviewer agent
* Summarizer agent
* Code assistant agent

---

## ⚙️ Skills

Skills are **workflow-level abstractions** that coordinate tasks.

Examples:

* `proofread.md`

  * Works across formats: Word / LaTeX / Quarto
  * Produces structured proofreading reports

* `review-paper.md`

  * Simulates journal-style peer review
  * Generates comments, suggestions, and decisions

---

## 📄 Data & Outputs

### Input

* `papers/` → manuscripts, drafts, notes
* `data/` → datasets, scripts, notebooks

### Output

* `output/` → generated drafts, slides, figures
* `quality_reports/` →

  * proofreading reports
  * review logs
  * literature summaries

---

## 🚀 Usage

### 1. Prepare inputs

Place files into:

```
papers/
data/
```

### 2. Select a skill

Examples:

* Proofreading → `skills/proofread.md`
* Paper review → `skills/review-paper.md`

### 3. Run via Claude CLI

Example workflow:

```
1. Load agent
2. Apply skill
3. Generate output
```

### 4. Check outputs

Results will appear in:

```
output/
quality_reports/
```

---

## 🧩 Customization

You can easily extend the system:

### Add a new agent

```
agents/
└── your-agent.md
```

### Add a new skill

```
skills/
└── your-workflow.md
```

### Add templates

```
templates/
```

---

## 📌 Notes

* Keep naming consistent across agents and skills
* Store reusable prompts in `templates/`
* Maintain logs in `quality_reports/` for reproducibility
* Use `scripts/` for batch automation if needed


---

## 🙌 Acknowledgements

Built for structured research workflows using Claude and modern AI-assisted writing tools.

