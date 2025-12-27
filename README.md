# aidisclose — Generative AI disclosure checklist and statements

[![CTAN](https://img.shields.io/ctan/v/aidisclose)](https://ctan.org/pkg/aidisclose)
[![Version](https://img.shields.io/badge/version-1.4.0-blue)](https://github.com/joaomlourenco/aidisclose)
[![Date](https://img.shields.io/badge/date-2025--12--25-orange)](https://github.com/joaomlourenco/aidisclose)
[![License: LPPL 1.3c](https://img.shields.io/badge/license-LPPL%201.3c-blue)](https://www.latex-project.org/lppl/lppl-1-3c/)
[![LaTeX](https://img.shields.io/badge/LaTeX-LaTeX2e%202020%2F10%2F01%2B-brightgreen)](https://www.latex-project.org/)

**aidisclose** is a LaTeX package that provides a standardized and transparent mechanism for declaring the use of **Generative Artificial Intelligence (GAI)** tools in academic, technical, and professional documents.

The package implements the **GAIDeT (Generative AI Delegation Taxonomy)** and automates the creation of disclosure statements and task-based checklists, aligned with emerging publisher and institutional requirements.

For the complete manual, full taxonomy, and visual examples, see **[aidisclose-doc.pdf](aidisclose-doc.pdf)**.

---

## Introduction

The package allows authors to:

- Select specific tasks delegated to Generative AI from the GAIDeT taxonomy
- Declare the Generative AI tools used (or explicitly state that none were used)
- Add optional explanatory comments (numbered or unnumbered)
- Automatically generate a formatted *Disclosure of Delegation to Generative AI* section or chapter
- Automatically manage citations for both the taxonomy and the package itself

---

## Package loading and options

Load the package in the document preamble:

```tex
\usepackage[<options>]{aidisclose}
```

### Options

- **`autobib = true | false`** (default: `true`)

When enabled, the package will automatically:

1. Writes an `aidisclose.bib` file containing references for the GAIDeT taxonomy and this package
2. Loads this bibliography resource (compatible with `biblatex` and standard BibTeX)

Set this option to `false` if you prefer to manage citations manually.

**NOTE:** if you use the package, please give credit to both the author of this package and the authors of the DAIDeT taxonomy.

---

## Internationalization

The package automatically detects the document language via `babel` or `polyglossia` and loads the appropriate translation file.

### Supported languages (v1.6.0)

English (default), Catalan, Czech, Danish, Dutch, French, German, Greek, Italian, Polish, Portuguese, Slovak, Spanish, and Ukrainian.

If the detected language is not supported, the package falls back to English.

---

## Taxonomy overview

Tasks are activated using short identifiers derived from the GAIDeT taxonomy, grouped into the following categories:

- Conceptualization
- Literature Review
- Methodology
- Software Development
- Data Management
- Writing and Editing
- Ethics Review
- Supervision

The complete list of keys and descriptions is provided in **[aidisclose-doc.pdf](aidisclose-doc.pdf)**.

---

## Usage

The disclosure process consists of two steps:

1. **Configuration** — defining what was done
2. **Rendering** — printing the declaration

### Activating taxonomy items

Use `\GAIactivate{}` to mark specific tasks as delegated to Generative AI.

```tex
\GAIactivate{c:idea}
\GAIactivate{s:opt}
```

### Specifying tools

Use `\GAItoolsUsed{}` to list the Generative AI tools employed.

```tex
% No tools used
\GAItoolsUsed{}

% Multiple tools
\GAItoolsUsed{ChatGPT-4, Gemini Advanced, Claude 3}
```

### Adding comments

Use the `GAIcomment` (numbered) and `GAIcomment*` (unnumbered) environments.

```tex
\begin{GAIcomment}
The AI was used primarily for refining the code in Section 3.
\end{GAIcomment}

\begin{GAIcomment*}
No GAI tools were used for data analysis.
\end{GAIcomment*}
```

### Customizing the title

Change the default title and sectioning level:

```tex
\GAIdiscloseTitle[Short Title]{Full Title}[section]
```

### Visual customization

- Checkmark symbol:
  
  ```tex
  \GAIsetCheckmarkSymbol{\texttimes}
  ```

- Checklist font size:
  
  ```tex
  \GAIsetChecklistFontSize{\small}
  ```

---

## Rendering the declaration

Place the rendering command where you want the disclosure to appear:

```tex
\GAIrenderDeclaration[<columns>]{<authors>}
\GAIrenderDeclaration*[<columns>]{<authors>}
```

- Starred form omits the section heading
- `<columns>` defaults to `3`
- `<authors>` is a comma-separated list of authors

---

## Minimal example

```tex
\GAIactivate{c:idea}
\GAIactivate{c:rq}
\GAIactivate{l:search}
\GAIactivate{l:write}
\GAIactivate{s:auto}
\GAIactivate{d:analyze}
\GAIactivate{w:summarize}
\GAIactivate{w:reformat}

\GAItoolsUsed{ChatGPT-4o, Gemini 1.5 Pro, GitHub Copilot}

\begin{GAIcomment}
AI was used for refining code structure in Section 4.
\end{GAIcomment}

\GAIrenderDeclaration[2]{Mary Doe, John Doe, Jane Doe}
```

---

## Example output (summary)

The rendered declaration includes:

- A responsibility statement naming the authors
- A checklist of delegated tasks organized by taxonomy category
- A declaration of Generative AI tools used (or an explicit statement that none were declared)
- Optional additional comments

See **[aidisclose-doc.pdf](aidisclose-doc.pdf)** for the full rendered example.

---

## Documentation

- **[aidisclose-doc.pdf](aidisclose-doc.pdf)** — complete documentation and examples
- [`aidisclose-doc.tex`](aidisclose-doc.tex) — documentation source
- https://ctan.org/pkg/aidisclose

---

## License

This package is distributed under the **LaTeX Project Public License (LPPL) 1.3c** or later.

---

Copyright © 2025-26 João M. Lourenço.  
Crafted with 💙 for reproducible scientific writing.
