# PRD — Quarto Reinterpretation of *Financial Mathematics (First Class)*

## 1. Goal

Create a student-friendly Quarto document (or multiple, if so create a folder structure) that turns the original lecture slides into:

* **Clear diagrams** that bridge math notation ↔ everyday finance examples.
* **Tables & timelines** instead of heavy notation when possible.
* **Cheat sheet** summarizing definitions, formulas, and conventions.
* **Exercises** for practice with cashflows, interest, and value functions.

Target audience: MBA students (varied quantitative backgrounds, some non-finance).

---

## 2. Scope

* **Source material**: *FinancialMathematics_FirstClass.pdf* (pages 1–49 at minimum).
* **Reinterpreted content**:

  * Copy directly when simple (e.g., cashflow tables, clean diagrams).
  * Simplify and redraw when overly abstract (e.g., value function decomposition, interest rate definitions).
* Deliverables: Quarto `.qmd` chapters, rendered PDF/HTML with diagrams, cheat sheet, exercises.

---

## 3. Content Mapping

### Section A: Basic Notions (pp. 5–24)

* **Keep**: Cashflow tables & timelines (pp. 5, 7, 8, 10, 20–21).
* **Change**:

  * (pp. 14–19) Notation should be simplified → use dual representations:

    * *Cashflow table*
    * *Time diagram*
  * Highlight sign convention with simple “Money In vs Money Out” color coding.

### Section B: Bonds (pp. 24–30)

* **Keep**: Simple coupon bond table (p. 25).
* **Change**:

  * Accrued interest (pp. 28–29) → replace algebraic formula with a **timeline bar showing elapsed vs remaining period**.
  * Dirty vs clean price → show with **two stacked boxes** (Market Price + Accrued Interest).

### Section C: Value Function (pp. 33–42)

* **Keep**: Definition tables (p. 34, p. 36).
* **Change**:

  * Multi-period decomposition (pp. 35–41) → instead of multiple overlapping formulas, use a **step-by-step cumulative cashflow graph**.
  * Emphasize “value function = smoothed story of money over time”.

### Section D: Interest & Discount Rates (pp. 42–49)

* **Keep**: Definitions tables (p. 43, p. 46).
* **Change**:

  * Show accumulation vs discount with **mirrored diagrams** (forward vs backward).
  * Use “money lens” analogy → accumulation = telescope (future larger), discount = microscope (back to present).

---

## 4. Cheat Sheet (Final Section)

One-page **high-density summary** with:

* Core formulas (interest rate, discount factor, accumulation factor).
* Time conventions (ACT/ACT, ACT/360, 30/360).
* Bond pricing components (Face Value, Coupon, Accrued Interest, Clean vs Dirty Price).
* Cashflow types (Investment vs Financing).
* Visual cues (timeline icons).

---

## 5. Exercises (Final Section)

* **Exercise 1: Cashflow table → Interest split**
  Given a 3-year loan with fixed installments, fill missing interest/principal parts.

* **Exercise 2: Bond dirty price**
  Compute accrued interest & dirty price from quotation.

* **Exercise 3: Value function graphing**
  Plot V(t) given simple cashflows & rates.

* **Exercise 4: Compare conventions**
  Compute year fraction for same dates using ACT/ACT, ACT/360, 30/360.

Each exercise links back to original slide pages for context.

---

## 6. Technical Notes (Quarto)

* Use **`quarto-diagram`** (mermaid or tikz) for timelines.
* Use **callout blocks** for *definitions* vs *remarks*.
* Add **math live preview** for formulas but keep text explanations always.
