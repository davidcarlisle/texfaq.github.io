---
title: How many pages are there in my document?
category: usage
permalink: /FAQ-howmanypp
date: 2014-06-10
---

Simple documents (those that start at page 1, and don't have any
breaks in their page numbering until their last page) present no
problem to the seeker after this truth.  The number of pages is
reported by the [`lastpage`](https://ctan.org/pkg/lastpage) package in its `LastPage` label.

For more complicated documents (most obviously, books with frontmatter
in a different series of page numbers) this simple approach will not
do.

The [`count1to`](https://ctan.org/pkg/count1to) package defines a label `TotalPages`; this is
the value of its copy of `\count1` (a reserved TeX count
register) at the end of the document.

Package [`totpages`](https://ctan.org/pkg/totpages) defines a label `TotPages`, but it also
makes the register it uses available as a LaTeX counter,
`TotPages`, which you can also reference via `\theTotPages`.  Of
course, the counter `TotPages` is asynchronous in the same way that
page numbers are, but snapshots may safely be taken in the output
routine.

The [`memoir`](https://ctan.org/pkg/memoir) class defines two counters `lastpage` and
`lastsheet`, which are set (after the first run of a document)
to the equivalent of the `LastPage` label and the
`TotalPages` labels.

Both [`count1to`](https://ctan.org/pkg/count1to) and [`totpages`](https://ctan.org/pkg/totpages) need the support of
the [`everyshi`](https://ctan.org/pkg/everyshi) package.

