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
This package is available on CTAN and can be installed via your TeX distribution manager (TeX Live, MiKTeX).
For manual [installation from GitHub](https://github.com/joaomlourenco/aidisclose):
1.  Download `aidisclose.sty` and the `langdef/` folder.
2.  Place them in your project directory or local TeX tree.

### Usage Example
  \usepackage{aidisclose}

  % Configure
  \AIDactivate{c:idea}   % Activate "Idea generation"
  \AIDactivate{w:poly}   % Activate "Polishing and Editing"
  \AIDtoolsUsed{ChatGPT, GitHub Copilot}

  % Render
  \AIDrenderDeclaration[ncols=2]{Author Name}
  
See the `aidisclose-doc.pdf` for full documentation and examples.
