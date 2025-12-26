# aidisclose – Generative AI disclosure checklist and statements

[![CTAN](https://img.shields.io/ctan/v/aidisclose)](https://ctan.org/pkg/aidisclose)
[![Version](https://img.shields.io/badge/version-1.4.0-blue)](https://github.com/joaomlourenco/aidisclose)
[![Date](https://img.shields.io/badge/date-2025--12--25-orange)](https://github.com/joaomlourenco/aidisclose)
[![License: LPPL 1.3c](https://img.shields.io/badge/license-LPPL%201.3c-blue)](https://www.latex-project.org/lppl/lppl-1-3c/)
[![LaTeX](https://img.shields.io/badge/LaTeX-LaTeX2e%202020%2F10%2F01%2B-brightgreen)](https://www.latex-project.org/)

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Requirements](#requirements)
- [Quick Start](#quick-start)
- [Documentation](#documentation)
- [Taxonomy Reference](#taxonomy-reference)
- [Public Interface](#public-interface)
  - [`\GAIrenderDeclaration`](#gairenderdeclaration)
  - [`\GAIdiscloseTitle`](#gaidisclosetitle)
  - [`\GAIactivate`](#gaiactivate)
  - [`\GAItoolsUsed`](#gaitoolsused)
  - [`GAIcomment` environments](#gaicomment-environments)
  - [`\GAIsetChecklistFontSize`](#gaisetchecklistfontsize)
  - [`\GAIsetCheckmarkSymbol`](#gaisetcheckmarksymbol)
- [Dependencies](#dependencies)
- [Contributing](#contributing)
- [Citation](#citation)
- [Author](#author)
- [License](#license)
- [Disclaimer](#disclaimer)

## Overview

**aidisclose** is a LaTeX package that helps authors produce clear, structured disclosures of how **Generative Artificial Intelligence (GAI)** tools were used when preparing manuscripts.

The package implements the **GAIDeT (Generative AI Delegation Taxonomy)** proposed by Suchikova et al. (2025), providing a standardized framework for transparent AI disclosure in academic and professional documents.

GAI tools are not listed as authors and do not bear responsibility for the final outcomes.

## Features

- **Taxonomy-based checklist**: Built on the GAIDeT (Generative AI Delegation Taxonomy) framework
- **Responsibility statements**: Automatically generates declarations attributing final responsibility to human authors
- **Flexible customization**: Customize titles, fonts, checkbox symbols, and column layouts
- **Multiple comment types**: Add numbered or unnumbered additional comments
- **Standard compliance**: Helps meet institutional and publisher AI disclosure requirements
- **Easy integration**: Single command renders the complete disclosure section
- **Optional title rendering**: Skip section title generation when integrating into custom document structures

## Installation

### Via CTAN

```bash
tlmgr install aidisclose
```

### Manual installation

Place `aidisclose.sty` either next to your document or in a local `texmf` tree.

## Requirements

- LaTeX2e (2020/10/01 or later)
- Standard packages: `expl3`, `xparse`, `amssymb`, `multicol`, `enumitem`, `relsize`
- No special fonts required
- Platform independent

## Quick Start

Here's a minimal example to get started:

```tex
\usepackage{aidisclose}

% ----------------------------------------------------------------------
% Configuration 

% Optional: customize the title (short, long, and optional sectioning command)
\GAIdiscloseTitle[AI disclosure]{Generative AI Disclosure Statement}[section]

% Select checklist items from the taxonomy
% The full list is available in the aidisclose-doc.pdf file
\GAIactivate{c:idea}
\GAIactivate{l:search}
\GAIactivate{w:proof}

% Declare tools used
\GAItoolsUsed{ChatGPT-4, Claude~3}

% Optional: add comments
% non-starred comments are numbered sequentially
% starred comments are not numbered
\begin{GAIcomment}
GAI tools were used for language editing only.
\end{GAIcomment}

\begin{GAIcomment*}
No GAI tools were used for data analysis.
\end{GAIcomment*}


% ----------------------------------------------------------------------
% Declaration rendering 

% Render the disclosure (optional argument = number of columns, default 3)
\GAIrenderDeclaration[3]{Alice Smith, Bob Jones}
```

See [aidisclose-doc.pdf](aidisclose-doc.pdf) for complete output examples.

## Documentation

**Full documentation** is available in:

- **PDF**: [aidisclose-doc.pdf](aidisclose-doc.pdf) – Complete manual with examples and full taxonomy reference
- **Source**: [aidisclose-doc.tex](aidisclose-doc.tex)
- **CTAN**: [https://ctan.org/pkg/aidisclose](https://ctan.org/pkg/aidisclose)

The documentation includes:

- Complete list of all taxonomy identifiers (50+ task categories)
- Advanced customization options
- Multiple usage examples
- Best practices for AI disclosure

## Taxonomy Reference

The package supports the complete GAIDeT taxonomy with 50+ task identifiers across 8 categories.  The list below is incomplete and for illustrative purposes.
***Full list**: See [aidisclose-doc.pdf](aidisclose-doc.pdf), Section 3.

| Category                 | Example Keys                          | Tasks                                                        |
| ------------------------ | ------------------------------------- | ------------------------------------------------------------ |
| **Conceptualization**    | `c:idea`, `c:objective`, `c:rq`       | Idea generation, research objectives, hypothesis formulation |
| **Literature Review**    | `l:search`, `l:write`, `l:gaps`       | Literature search, writing, gap identification               |
| **Methodology**          | `m:design`, `m:protocols`             | Research design, protocol development                        |
| **Software Development** | `s:codegen`, `s:opt`, `s:auto`        | Code generation, optimization, automation                    |
| **Data Management**      | `d:collect`, `d:analyze`, `d:viz`     | Collection, analysis, visualization                          |
| **Writing & Editing**    | `w:textgen`, `w:proof`, `w:translate` | Text generation, proofreading, translation                   |
| **Ethics Review**        | `e:bias`, `e:risk`, `e:compliance`    | Bias analysis, risk assessment, compliance                   |
| **Supervision**          | `sup:qa`, `sup:limits`                | Quality assessment, limitation identification                |

## Public Interface

### `\GAIrenderDeclaration`

Render the full disclosure block (title, statement, checklist, tools, comments).

```tex
\GAIrenderDeclaration[<cols>]{<authors>}
\GAIrenderDeclaration*[<cols>]{<authors>}
```

- `<cols>`: number of columns used for the checklist (default: `3`)
- `<authors>`: comma-separated author list
- **Starred form** (`\GAIrenderDeclaration*`): renders the disclosure **without** the automatic section title, useful when you want to manage the heading entirely yourself.

Examples:

```tex
% With title (uses the configured sectioning command and title)
\GAIrenderDeclaration{Jane Doe}

% With title and two columns
\GAIrenderDeclaration[2]{Jane Doe, John Doe, Mary Doe}

% Without title (starred form) 
\section*{AI Disclosure}
 \GAIrenderDeclaration*{Jane Doe, John Doe}
```

### `\GAIdiscloseTitle`

Set the title used when rendering the disclosure.

```tex
\GAIdiscloseTitle[<short>]{<long>}[<sectioning cmd>]
```

- If `<short>` is omitted, it defaults to `<long>`.
- If `<sectioning cmd>` is omitted/blank, the package picks `\chapter` when available, otherwise `\section`.
- **Special value**: Use `none` as the sectioning command to skip automatic title generation entirely.

Examples:

```tex
\GAIdiscloseTitle{Disclosure of Delegation to Generative AI}
\GAIdiscloseTitle[Disclosure]{Disclosure of Delegation to Generative Artificial Intelligence}[\section*]

% Skip automatic title generation (useful when embedding in custom sections)
\GAIdiscloseTitle{My Custom Title}[none]

% Retrieve stored titles for manual use
\GAIdiscloseTitleLong
\GAIdiscloseTitleShort
```

### `\GAIactivate`

Activate a checklist item by its taxonomy identifier (e.g., `c:idea`, `l:search`).

```tex
\GAIactivate{<id>}
```

Example:

```tex
\GAIactivate{c:idea}
\GAIactivate{w:proof}
```

### `\GAItoolsUsed`

Declare the tools used (comma-separated list). This text is rendered as a sentence in the disclosure.

```tex
\GAItoolsUsed{<tool list>}
```

Example:

```tex
\GAItoolsUsed{ChatGPT-5.2, Gemini 3 Pro}
```

### `GAIcomment` environments

Add comments to the disclosure:

- `GAIcomment` is **numbered** and increments an internal counter.
- `GAIcomment*` is **unnumbered** and does not increment the counter.

```tex
\begin{GAIcomment}
•••
\end{GAIcomment}

\begin{GAIcomment*}
•••
\end{GAIcomment*}
```

### `\GAIsetChecklistFontSize`

Change the font size used when rendering the checklist (optional):

```tex
\GAIsetChecklistFontSize{\small}
```

(The default in the package is `\smaller`, which means slightly smaller than the main text.)

### `\GAIsetCheckmarkSymbol`

Change the symbol used inside the framed checkbox (optional):

```tex
\GAIsetCheckmarkSymbol{\checkmark}
```

(The default is `√`)
This also updates the internal width so checked/unchecked boxes align.

## Dependencies

`aidisclose` uses only standard LaTeX packages:

- `expl3` — for package/commands implementation;
- `xparse` — for package/commands implementation;
- `amssymb` — for the \checkmark (√) symbol;
- `multicol` — for printing the Checklist in multiple columns;
- `enumitem` — for configuring the Checklist layout;
- `relsize` — for setting font sizes relative to current size (e.g., `\smaller`).

## Contributing

Contributions are welcome! Please feel free to submit issues, feature requests, or pull requests on [GitHub](https://github.com/joaomlourenco/aidisclose).

If you find bugs or have suggestions for improvements, please open an issue with:

- A clear description of the problem;
- Minimal working example (MWE) demonstrating the issue;
- Expected vs. actual behavior.

## Citation

If you use this package in your research, please cite both the package and the GAIDeT taxonomy:

**Package:**

```bibtex
@software{Lourenco:2025:aidisclose,
  author = {Lourenço, João M.},
  title = {aidisclose: Generative AI disclosure checklist and statements},
  year = {2025},
  url = {https://ctan.org/pkg/aidisclose},
  version = {1.4.0}
}
```

**GAIDeT Taxonomy:**

```bibtex
@article{Suchikova:2025:GAIDeT,
  title = {{GAIDeT (Generative AI Delegation Taxonomy)}: A Taxonomy for Humans to Delegate Tasks to Generative Artificial Intelligence in Scientific Research and Publishing},
  author = {Yana Suchikova and Natalia Tsybuliak and Jaime A. Teixeira da Silva and Serhii Nazarovets},
  year = {2025},
  journal = {Accountability in Research},
  pages = {1--27},
  doi = {10.1080/08989621.2025.2544331}
}
```

## Author

**João M. Lourenço**

- GitHub: [@joaomlourenco](https://github.com/joaomlourenco)
- CTAN: [João M. Lourenço](https://ctan.org/author/lourenco-j)

## License

This package is distributed under the **LaTeX Project Public License (LPPL) 1.3c** or later.

See: [https://www.latex-project.org/lppl/lppl-1-3c/](https://www.latex-project.org/lppl/lppl-1-3c/)

## Disclaimer

This package provides **formatting utilities only** and does not enforce any specific AI usage policy. Authors remain fully responsible for:

- The accuracy and integrity of manuscript content
- Compliance with institutional, publisher, and legal requirements
- Appropriate disclosure of AI tool usage

Always consult your institution's or publisher's specific AI disclosure policies.

---

Copyright © 2025 João M. Lourenço.  
Crafted with 💙 for reproducible scientific writing.