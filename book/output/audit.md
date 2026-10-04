# Retypesetting fidelity audit

## 2026-10-02 — Introduction and targeted discrepancies

This is a **partial audit**, not certification that all nine chapters match
the source. The original page images were read directly; no OCR was used.
The retypesetting skill's conventions govern notation, hyperlinks, and
typography; the original text and supplied erratum govern content.

### Source and recovery

- Original: `../source/Katz.pdf`, with page images in `../source/img/`.
- Erratum: `../source/erratum.png`.
- Pre-edit backup: `../backups/before-fidelity-fixes-2026-10-02.tar.gz`.
  The archive contains the previous chapter sources, main source,
  bibliography, compiled PDF, and navigation index. Archive paths start
  at `book/`; extract into a separate directory when comparing versions.

### Corrections made

- Replaced the paraphrased and abridged introduction with a transcription
  of source PDF pages 4–12. Restored the original sequence of paragraphs,
  the scalar-equation/system distinction for accessory parameters, the
  doubling discussion, recognition/construction problems, apparent
  singularities, chapter overview, historical open questions, and
  acknowledgments. Removed invented assertions, notably that a local
  system determines an equation “up to accessory parameters.”
- Retained the supplied correction to the hypergeometric equation's
  coefficient: `c-(a+b+1)\lambda`.
- Restored source list labels in §2.5.3: translations are (3), Lang-torsor
  twists are (4). The explicit labels (2a) and (2b) had not advanced the
  automatic list counter.
- Restored Corollary 2.8.5's outer labels (1)–(5) and inner labels (a), (b)
  (source pages 58–59).
- Restored Lemma 3.1.7's labels (1)–(3), rather than (2a)–(2c)
  (source pages 95–96).
- Restored Lemma 3.2.3's nested labels (2a), (2b)
  (source pages 99–100).
- Restored Lemma 3.3.1's labels (1), (2), and Theorem 3.3.3's outer
  labels (1)–(3) and nested labels (1a)–(1b), (2a)–(2d)
  (source pages 100–102).
- Corrected the Whittaker–Watson citation's visible handle from WWW to WW,
  matching source pages 8 and 219; retained the internal bibliography key.
- Corrected the introduction's running header from “Contents” to
  “Introduction”; enabled first-paragraph indentation after headings.
  Preserved the existing book layout rather than reproducing the scan's
  typewriter typography or page breaks.
- Updated obsolete `localsystem/source/` paths in the navigation index.
  Corrected the chapter ranges to Chapter 2: 35–90, Chapter 3: 91–110,
  Chapter 4: 111–119 (and Chapter 4's local page range to 1–9).

### Supplied erratum checked

All seven corrections were already represented in the editable source
before this audit and were preserved:

1. Introduction: corrected hypergeometric differential equation.
2. Remarks 2.10.4: “Here is a slightly variant…” wording.
3. Corollary 2.13.3: translated Kummer object
   `K=\mathcal L_{\chi(x-1)}[1]`.
4. Lemma 3.3.1 proof: references to Lemma 2.10.2 and Theorem 2.10.8.
5. Lemma 4.3.8: `j:X-D\to X`.
6. Lemma 8.2.2 proof: “By proper base change.”
7. §8.5.1: base factor involving `\chi_{2,i}(X_2-T_i)` and the
   character convention `\chi_{a,i}=\chi^{e(a,i)}`.

### Fidelity notes and remaining work

- Historical claims that problems “remain open” have not been updated.
  They are Katz's text, not assertions about the state of research in 2026.
- Source wording such as “the most local systems,” “Is this this,” and
  “any irreducible D-module” in the speculative paragraph is retained.
  These are not new transcription mistakes. No unlisted mathematical
  corrections have been silently imposed on Katz's original.
- Parenthetical prose brackets were normalized to parentheses under the
  style guide, including removal of the stray closing parenthesis after
  the introduction's formula `2-[(2-m)n^2+mn]`.
- The rest of Chapters 1–9 still requires a systematic page-by-page
  fidelity audit. The targeted checks above do not certify surrounding
  statements, proofs, or other enumeration labels.

### Build and visual verification

Build from this directory with:

```sh
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
```

- Final rebuild succeeded: `main.pdf`, 175 pages, with no LaTeX warnings,
  undefined references/citations, overfull boxes, or Biber warnings/errors
  in the final logs.
- Visually inspected all six rendered introduction pages and the affected
  lists on PDF pages 36–37, 45–46, 75, and 79–81. Re-rendered and verified
  the corrected introduction header and section citation.
- The multi-file project was built with its existing latexmk/Biber setup;
  the standalone editor's single-file compiler was not used.
