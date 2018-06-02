---
title: Putting bibliography entries in text
category: bibliographies
tags: citations
permalink: /FAQ-bibinline
date: 2014-06-10
---

This is a common requirement for journals and other publications in
the humanities.  Sometimes the requirement is for the entry to appear
in the running text of the document, while other styles require that
the entry appear in a footnote.

Options for entries in running text are
  

-  The package [`bibentry`](https://ctan.org/pkg/bibentry), which puts slight restrictions
    on the format of entry that your `bst` file generates, but is
    otherwise undemanding of the bibliography style.
-  The package [`inlinebib`](https://ctan.org/pkg/inlinebib), which requires that you use its
    `inlinebib.bst`.  [`Inlinebib`](https://ctan.org/pkg/Inlinebib) was actually designed for
    footnote citations: its _expected_ use is that you place a
    citation inline as the argument of a `\footnote` command.
-  The package [`jurabib`](https://ctan.org/pkg/jurabib), which was originally designed for
    German law documents, and has comprehensive facilities for the
    manipulation of citations.  The package comes with four bibliography
    styles that you may use: `jurabib.bst`, `jhuman.bst` and
    two Chicago-like ones.

Options for entries in footnotes are
  

-  The package [`footbib`](https://ctan.org/pkg/footbib), and
-  Packages [`jurabib`](https://ctan.org/pkg/jurabib) and [`inlinebib`](https://ctan.org/pkg/inlinebib), again.

Note that [`jurabib`](https://ctan.org/pkg/jurabib) does the job using LaTeX's standard
footnotes, whereas [`footbib`](https://ctan.org/pkg/footbib) creates its own sequence of
footnotes.  Therefore, in a document which has other footnotes, it may
be advisable to use [`jurabib`](https://ctan.org/pkg/jurabib) (or of course
[`inlinebib`](https://ctan.org/pkg/inlinebib)), to avoid confusion of footnotes and
foot-citations.

The [`usebib`](https://ctan.org/pkg/usebib) package offers a ''toolbox'', which allows the user
to place exactly what is needed, in the text (that is, rather than a
full citation).  The package's command, that does the actual
typesetting, is `\usebibdata{<key>}{<field>}`; it
typesets the _field_ item from the entry _key_ in the
bibliography; the user then formats the entry as desired&nbsp;&mdash; obviously
one could construct one's own bibliography, altogether, from this
command, but it would quickly become tedious.

