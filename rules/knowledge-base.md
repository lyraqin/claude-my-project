---
paths = [
  "Slides/**/*.tex",
  "Quarto/**/*.qmd",
  "scripts/**/*.R"
]

description = "Central knowledge base governing notation, lecture flow, empirical examples, and coding standards for the course."

version = "1.0"
---

# Course Knowledge Base

Claude must consult this file before creating or modifying any lecture slides, Quarto documents, or R scripts.  
All generated material must conform to the notation, structure, and design principles defined below.

---

# 1. Notation Registry

Maintain consistent notation across lectures.

| Rule | Convention | Example | Anti-Pattern |
|-----|------------|---------|--------------|
| Scalars | Lowercase italics | \(x, y, \alpha\) | Using uppercase for scalars |
| Vectors | Bold lowercase | **x**, **β** | Mixing bold and non-bold |
| Matrices | Bold uppercase | **X**, **Σ** | Using lowercase matrices |
| Expectations | \(E[\cdot]\) notation | \(E[Y|X]\) | Writing mean() in math slides |
| Probabilities | \(P(\cdot)\) | \(P(Y=1|X)\) | Writing Pr() or prob() |

Claude should never introduce new notation if an equivalent already exists.

---

# 2. Symbol Reference

Central registry of symbols introduced across lectures.

| Symbol | Meaning | Introduced |
|------|---------|-----------|
| \(Y_i\) | Outcome variable | Lecture 1 |
| \(X_i\) | Covariate vector | Lecture 1 |
| \(D_i\) | Treatment indicator | Lecture 3 |
| \(ATE\) | Average Treatment Effect | Lecture 4 |

If Claude introduces a new symbol, it must be added to this table.

---

# 3. Lecture Progression

Ensures logical progression across lectures.

| # | Title | Core Question | Key Notation | Key Method |
|---|------|--------------|-------------|-----------|
| 1 | Introduction to Empirical Finance | What questions do we study? | \(Y,X\) | Regression |
| 2 | Causal Inference Basics | When does correlation imply causation? | \(D,Y(1),Y(0)\) | Potential Outcomes |
| 3 | Instrumental Variables | How to address endogeneity? | \(Z\) | IV Estimation |

Claude must maintain conceptual continuity across lectures.

---

# 4. Empirical Applications

Real research examples used for teaching.

| Application | Paper | Dataset | Lecture(s) | Purpose |
|------------|------|--------|------------|---------|
| Monetary Policy & Stocks | Fed Communication Study | FOMC transcripts | Lecture 5 | Text analysis |
| Climate Risk | Green Innovation Study | Firm ESG data | Lecture 7 | Asset pricing |

Applications must illustrate the lecture's methodological focus.

---

# 5. Design Principles

Pedagogical design guidelines.

| Principle | Evidence | Lectures Applied |
|----------|---------|----------------|
| One concept per slide | Cognitive load theory | All |
| Show intuition before math | Teaching research | 1–10 |
| Include empirical example | Applied learning | 3–10 |

Claude should prefer intuition → method → empirical example.

---

# 6. Anti-Patterns

Common mistakes to avoid.

| Anti-Pattern | What Happened | Correction |
|--------------|--------------|-----------|
| Too many equations | Slides became unreadable | Split across slides |
| Undefined symbols | Students confused | Add to Symbol Registry |
| No empirical context | Method lacked motivation | Add research example |

Claude should actively detect and avoid these patterns.

---

# 7. R Code Standards

Rules for scripts in `scripts/`.

| Standard | Rule |
|--------|------|
| Style | Use tidyverse conventions |
| Reproducibility | Set random seed |
| Output | Save figures to `/figures/` |
| Documentation | Comment key steps |

Example:

```r
set.seed(123)

library(tidyverse)

data <- read_csv("data/input.csv")

#8. R Code Pitfalls

| Anti-Pattern | What Happened | Correction | 

| Bug            | Impact           | Fix                    |
| --------------- | ------------------ | ---------------------- |
| Missing `set.seed()`  | Non-reproducible results      | Add seed at top        |
| Hard-coded paths      | Code breaks on other machines | Use relative paths     |
| Silent NA propagation | Incorrect estimates           | Check with `summary()` |
