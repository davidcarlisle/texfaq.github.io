---
title: Typesetting epigraphs
category: formatting
tags: layout
permalink: /FAQ-epigraph
---

Epigraphs are those neat quotations that authors put at the start of
chapters (or even at the end of chapters: Knuth puts things at the
ends of chapters of the TeXbook).

Typesetting them is a bit of a fiddle, but not impossible to do for
yourself.  Fortunately, there are two packages that do the job, to
some extent; there are also facilities in the two "big" classes
([`memoir`](https://ctan.org/pkg/memoir) and [`koma-script`](https://ctan.org/pkg/koma-script).

The [`epigraph`](https://ctan.org/pkg/epigraph) package defines an `\epigraph` command, for
creating a single 
epigraph (as at the top of a chapter):
```latex
\chapter{The Social Life of Rabbits}
\epigraph{Oh!  My ears and whiskers!}%
         {Lewis Carroll}
```
and an epigraphs environment, for entering more than one epigraph
consecutively, in a sort of list introduced by `\qitem` commands:
```latex
\begin{epigraphs}
\qitem{What I tell you three times is true}%
      {Lewis Carroll}
\qitem{Oh listen do, I'm telling you!}%
      {A.A. Milne}
\end{epigraphs}
```
The `\epigraphhead` command enables you to place your epigraph
_above_ a chapter header:
<!-- {% raw %} -->
```latex
\setlength{\unitlength}{1pt}
...
\chapter{The Social Life of Rabbits}
\epigraphhead[<distance>]{%
  \epigraph{Oh!  My ears and whiskers!}%
           {Lewis Carroll}%
}
```
<!-- {% endraw %} -->
The &lsaquo;_distance_&rsaquo; says how far above the chapter heading the
epigraph is to go; it's expressed in terms of the `\unitlength`
that's used in the `picture` environment; the package's
author recommends `70pt`.

The package also offers various tricks for adjusting the layout of
chapter header (necessary if you've found a hugely long quotation for
an `\epigraphhead`), for patching the bibliography, for patching
`\part` pages, and so on.  (Some of these suggested patches lead you
through writing your own package&hellip;)

The [`quotchap`](https://ctan.org/pkg/quotchap) package redefines chapter headings (in a
moderately striking way), and provides an environment
`savequotes` in which you can provide one (or more)
quotations to use as epigraphs.  The facilities seem not as flexible
as those of [`epigraph`](https://ctan.org/pkg/epigraph), but it's probably easier to use.

The [`memoir`](https://ctan.org/pkg/memoir) class offers all the facilities of the
[`epigraph`](https://ctan.org/pkg/epigraph) package.  The [`Koma-script`](https://ctan.org/pkg/Koma-script) classes have
commands `\setchapterpreamble` and `\dictum` to provide these
facilities.

