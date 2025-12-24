# GAIDeT — Utilities for a Generative AI disclosure checklist and statements

[![CTAN](https://img.shields.io/ctan/v/GAIDeT)](https://ctan.org/pkg/gaidet)
[![License: LPPL 1.3c](https://img.shields.io/badge/license-LPPL%201.3c-blue)](https://www.latex-project.org/lppl/lppl-1-3c/)
[![LaTeX](https://img.shields.io/badge/LaTeX-2020%2B-brightgreen)](https://www.latex-project.org/)

---

## About

* **Package:** GAIDeT — Utilities for Generative AI disclosure checklist and statements
* **Copyright:** 2025 © João M. Lourenço <joao.lourenco@fct.unl.pt>
* **CTAN:** https://ctan.org/pkg/GAIDeT
* **Repository:** https://github.com/joaomlourenco/GAIDeT
* **License:** The LaTeX Project Public License 1.3c

---

## Description

**GAIDeT** is a LaTeX package providing a standardized, transparent mechanism for declaring the use of Generative Artificial Intelligence (GAI) tools in academic, technical, and professional documents.

The package is designed to support emerging ethical, institutional, and publisher requirements concerning AI-assisted content creation. It implements the *GAIDeT (Generative AI Delegation Taxonomy*, as proposed in
Suchikova, Y., Tsybuliak, N., Teixeira da Silva, J. A., \& Nazarovets, S. (2025). GAIDeT (Generative AI Delegation Taxonomy): A taxonomy for humans to delegate tasks to generative artificial intelligence in scientific research and publishing. *Accountability in Research*, 1–27. https://doi.org/10.1080/08989621.2025.2544331

GAIDeT (Generative AI Declaration of Transparency) enables authors to:

- Declare whether and how Generative AI tools were used;
- Explicitly state human responsibility for the final manuscript;
- Report GAI tools employed during document preparation; and
- Produce a consistent, reusable disclosure block.

Generative AI tools are never listed as authors and bear no responsibility for the final content.

---

## Installation

### CTAN

The recommended installation method is via CTAN:

```
tlmgr install gaidet
```

### Manual Installation

Alternatively, place the file:

```
GAIDeT.sty
```

in the same directory as your document or in a local `texmf` tree.

---

## Usage

Load the package in the preamble:

```tex
\usepackage{GAIDeT}
```

### Setting the Declaration Title

```tex
\GAIDeTtitle{Generative AI Declaration of Transparency}
```

With a short title:

```tex
\GAIDeTtitle[GAI DeT]
           {Generative AI Declaration of Transparency}
```

Stored titles can be reused later:

```tex
\GAIDeTtitleLong
\GAIDeTtitleShort
```

---

### Rendering the Declaration

```tex
\RenderGAIDeTDeclaration{Alice Smith, Bob Jones}
```

Single-author case:

```tex
\RenderGAIDeTDeclaration{Alice Smith}
```

Optional number of columns while printing the Check Lisk.  Defaults to 3 columns.

```tex
\RenderGAIDeTDeclaration[1]{Alice Smith, Bob Jones}
```

---

### Declaring GAI Tools Used

```tex
\GAItoolsUsed{ChatGPT-5.2, Gemini 3 Pro}
```

---

### Activating Checklist Items

```tex
\Activate{c:idea}
\Activate{l:search}
```

Activated items are reflected automatically in the rendered declaration.  See the documentation for the full list of Checklist Items.

---

## Dependencies

GAIDeT relies on standard LaTeX packages only:

- `expl3`
- `xparse`
- `enumitem`
- `relsize`

All dependencies are included in standard LaTeX distributions.

---

## Design Philosophy

- Minimal intrusion into document structure
- Explicit human responsibility
- Transparency rather than enforcement

The package is class-agnostic and compatible with common LaTeX workflows.

---

## Documentation

The full user manual is provided in:

```
GAIDeT-doc.tex
```

---

## License

This work is distributed under the **LaTeX Project Public License (LPPL) 1.3c** or later.

---

## Disclaimer

This package does not enforce compliance with any specific policy.  
Authors remain fully responsible for their manuscripts and for adherence to institutional, publisher, or legal requirements regarding the use of Generative AI tools.

---

## CTAN Maintenance

This package is intended for submission and maintenance on CTAN.
