# Financial Mathematics - Class 1

A student-friendly Quarto book reinterpreting traditional financial mathematics lecture materials for MBA students with varied quantitative backgrounds.

## 📚 Overview

This interactive guide transforms dense lecture slides into:

- **Clear visual diagrams** connecting math notation to real-world finance
- **Tables & timelines** for intuitive understanding
- **Practical examples** from everyday finance scenarios
- **Comprehensive cheat sheet** for quick reference
- **Practice exercises** with detailed solutions

## 🎯 Target Audience

MBA students with varied quantitative backgrounds, particularly those seeking:
- Clear explanations over mathematical rigor
- Visual learning approaches
- Practical applications
- Self-paced study materials

## 📖 Contents

1. **Basic Notions** - Cashflows, timelines, sign conventions
2. **Bonds** - Coupon bonds, accrued interest, clean vs dirty prices
3. **Value Function** - Understanding money over time, NPV
4. **Interest & Discount Rates** - Accumulation, discount factors, compounding
5. **Cheat Sheet** - One-page reference for all key formulas
6. **Exercises** - Practice problems with comprehensive solutions

## 🚀 Getting Started

### Prerequisites

You'll need [Quarto](https://quarto.org/) installed on your system.

**Install Quarto**:
- **macOS**: `brew install quarto` (using Homebrew)
- **Windows/Linux**: Download from [quarto.org](https://quarto.org/docs/get-started/)

**Verify installation**:
```bash
quarto --version
```

### Rendering the Book

Navigate to the project directory and render:

```bash
cd /Users/goviedb/Development/MIB/FinMaths/classes/class_1
quarto render
```

This will generate:
- **HTML version**: `_output/index.html` (interactive, recommended for screen)
- **PDF version**: `_output/Financial-Mathematics---Class-1.pdf` (for printing)

### Previewing During Development

For live preview with auto-reload:

```bash
quarto preview
```

This opens a browser window that automatically updates as you edit `.qmd` files.

## 📂 Project Structure

```
class_1/
├── _quarto.yml           # Quarto configuration
├── index.qmd             # Welcome page
├── basic_notions.qmd     # Chapter 1: Cashflows & timelines
├── bonds.qmd             # Chapter 2: Bond pricing
├── value_function.qmd    # Chapter 3: Value function & NPV
├── interest_rates.qmd    # Chapter 4: Interest rates & discounting
├── cheat_sheet.qmd       # Quick reference guide
├── exercises.qmd         # Practice problems
├── references.bib        # Bibliography (if needed)
├── README.md             # This file
├── PRD/
│   └── PRD_1.md         # Product requirements document
└── _output/             # Generated files (HTML/PDF)
```

## 🎨 Features

### Visual Learning

- **Mermaid diagrams** for timelines and flowcharts
- **TikZ graphics** for mathematical visualizations
- **Color-coded cashflows** (green = inflow, red = outflow)

### Interactive Elements

- **Callout blocks** for definitions, tips, warnings
- **Collapsible solutions** (click to reveal answers)
- **Cross-references** between chapters
- **Searchable HTML version**

### Pedagogical Design

- **"Money lens" analogies** (telescope/microscope for accumulation/discount)
- **Dual representations** (tables + timelines + diagrams)
- **Progressive complexity** (simple examples first, then realistic scenarios)
- **Common pitfalls** highlighted throughout

## 🔧 Customization

### Changing Themes

Edit `_quarto.yml`:

```yaml
format:
  html:
    theme: cosmo  # Try: minty, flatly, united, etc.
```

### Output Formats

Generate only HTML:
```bash
quarto render --to html
```

Generate only PDF:
```bash
quarto render --to pdf
```

### Adding Content

1. Create new `.qmd` file
2. Add to `_quarto.yml` under `chapters:`
3. Run `quarto render`

## 📋 Using the Materials

### For Students

1. **First time**: Read chapters 1-4 in order
2. **Review**: Use the cheat sheet for quick reference
3. **Practice**: Work through exercises with pen and paper
4. **Stuck?**: Review relevant chapter, then check solution

### For Instructors

- **Modular design**: Use individual chapters as needed
- **Editable source**: All content in plain text `.qmd` files
- **Extend**: Add your own exercises or examples
- **Customize**: Adjust difficulty, add industry-specific cases

## 🧮 Mathematics Rendering

The book uses **MathJax** for HTML and **LaTeX** for PDF. All formulas render beautifully:

Inline: $V(t) = \sum_{i=0}^{n} \frac{C_i}{(1+r)^{t_i}}$

Display:
$$
\text{NPV} = \sum_{t=0}^{n} \frac{C_t}{(1+i)^t}
$$

## 🐛 Troubleshooting

### Rendering Issues

**Problem**: "quarto: command not found"  
**Solution**: Install Quarto or add to PATH

**Problem**: TikZ diagrams not rendering in PDF  
**Solution**: Ensure LaTeX is installed (`tlmgr install tikz`)

**Problem**: Mermaid diagrams not showing  
**Solution**: Use HTML output (Mermaid not supported in PDF)

### Content Issues

**Problem**: Formulas not displaying  
**Solution**: Check for unescaped special characters (%, $, etc.)

**Problem**: Cross-references broken  
**Solution**: Ensure target exists and has proper `{#sec-label}` syntax

## 📝 Contributing

This is a living document! Suggestions for improvement:

1. **Clarity**: Flag confusing explanations
2. **Errors**: Report typos or calculation mistakes
3. **Examples**: Suggest additional real-world scenarios
4. **Exercises**: Propose new practice problems
5. **Visuals**: Suggest better diagrams or analogies

## 📄 License

This educational material is provided for academic use. Please attribute appropriately when sharing or adapting.

## 🙏 Acknowledgments

Based on traditional financial mathematics course materials, reinterpreted with a focus on accessibility and visual learning for MBA students.

## 📞 Support

For questions or issues:
- Review the [Cheat Sheet](cheat_sheet.qmd) for quick answers
- Consult the [Exercises](exercises.qmd) for worked examples
- Check individual chapters for detailed explanations

---

**Ready to learn?** Start with [index.qmd](index.qmd) or run `quarto preview` to begin!

---

## 🔖 Quick Commands Reference

| Command | Purpose |
|---------|---------|
| `quarto render` | Build HTML + PDF |
| `quarto preview` | Live preview (auto-reload) |
| `quarto render --to html` | Build HTML only |
| `quarto render --to pdf` | Build PDF only |
| `quarto check` | Verify installation |

---

*Last updated: September 30, 2025*
