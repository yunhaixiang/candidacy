# Candidacy LaTeX templates

- `presentation/presentation.tex`: a 16:9 Beamer presentation.
- `writeup/writeup.tex`: an article with sections, numbered theorem environments, and cross-references.
- `writeup/references.bib`: the writeup's BibTeX bibliography, using the `alpha` style.
- `source/`: existing reference material.

The writeup is ready for drafting, with automatic paragraph numbering, formatting,
and math environments configured. The presentation still contains editable
metadata and gray instructional placeholders. Both documents can be uploaded to Overleaf; include `references.bib`
alongside the writeup source.

Build from the candidacy directory with a TeX distribution containing `latexmk`:

```sh
latexmk -cd -pdf -outdir=build presentation/presentation.tex
latexmk -cd -pdf -outdir=build writeup/writeup.tex
```

The resulting PDFs are `presentation/build/presentation.pdf` and
`writeup/build/writeup.pdf`. Re-running the commands updates cross-references.

Both templates define common notation (`\C`, `\PP`, `\GL`, `\End`, `\rig`).
The presentation uses Beamer's theorem environments. The writeup additionally
provides proposition, lemma, corollary, definition, example, question, remark, and custom
environments; use `\label{...}` and `\cref{...}` for cross-references.

### Writeup numbering and references

Use `\section{...}` and `\subsection{...}` for the hierarchy. All numbered math
environments and ordinary prose paragraphs share a single counter, reset
at each subsection, with the form `section.subsection.index`.

```tex
\begin{theorem}[Optional name]\label{thm:sample}
  The statement goes here.
\end{theorem}

Now this is content.

This blank-line-separated paragraph receives the next number automatically.
```

The headings look like `2.1.3 Theorem. (Optional name)` and `2.1.4.` respectively.
Omit the theorem's optional argument to omit its parenthesized name.
Ordinary top-level prose is numbered after a source paragraph break (a blank
line or an explicit `\par`), after the first section. Text immediately following
a table, list, theorem, or display without a blank line continues the preceding
block and receives no new paragraph number. Headings, the contents, footnotes, and
environment bodies (including theorems, proofs, lists, and references) do not
receive extra paragraph numbers. Text continuing after a displayed equation is
part of the same paragraph unless separated by a blank line.

Source paragraph breaks also add the same vertical separation (`\topsep`) as
the theorem-style environments. Adjacent block spacings merge rather than
double; unnumbered continuations after tables do not gain this extra gap.

`\paragraph{A title}` still adds a numbered bold run-in title, without duplicating
the automatic number. `\paragraph*{A title}` gives an unnumbered titled paragraph.
For an ordinary paragraph label, put `\parlabel{par:sample}` before its first word;
this starts the paragraph before recording its number. With explicit
`\paragraph{}`, `\label` immediately after the command still works.
Wrap prose in `\begin{unnumberedparagraphs} ... \end{unnumberedparagraphs}` to
opt out of automatic numbering for a passage.
Place numbered content inside a subsection to avoid a subsection component of zero.

For a freely chosen heading, use the `custom` environment's required title:

```tex
\begin{custom}{A Simple Follow-up to \Cref{thm:main}}
  Content goes here.
\end{custom}
```

This displays the shared number followed by your title, with no literal
"Custom" heading. `\Cref{thm:main}` produces a linked theorem name and number;
put `\label{thm:main}` in the theorem being referenced. To add parenthesized
information, use `\begin{custom}[Optional Info]{Your heading}`. A `\label`
inside the custom environment supports `\ref` and `\cref` (called an "item").

Add bibliography entries to `writeup/references.bib` and use `\cite{Katz1996}`.
The `alpha` style produces labels such as `[Kat96]`; `latexmk` runs BibTeX and
the necessary LaTeX passes automatically. Uncomment `\bibliography{references}`
in the writeup when you add your first citation; the bibliography is currently
disabled so the empty draft has no references section.

In Beamer, use the
`fragile` frame option for slides containing `tikzcd` diagrams or verbatim code.
