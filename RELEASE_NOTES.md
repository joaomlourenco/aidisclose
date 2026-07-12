## aidisclose v1.13.0 (2026-07-12)
Maintenance and refinement release. No changes to the public command interface.

### Bug Fixes
*   Added the missing `<declares>` placeholder to the preamble substitution (previously only `<acknowledges>` and `<accept>` were replaced).
*   Declared the internal `\l__aid_iso_code_tl` variable explicitly (it was used without a prior declaration).
*   Used global assignment (`\clist_gset` / `\int_gset`) for the global author-context variables.

### Improvements
*   Made the taxonomy rendering helpers (`\TGroup`, `\TItems`, `\TItem`) protected for safer expansion.
*   Renamed the internal `\_aid_label:` to `\__aid_label:` to follow the expl3 naming convention.
*   Removed unused internal variables.
*   Slightly widened the checklist label box (`labelwidth`).

### Language Files
*   Added a reference to the companion website ([aidisclose.org](https://aidisclose.org)) in the disclosure footnote across all 14 languages.

### Documentation
*   Documented CTAN availability in the README and the manual.

---

## Initial Release: aidisclose v1.12.0
**aidisclose** is a LaTeX package designed to provide a standardized, transparent, and automated mechanism for declaring the use of Generative AI (GenAI) in academic and professional documents.
This package implements an extension of the **GAIDeT (Generative AI Delegation Taxonomy)**, allowing authors to precisely specify which tasks were delegated to AI too during the research and writing process.

### ✨ Key Features
*   **Standardized Disclosure:** Automatically generates formatted disclosure statements and checklists.
*   **GAIDeT Implementation:** Full support for the 9-phase taxonomy (Conceptualization, Literature Review, Methodology, Software, Data, Visual Writing, Ethics, Quality Assurance).
*   **Multilingual Support:** Auto-detection for **14 languages** (English, Catalan, Czech, Danish, Dutch, French, German, Greek, Italian, Polish, Portuguese, Slovak, Spanish, Ukrainian).
*   **Unified Configuration:** Easy setup via `\AIDconfig` and `\AIDset` for customizing visuals, colors, and order.
*   **Bibliography Management:** Automatically handles citations for the taxonomy and package (`autobib` option).
*   **Companion Tool:** Fully compatible with the LaTeX generator at [aidisclose.org](https://aidisclose.org).

### Installation
Available on CTAN: [ctan.org/pkg/aidisclose](https://ctan.org/pkg/aidisclose). The package ships with TeX Live and MiKTeX.

*   **TeX Live:** `tlmgr install aidisclose`
*   **MiKTeX:** install via the MiKTeX Console / Package Manager
*   **Manual:** download `aidisclose.sty` and the `langdef/` folder from [GitHub](https://github.com/joaomlourenco/aidisclose) and place them in your project directory or local TeX tree.

### Usage Example
    \usepackage{aidisclose}

    % Configure
    \AIDactivate{c:idea}   % Activate "Idea generation"
    \AIDactivate{w:poly}   % Activate "Polishing and Editing"
    \AIDtoolsUsed{ChatGPT, GitHub Copilot}

    % Render
    \AIDrenderDeclaration[ncols=2]{Author Name}

See the `aidisclose-doc.pdf` for full documentation and examples.
