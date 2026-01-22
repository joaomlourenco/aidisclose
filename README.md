# aidisclose — Generative AI disclosure checklist and statements

[![CTAN](https://img.shields.io/ctan/v/aidisclose)](https://ctan.org/pkg/aidisclose)
[![Version](https://img.shields.io/badge/version-1.8.1-blue)](https://github.com/joaomlourenco/aidisclose)
[![Date](https://img.shields.io/badge/date-2026--01--20-orange)](https://github.com/joaomlourenco/aidisclose)
[![License: LPPL 1.3c](https://img.shields.io/badge/license-LPPL%201.3c-blue)](https://www.latex-project.org/lppl/lppl-1-3c/)
[![LaTeX](https://img.shields.io/badge/LaTeX-LaTeX2e%202020%2F10%2F01%2B-brightgreen)](https://www.latex-project.org/)

**aidisclose** is a LaTeX package that provides a standardized and transparent mechanism for declaring the use of **Generative Artificial Intelligence (AID)** tools in academic, technical, and professional documents.

The package implements an extension of the **AIDDeT (Generative AI Delegation Taxonomy)** and automates the creation of disclosure statements and task-based checklists, aligned with emerging publisher and institutional requirements.

For the complete manual, full taxonomy, and visual examples, see **[aidisclose-doc.pdf](aidisclose-doc.pdf)**.

---

## Introduction

The package allows authors to:

- Select specific tasks delegated to Generative AI from the AIDDeT taxonomy
- Declare the Generative AI tools used (or explicitly state that none were used)
- Add optional explanatory comments (numbered or unnumbered)
- Automatically generate a formatted *Disclosure of Delegation to Generative AI* section or chapter
- Automatically manage citations for both the taxonomy and the package itself

---

## Companion Website (generator)

The package is supported by the companion website **[aidisclose.org](https://aidisclose.org)**.

The website provides an interactive interface where authors can:

- **Fill in authors** and (optionally) the AID tools used
- **Browse the AIDDeT taxonomy** visually and **Select delegated tasks**.
- **Select delegated tasks** from the AIDDeT taxonomy
- Add multiple comments (numbered or unnumbered), reorder them by drag-and-drop, and preview numbering
- Generate either a **full minimal LaTeX document** or just a **configuration snippet**
- Copy the generated code to the clipboard

If you generate a full document, the website also points you to download `aidisclose.sty` and compile the resulting `.tex` file.

---

## Package loading and options

Load the package in the document preamble:

```tex
\usepackage[<options>]{aidisclose}
```

### Options

* **`autobib = true | false`** (default: `true`)

When enabled, the package will automatically:

1. Writes an `aidisclose.bib` file containing references for the AIDDeT taxonomy and this package
2. Loads this bibliography resource (compatible with `biblatex` and standard BibTeX)

Set this option to `false` if you prefer to manage citations manually.

**NOTE:** if you use the package, please give credit to both the author of this package and the authors of the DAIDeT taxonomy.

---

## Internationalization

The package automatically detects the document language via `babel` or `polyglossia` and loads the appropriate translation file.

### Supported languages (v1.8.1)

English **(default)**, Catalan, Czech, Danish, Dutch, French, German, Greek, Italian, Polish, Portuguese, Slovak, Spanish, and Ukrainian (*there were automatic translations, please contribute with fixes*).

If the detected language is not supported, the package falls back to English.

---

## Taxonomy overview

Tasks are activated using short identifiers derived from the AIDDeT taxonomy, grouped into the following categories:

* Conceptualization
* Literature Review
* Methodology
* Software Development and Automation
* Data Management
* Visuals and Multimedia
* Writing and Editing
* Ethics Review
* Quality Assurance

The complete list of keys and descriptions is provided in **[aidisclose-doc.pdf](https://www.google.com/search?q=aidisclose-doc.pdf)**.

---

## Usage

The disclosure process consists of two steps:

1. **Configuration** — defining what was done
2. **Rendering** — printing the declaration

### Activating taxonomy items

Use `\AIDactivate{}` to mark specific tasks as delegated to Generative AI. The keys use colons (:) to separate the category from the task.

```tex
\AIDactivate{c:idea}
\AIDactivate{s:opt}
```

### Specifying tools

Use `\AIDtoolsUsed{}` to list the Generative AI tools employed.

```tex
% No tools used
\AIDtoolsUsed{}

% Multiple tools
\AIDtoolsUsed{ChatGPT-4, Gemini Advanced, Claude 3}
```

### Adding comments

Use the `AIDcomment` (numbered) and `AIDcomment*` (unnumbered) environments.

```tex
\begin{AIDcomment}
The AI was used primarily for refining the code in Section 3.
\end{AIDcomment}

\begin{AIDcomment*}
No AID tools were used for data analysis.
\end{AIDcomment*}
```

### Customizing the title

Change the default title and sectioning level:

```tex
\AIDdiscloseTitle[Short Title]{Full Title}[section]
```

To retrieve these values later, you can use `\AIDdiscloseTitleLong` and `\AIDdiscloseTitleShort`.

### Visual customization
   
* Checkmark symbol:
 ```tex
 \AIDcheckmarkSymbol{\texttimes}

 ```

* Checklist font size:

 ```tex
 \AIDchecklistFontSize{\small}

 ```

* Colors:

 ```tex
 \AIDusedColor{black}         % Active items text color
 \AIDboxUsedColor{black}      % Box outline color
 \AIDunusedColor{black!50}    % Inactive items text color
 \AIDboxUnusedColor{black!50} % Box outline color
 \AIDcheckmarkColor{black}    % Checkmark symbol color

 ```
 

---

## Advanced Customization (New in v1.8.1)

### Layout Ordering

You can customize the order in which the disclosure components appear using `\AIDorder`. The valid components are `preamble`, `tools`, `taxonomy`, and `comments`.

```tex
% Default order
\AIDorder{preamble, tools, taxonomy, comments}
```

### Inserting Text

You can inject custom text before or after specific sections:

```tex
\AIDpreTools{Text before the tools list.}
\AIDpostTools{Text after the tools list.}

\AIDpreTaxonomy{Text before the checklist.}
\AIDpostTaxonomy{Text after the checklist.}

\AIDpreComments{Text before comments.}
\AIDpostComments{Text after comments.}
```

### Custom Strings and Preamble

To modify specific strings or the main preamble text:

```tex
% Modify internal strings
\AIDstrings{
  tools_used = {AI Tools employed:},
  none_used  = {No AI tools used.}
}

% Set the main preamble (using placeholders <AUTHOR>, <DECLARES>, <ACKNOWLEDGES>)
\AIDpreamble{The authors (<AUTHOR>) <DECLARES> the use of...}
```

---

## Rendering the declaration

Place the rendering command where you want the disclosure to appear:

```tex
\AIDrenderDeclaration[<columns>]{<authors>}
\AIDrenderDeclaration*[<columns>]{<authors>}
```

* Starred form omits the section heading
* `<columns>` defaults to `3`
* `<authors>` is a comma-separated list of authors

---

## Minimal example

```tex
\AIDactivate{c:idea}
\AIDactivate{c:rq}
\AIDactivate{l:srch}
\AIDactivate{l:sum}
\AIDactivate{s:auto}
\AIDactivate{d:anl}
\AIDactivate{w:sum}
\AIDactivate{w:poly}

\AIDtoolsUsed{ChatGPT-4o, Gemini 1.5 Pro, GitHub Copilot}

\begin{AIDcomment}
AI was used for refining code structure in Section 4.
\end{AIDcomment}

\AIDrenderDeclaration[2]{Mary Doe, John Doe, Jane Doe}
```

---

## Example output (summary)

The rendered declaration includes:

* A responsibility statement naming the authors
* A checklist of delegated tasks organized by taxonomy category
* A declaration of Generative AI tools used (or an explicit statement that none were declared)
* Optional additional comments

See **[aidisclose-doc.pdf](https://www.google.com/search?q=aidisclose-doc.pdf)** for the full rendered example.

<img height="400" alt="example-pg-1" src=".resources/example-pg1.svg" />
<img height="400" alt="example-pg-1" src=".resources/example-pg2.svg" />

---

## Documentation

* **[aidisclose-doc.pdf](https://mirrors.ctan.org/macros/latex/contrib/stocksize/stocksize-doc.pdf)** — complete documentation and examples
* [`aidisclose-doc.tex`](https://mirrors.ctan.org/macros/latex/contrib/stocksize/stocksize-doc.tex) — documentation source
* https://ctan.org/pkg/aidisclose

---

## License

This package is distributed under the **LaTeX Project Public License (LPPL) 1.3c** or later.

---

Copyright © 2025-26 João M. Lourenço.

Crafted with 🧡 for reproducible scientific writing.
