---
title: Getting the right paper geometry from (La)TeX
category: formatting
tags: layout
permalink: /FAQ-papergeom
---

If your output is the wrong size, and you've checked that it's not due
to the [ministrations of Adobe `Reader`](FAQ-acroantics),
the problem is probably that your (La)TeX system is producing output
that specifies the wrong paper size.  Paper sizes can be a pain:
they're a forgotten backwater&nbsp;&mdash; Knuth seems not to have considered
paper size as something the TeX engine needs to know about.  As a
result, there is no DVI command to specify the paper on which
the document should be printed, which has led a dichotomy where macros
shape the text according to the needs of the author's chosen paper
size, and device drivers" choice happens independently of the macros"
ideas.

In practice, one usually finds that macro packages (such as Plain TeX and
LaTeX) assume American "letter" paper size, by default; and since
most distributions nowadays originate in Europe, the drivers usually
default to ISO "A4" paper size.

This is (of course) pretty unsatisfactory.  Users may select a
different paper size for their document (current LaTeX offers a
range of sizes as options in the standard classes), pretty easily.
Nevertheless, the user also has to be sure that each time
`xdvi`, `dvips` (or whatever) runs, it uses the
paper size the document was designed for.

The default paper size for DVI drivers may be changed by a
distribution management command (`texconfig` for TeX&nbsp;Live,
the `Options` application for MiKTeX), but this still
doesn't provide for people using the "wrong" sort of paper for some
reason.

A different issue arises for users of pdfTeX&nbsp;&mdash; the
PDF format _does_ have the means of expressing paper size
and pdfTeX has system variables `\pdfpagewidth` and
`\pdfpageheight`, that are written into the output PDF file.
Unfortunately, most of the core software predates pdfTeX, so not even
pdfLaTeX sets the correct values into those variables, to match the
paper size specified in a `\documentclass` option.

The DVI drivers `dvips`, `dvipdfm` and its
extensions (`dvipdfmx` and `xdvipdfmx`) define
`\special` commands for the document to specify its own paper size;
so in those cases, as when pdfTeX is being used, the
paper size can be programmed by the document.  Users who wish to, may
of course consult the manuals of the various programs to write the
necessary code.

The [`geometry`](https://ctan.org/pkg/geometry) and [`zwpagelayout`](https://ctan.org/pkg/zwpagelayout) packages (whose main
business includes defining
typeset page areas), also takes notice the size of the paper that the
document is going to be printed on, and can issue the commands
necessary to ensure the correct size of paper is used.  If
[`geometry`](https://ctan.org/pkg/geometry) is used when a document is being processed by
pdfLaTeX, it can set the necessary dimensions "in the output".
If the document is being processed by LaTeX on a TeX or &epsilon;-TeX
engine, there are package options which instruct [`geometry`](https://ctan.org/pkg/geometry)
which `\special` commands to use.  (Note that the options are
ignored if you are using pdfLaTeX.)

So, one resolution of the problem, when you are using LaTeX, is to add
```latex
\usepackage[processor-option,...]{geometry}
```
Where `processor-option` tells the package what will produce
your (PostScript or PDF output&nbsp;&mdash; [`geometry`](https://ctan.org/pkg/geometry) knows about
`dvips` and `dvipdfm` (`dvipdfm` also
serves for the extension `dvipdfmx` and
`xdvipdfmx`).

If you're using pdfLaTeX or XeTeX, load with
```latex
\usepackage[program-option,...]{geometry}
```
where `program-option` is `pdftex`,
`xetex`.

The alternative, [`zwpagelayout`](https://ctan.org/pkg/zwpagelayout) requires a `driver`
option:
```latex
\usepackage[driver=value,...]{zwpagelayout}
```
(permissible &lsaquo;_values_&rsaquo; are `pdftex`, `xetex`
and `dvips`; the default value is `unknown`).

Needless to say, both the "big" classes ([`koma-script`](https://ctan.org/pkg/koma-script) and
[`memoir`](https://ctan.org/pkg/memoir)) provide their own ways to get the paper size
"right".

The [`typearea`](https://ctan.org/pkg/typearea) package is the [`Koma-script`](https://ctan.org/pkg/Koma-script)
distribution's way of providing page layout functionality.  Load it
with the `pagesize` option and it will ensure the correct
paper is selected, for PDF output from pdfLaTeX, and for
PostScript output from LaTeX via `dvips`.

[`Memoir`](https://ctan.org/pkg/Memoir) has the standard classes' paper-size selections
(`a4paper`, `letterpaper` and so on), but also
permits the user to choose an arbitrary paper size, by setting the
length registers `\stockheight` and `\stockwidth`.  The commands
`\fixdvipslayout` (for LaTeX processing), and `\fixpdflayout`
(for pdfLaTeX processing) then instruct the processor to produce
output that specifies the necessary paper size.

