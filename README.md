# aidisclose — Generative AI disclosure checklist and statements

[![CTAN](https://img.shields.io/ctan/v/aidisclose)](https://ctan.org/pkg/aidisclose)
[![Version](https://img.shields.io/badge/version-1.12.0-blue)](https://github.com/joaomlourenco/aidisclose)
[![Date](https://img.shields.io/badge/date-2026--01--23-orange)](https://github.com/joaomlourenco/aidisclose)
[![License: LPPL 1.3c](https://img.shields.io/badge/license-LPPL%201.3c-blue)](https://www.latex-project.org/lppl/lppl-1-3c/)
[![LaTeX](https://img.shields.io/badge/LaTeX-LaTeX2e%202020%2F10%2F01%2B-brightgreen)](https://www.latex-project.org/)

**aidisclose** is a LaTeX package that provides a standardized and transparent mechanism for declaring the use of **Generative Artificial Intelligence (AID)** tools in academic, technical, and professional documents.

The package implements an extension of the **GAIDeT (Generative AI Delegation Taxonomy)** and automates the creation of disclosure statements and task-based checklists, aligned with emerging publisher and institutional requirements.

For the complete manual, full taxonomy, and visual examples, see **[aidisclose-doc.pdf](https://mirrors.ctan.org/macros/latex/contrib/aidisclose/aidisclose-doc.pdf)**.

---

## Introduction

The package allows authors to:

- Select specific tasks delegated to Generative AI from the GAIDeT taxonomy
- Declare the Generative AI tools used (or explicitly state that none were used)
- Add optional explanatory comments (numbered or unnumbered)
- Automatically generate a formatted *Disclosure of Delegation to Generative AI* section or chapter
- Automatically manage citations for both the taxonomy and the package itself

---

## Companion Website (generator)

The package is supported by the companion website **[aidisclose.org](https://aidisclose.org)**.

The website provides an interactive interface where authors can:

- **Fill in authors** and (optionally) the AID tools used
- **Browse the GAIDeT taxonomy** visually and **Select delegated tasks**
- Add multiple comments (numbered or unnumbered), reorder them by drag-and-drop, and preview numbering
- Generate either a **full minimal LaTeX document** or just a **configuration snippet**
- Copy the generated code to the clipboard

If you generate a full document, the website also points you to download `aidisclose.sty` and compile the resulting `.tex` file.

---

## Package Loading and Options

Load the package in the document preamble:

```tex
\usepackage[<options>]{aidisclose}

```

### Options

* **`autobib = true | false`** (default: `true`)
When enabled, the package automatically:
1. Writes an `aidisclose.bib` file containing references for the GAIDeT taxonomy and this package.
2. Loads this bibliography resource (compatible with `biblatex` and standard BibTeX).


Set this option to `false` if you prefer to manage citations manually.
* **`nocite = true | false`** (default: `false`)
This option controls the visible citations in the disclosure statement footnote.
* If `false` (default), the package adds visible citations to the GAIDeT taxonomy paper and the package manual in the footnote.
* If `true`, citations are suppressed in the output (though references are still needed).



---

## Configuration

You can configure the package using the new unified interface (recommended) or individual commands.

### Unified Interface

You can set options and configuration dynamically using key-value lists.

```tex
% 1. Set Package Options
\AIDset{
  autobib = true, 
  nocite = false
}

% 2. Configure Content and Visuals
\AIDconfig{
  tools     = {ChatGPT, Gemini},
  checkmark = {\ding{51}},    % Requires pifont package
  color_used = blue!70!black,
  order     = {preamble, taxonomy, tools, comments}
}

```

### Taxonomy Categories

The taxonomy is organized into 9 phases. Use the corresponding keys (e.g., `c:idea`) with `\AIDactivate{}`.

* **1. Conceptualization** (`c:*`)
* **2. Literature Review** (`l:*`)
* **3. Methodology** (`m:*`)
* **4. Software Development and Automation** (`s:*`)
* **5. Data Management and Analysis** (`d:*`)
* **6. Visuals and Multimedia** (`v:*`)
* **7. Writing and Editing** (`w:*`)
* **8. Ethics Review** (`e:*`)
* **9. Quality Assurance** (`sup:*`)

### List of Commands

| Command | Description |
| --- | --- |
| `\AIDactivate{<key>}` | Activates a specific task in the taxonomy (e.g., `w:draft`). |
| `\AIDtoolsUsed{<list>}` | Defines the list of AI tools used. |
| `\AIDset{<key=val>}` | Sets package boolean options (`autobib`, `nocite`). |
| `\AIDconfig{<key=val>}` | Sets visual and content configuration (colors, order, etc.). |
| `\AIDdiscloseTitle{<title>}` | Customizes the section title. |
| `\AIDorder{<list>}` | Reorders sections (`preamble`, `tools`, `taxonomy`, `comments`). |
| `\AIDrenderDeclaration` | Prints the full disclosure statement. |
| `\AIDloadLanguage{<code>}` | Manually forces a specific language (e.g., `pt`, `fr`). |
| `\AIDpackageName` | Prints the package name with a link to CTAN. |
| `\AIDGetString{<key>}` | Returns the localized string for a specific internal key. |
| `\aidversion` | Prints the current version number. |

---

## Minimal Example

```tex
\documentclass{article}
\usepackage{aidisclose}

\AIDactivate{c:idea}
\AIDactivate{l:sum}
\AIDactivate{w:poly}

\AIDtoolsUsed{ChatGPT-4o, GitHub Copilot}

\begin{AIDcomment}
AI was used for refining code structure in Section 4.
\end{AIDcomment}

\begin{document}

\section{Conclusion}
...

\AIDrenderDeclaration[2]{Mary Doe, John Doe}

\end{document}

```

---

## Internationalization

The package automatically detects the document language via `babel` or `polyglossia` and loads the appropriate translation file.

### Supported Languages

English (default), Catalan, Czech, Danish, Dutch, French, German, Greek, Italian, Polish, Portuguese, Slovak, Spanish, and Ukrainian.

If the detected language is not supported, the package falls back to English.

---

## Utilities

For advanced users:

* **`\AIDloadLanguage{<code>}`**: Manually forces the loading of a language file (e.g., `\AIDloadLanguage{pt}`), overriding auto-detection.
* **`\AIDGetString{<key>}`**: Returns the localized string for a specific internal key.
* **`\AIDpackageName`**: Typesets the package name with a hyperref link.
