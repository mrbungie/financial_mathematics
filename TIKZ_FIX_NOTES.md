# TikZ Diagram Fix Summary

## Problem
TikZ diagrams were not rendering in the PDF output.

## Root Cause
The project was trying to use the [quarto_tikz extension](https://github.com/danmackinlay/quarto_tikz) filter, which is primarily designed for HTML output (converting TikZ → SVG via inkscape). For PDF output, this added unnecessary complexity and was causing errors.

## Solution
Converted to **native LaTeX TikZ rendering** for PDF output. This is the recommended approach when:
- Targeting PDF as the primary output format
- You already have a LaTeX distribution with TikZ installed
- You want simpler, more reliable compilation

## Changes Made

### 1. Updated `_quarto.yml`
**Added TikZ library:**
```yaml
include-in-header:
  text: |
    \usepackage{amsmath}
    \usepackage{tikz}
    \usetikzlibrary{arrows,positioning,calc,shapes}
```

**Removed the filter:**
```yaml
# filters:
#   - tikz  # <-- Removed this
```

### 2. Converted TikZ Code Blocks
**Changed from extension syntax:**
```markdown
```{.tikz}
%%| fig-width: 8
%%| fig-height: 3

\begin{tikzpicture}
% TikZ code here
\end{tikzpicture}
```
```

**To raw LaTeX blocks:**
```markdown
```{=latex}
\begin{figure}[h]
\centering
\begin{tikzpicture}
% TikZ code here
\end{tikzpicture}
\end{figure}
```
```

### 3. Files Modified
- `basic_notions.qmd` - 2 TikZ blocks converted
- `bonds.qmd` - 3 TikZ blocks converted
- `value_function.qmd` - 3 TikZ blocks converted
- `interest_rates.qmd` - 3 TikZ blocks converted
- `cheat_sheet.qmd` - 1 TikZ block converted

**Total: 12 TikZ diagrams** converted to native LaTeX format.

## Results

✅ **PDF Output:** All TikZ diagrams now render perfectly via native LaTeX  
✅ **HTML Output:** Compiles successfully (TikZ blocks are PDF-only with `{=latex}`)  
✅ **Compilation:** Faster, simpler, no external filter dependencies  
✅ **Maintainability:** Standard LaTeX approach, widely documented  

## How It Works

### PDF Rendering
1. Quarto processes the `.qmd` files
2. Raw `{=latex}` blocks are passed directly to LaTeX
3. LuaLaTeX compiles the TikZ code natively
4. TikZ diagrams appear as vector graphics in the PDF

### HTML Rendering
- `{=latex}` blocks are ignored in HTML output
- Only Mermaid diagrams appear in HTML
- This is acceptable since the primary target is PDF

## Alternative Approaches

### If you need TikZ in both HTML and PDF:

**Option 1: Use the extension properly**
- Install: `quarto add danmackinlay/quarto_tikz`
- Ensure `pdflatex` and `inkscape` are installed
- Use `{.tikz}` blocks with `%%|` options
- The extension will convert to SVG for HTML and PDF for PDF

**Option 2: Pre-render TikZ to images**
- Compile TikZ diagrams to PDF/SVG separately
- Include them as images: `![Diagram](diagram.pdf)`
- Most control, but extra workflow step

**Option 3: Use Quarto's built-in diagram support**
- For simple diagrams, Mermaid works in both formats
- For complex mathematical diagrams, stick with PDF + native TikZ

## Current Setup: Best Practices

### For PDF (Primary Target)
✅ Use `{=latex}` blocks with TikZ  
✅ Load required TikZ libraries in preamble  
✅ Use LaTeX figure environments for positioning  

### For HTML (Secondary)
✅ Use Mermaid for timelines/flowcharts  
✅ Keep TikZ in PDF-only sections  
✅ Consider providing PDF download for full diagrams  

## Dependencies

**Required for PDF rendering:**
- LaTeX distribution (TeX Live 2025 or similar)
- TikZ/PGF packages (standard in TeX Live)
- LuaLaTeX engine (default in Quarto)

**NOT required:**
- inkscape
- quarto_tikz extension
- dvisvgm
- ghostscript

## Rendering Commands

**Generate PDF:**
```bash
quarto render --to pdf
```

**Generate HTML:**
```bash
quarto render --to html
```

**Generate both:**
```bash
quarto render
```

## Verification

To verify TikZ is working:
1. Open `_output/Financial-Mathematics---Class-1.pdf`
2. Check that timeline diagrams, graphs, and visualizations appear
3. Verify they are sharp vector graphics (zoom in to confirm)

All 12 TikZ diagrams should render as high-quality vector graphics in the PDF.

## Troubleshooting

### "tikz.sty not found"
**Solution:** Install TeX Live full distribution:
```bash
# macOS
brew install mactex-no-gui

# Linux
sudo apt-get install texlive-full
```

### TikZ libraries missing
**Solution:** Add to `_quarto.yml`:
```yaml
include-in-header:
  text: |
    \usetikzlibrary{library-name}
```

### Diagrams not appearing
**Check:**
1. Is the block using `{=latex}` (not `{.tikz}`)?
2. Is rendering targeting PDF (not HTML)?
3. Are there LaTeX errors in the log?

### Want both PDF and HTML with TikZ
**Solution:** Revert to extension approach:
```bash
quarto add danmackinlay/quarto_tikz
# Then convert {=latex} back to {.tikz}
```

## References

- [Quarto Raw Blocks](https://quarto.org/docs/authoring/markdown-basics.html#raw-content)
- [TikZ/PGF Manual](https://ctan.org/pkg/pgf)
- [quarto_tikz Extension](https://github.com/danmackinlay/quarto_tikz)
- [Quarto PDF Options](https://quarto.org/docs/output-formats/pdf-basics.html)

---

**Date:** September 30, 2025  
**Status:** ✅ Fixed and verified  
**Approach:** Native LaTeX TikZ rendering for PDF
