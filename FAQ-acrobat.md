---
title: Making PDF documents from (La)TeX
category: usage
permalink: /FAQ-acrobat
---

There are three general routes to PDF output: Adobe's original
"distillation" route (via PostScript output), direct conversion of a
DVI file, and the use of a direct TeX-like PDF
generator such as [pdfTeX](FAQ-pdftex).

For simple documents (with no hyper-references), you can either
  

-  process the document in the normal way, produce PostScript
    output and distill it;
-  (on a Windows or Macintosh machine with appropriate
    tools installed) pass the output through a PDFwriter in place
    of a printer driver.  This route is only appropriate for simple
    documents: PDF writers cannot create hyperlinks;
-  process the document with "vanilla" LaTeX and generate PDF
    direct from the DVI using `dvipdfm`/`dvipdfmx`; or 
-  process the document direct to PDF with pdfTeX,
    [LuaTeX](FAQ-luatex), or [XeTeX](FAQ-xetex).

To translate all the LaTeX cross-referencing into Acrobat
links, you need a LaTeX package to redefine
the internal commands.  There are two of these for LaTeX, both
capable of conforming to the
[HyperTeX specification](FAQ-hyper):
Heiko Oberdiek's [`hyperref`](https://ctan.org/pkg/hyperref), and Michael Mehlich's
[`hyper`](https://ctan.org/pkg/hyper).  (In practice, almost everyone uses
[`hyperref`](https://ctan.org/pkg/hyperref); [`hyper`](https://ctan.org/pkg/hyper) hasn't been updated since 2000.)
[`Hyperref`](https://ctan.org/pkg/Hyperref) can often determine how it should generate
hypertext from its environment, but there is a wide set of
configuration options you can give via `\usepackage`.  The package
can operate using pdfTeX primitives, the hyperTeX
`\special`s, or DVI driver-specific `\special` commands.
Both `dvips` and Y&Y's `DVIPSONE` can
translate the DVI with these `\special` commands into
PostScript acceptable to Distiller, and
`dvipdfm` and `dvipdfmx` have `\special` commands of
their own.

If you use Plain TeX, the [Eplain macros](FAQ-eplain) can
help you create PDF documents with hyper-references.
It can operate using pdfTeX primitives, or `\special` commands
for the `dvipdfm`/`dvipdfmx` DVI drivers.

While there is no free implementation of all of `Adobe`
`Distiller`s
functionality, any but the implausibly old versions of
[`ghostscript`](https://www.ghostscript.com/)
provide pretty reliable distillation (but beware of the problems with
[`dvips` output for distillation](FAQ-dvips-pdf)).

For viewing (and printing) the resulting files, Adobe's
_Acrobat Reader_ is available for a fair range of
platforms; for those for which Adobe's reader is unavailable, remotely
current versions of [`ghostscript`](https://www.ghostscript.com/)
combined with `gv` or
[`gsview`](http://www.ghostgum.com.au/) can display and
print PDF files, as can `xpdf`.

In some circumstances, a
[`ghostscript`](https://www.ghostscript.com/)-based viewer
application is actually preferable to Acrobat Reader.  For example, on
Windows Acrobat Reader locks the `pdf` file it's displaying: this
makes the traditional (and highly effective) (La)TeX development
cycle of "Edit&rarr;Process&rarr;Preview" become
rather clumsy&nbsp;&mdash; [`gsview`](http://www.ghostgum.com.au/)
doesn't make the same mistake.

