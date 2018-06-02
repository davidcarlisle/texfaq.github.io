---
title: Packages to set up page designs
category: formatting
tags: layout
permalink: /FAQ-marginpkgs
date: 2014-06-10
---

There are two trustworthy tools for adjusting the dimensions and position of the
printed material on the page are [`geometry`](https://ctan.org/pkg/geometry) and the
[`zwpagelayout`](https://ctan.org/pkg/zwpagelayout) packages; a very
wide range of adjustments of the layout may be relatively
straightforwardly programmed with either, and package documentation is good and
comprehensive.

As is usual, users of the [`memoir`](https://ctan.org/pkg/memoir) class have built-in
facilities for this task, and users of the [`KOMA-script`](https://ctan.org/pkg/KOMA-script) classes
are recommended to use an alternative package, [`typearea`](https://ctan.org/pkg/typearea).  In
either case it is difficult to argue that users should go for
[`geometry`](https://ctan.org/pkg/geometry): both alternatives are good.

The documentation both of [`geometry`](https://ctan.org/pkg/geometry) and of
[`zwpagelayout`](https://ctan.org/pkg/zwpagelayout) is rather overwhelming, and
learning all of of either package's capabilities is likely to be more
than you ever need.
The [`vmargin`](https://ctan.org/pkg/vmargin) package is somewhat simpler to use: it has a
canned set of paper sizes (a superset of that provided in LaTeX2e),
provision for custom paper, margin adjustments and provision for
two-sided printing.

