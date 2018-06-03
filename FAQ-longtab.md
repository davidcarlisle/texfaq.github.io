---
title: Tables longer than a single page
category: floats
tags:
  - tables
  - figures
permalink: /FAQ-longtab
---

Tables are, by default, set entirely in boxes of their own: as a
result, they won't split over a page boundary.  Sadly, the world keeps
turning up tables longer than a single page that we need to typeset.

For simple tables (whose shape is highly regular), the simplest
solution may well be to use the `tabbing` environment,
which is slightly tedious to set up, but which doesn't force the whole alignment
onto a single page.

The [`longtable`](https://ctan.org/pkg/longtable) package builds the whole table (in chunks), in
a first pass, and then uses information it has written to the `aux`
file during later passes to get the setting "right" (the package
ordinarily manages to set tables in just two passes).  Since the
package has overview of the whole table at the time it's doing
"final" setting, the table is set "uniformly" over its entire
length, with columns matching on consecutive pages.
[`longtable`](https://ctan.org/pkg/longtable) has a reputation for failing to interwork with
other packages, but it does work with [`colortbl`](https://ctan.org/pkg/colortbl), and its
author has provided the [`ltxtable`](https://ctan.org/pkg/ltxtable) package to provide (most
of) the facilities of [`tabularx`](https://ctan.org/pkg/tabularx) (see
[fixed-width tables](FAQ-fixwidtab)) for long tables:
beware of its rather curious usage constraints&nbsp;&mdash; each long table
should be in a file of its own, and included by
`\LTXtable{width}{file}`.  Since [`longtable`](https://ctan.org/pkg/longtable)'s
multiple-page tables can't possibly live inside floats, the package
provides for captions within the `longtable` environment
itself.

A seeming alternative to [`ltxtable`](https://ctan.org/pkg/ltxtable) is [`ltablex`](https://ctan.org/pkg/ltablex); but
it is outdated and not fully functional.  Its worst problem is its
strictly limited memory capacity ([`longtable`](https://ctan.org/pkg/longtable) is not so
limited, at the cost of much complication in its code);
[`ltablex`](https://ctan.org/pkg/ltablex) can only deal with relatively small tables, it doesn't seem
likely that support is available; but its user interface is much
simpler than [`ltxtable`](https://ctan.org/pkg/ltxtable), so if its restrictions aren't a
problem for you, it may be worth a try.

The [`supertabular`](https://ctan.org/pkg/supertabular) package starts and stops a
`tabular` environment for each page of the table.  As a
result, each "page worth" of the table is compiled independently, and
the widths of corresponding columns may differ on successive pages.
However, if the correspondence doesn't matter, or if your columns are
fixed-width, [`supertabular`](https://ctan.org/pkg/supertabular) has the great advantage of doing
its job in a single run.

Both [`longtable`](https://ctan.org/pkg/longtable) and [`supertabular`](https://ctan.org/pkg/supertabular) allow definition
of head- and footlines for the table; [`longtable`](https://ctan.org/pkg/longtable) allows
distinction of the first and last head and foot.

The [`xtab`](https://ctan.org/pkg/xtab) package fixes some infelicities of
[`supertabular`](https://ctan.org/pkg/supertabular), and also provides a "last head" facility
(though this, of course, destroys [`supertabular`](https://ctan.org/pkg/supertabular)'s advantage
of operating in a single run).

The [`stabular`](https://ctan.org/pkg/stabular) package provides a simple-to-use "extension to
`tabular`" that allows it to typeset tables that run over
the end of a page; it also has usability extensions, but doesn't have
the head- and footline capabilities of the major packages.

Documentation of [`ltablex`](https://ctan.org/pkg/ltablex) is to be found in the package file.

