---
title: Parallel setting of text
category: formatting
tags: layout
permalink: /FAQ-parallel
---

It's commonly necessary to present text in two languages "together" on a
page, or on a two-page spread.  For this to be satisfactory, one usually
needs some sort of alignment between the two texts.

The [`parallel`](https://ctan.org/pkg/parallel) package satisfies the need, permitting
typesetting in two columns (not necessarily of the same width) on one
page, or on the two opposing pages of a two-page spread.  Use can be
as simple as
```latex
\usepackage{parallel}
...
\begin{Parallel}{<left-width>}{<right-width}
  \ParallelLText{left-text}
  \ParallelRText{right-text}
  \ParallelPar
  ...
\end{Parallel}
```
[`Parallel`](https://ctan.org/pkg/Parallel) can get terribly confused with color changes, in
pdfTeX; the indefatigable Heiko Oberdiek has a patch for this
issue&nbsp;&mdash; the [`pdfcolparallel`](https://ctan.org/pkg/pdfcolparallel) package, which maintains
separate color stacks for the columns.

The [`parcolumns`](https://ctan.org/pkg/parcolumns) package can (in principle) deal with any
number of columns: the documentation shows its use with three
columns.  Usage is rather similar to that of [`parallel`](https://ctan.org/pkg/parallel),
though there is of course a "number of columns to specify":
```latex
\usepackage{parcolumns}
...
\begin{parcolumns}[<options>]{3}
  \colchunk{<Column 1 text>}
  \colchunk{<Column 2 text>}
  \colchunk{<Column 3 text>}
  \colplacechunks
  ...
\end{parcolumns}
```
The &lsaquo;_options_&rsaquo; can specify the widths of the columns, whether to
place rules between the columns, whether to set the columns sloppy,
etc.  Again, there are issues with colors, which are addressed by the
[`pdfcolparcolumns`](https://ctan.org/pkg/pdfcolparcolumns) package.

The [`ledpar`](https://ctan.org/pkg/ledpar) package is distributed with (and integrated with)
the [`ledmac`](https://ctan.org/pkg/ledmac) package.  It provides parallel
setting carefully integrated with the needs of a scholarly text,
permitting translation, or notes, or both, to be set in parallel with
the "base" text of the document.

