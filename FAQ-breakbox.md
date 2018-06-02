---
title: Breaking boxes of text
category: formatting
permalink: /FAQ-breakbox
date: 2014-06-10
---

(La)TeX boxes may not be broken, in ordinary usage: once you've
typeset something into a box, it will stay there, and the box will jut
out beyond the side or the bottom of the page if it doesn't fit in the
typeset area.

If you want a substantial portion of your text to be framed (or
colored), the restriction imposes a serious restriction.
Fortunately, there are ways around the problem.

The [`framed`](https://ctan.org/pkg/framed) package provides `framed` and
`shaded` environments; both put their content into
something which looks like a framed (or colored) box, but which
breaks as necessary at page end.  The environments ''lose'' footnotes,
marginpars and head-line entries, and will not work with
[`multicol`](https://ctan.org/pkg/multicol) or other column-balancing macros.  The
[`memoir`](https://ctan.org/pkg/memoir) class includes the functionality of the
[`framed`](https://ctan.org/pkg/framed) package.

The [`mdframed`](https://ctan.org/pkg/mdframed) package does the same job, using a different
algorithm.  The package also provides means of defining
''private'' framed environments, whose parameters are set at definition
time, thus saving considerable effort in documents with many framed
boxes.  Its restrictions seem much the same as those of
[`framed`](https://ctan.org/pkg/framed); this is as one would expect, but the list is
noticeably different in the two packages' documentation.

The [`boites`](https://ctan.org/pkg/boites) package provides a `breakbox`
environment; examples of its use may be found in the distribution, and
the package's `README` file contains terse documentation.  The
environments may be nested, and may appear inside
`multicols` environments; however, floats, footnotes and
marginpars will be lost.

For Plain TeX users, the facilities of the [`backgrnd`](https://ctan.org/pkg/backgrnd)
package may be useful; this package subverts the output routine to
provide vertical bars to mark text, and the macros are clearly marked
to show where colored backgrounds may be introduced (this requires
[`shade`](https://ctan.org/pkg/shade), which is distributed as tex macros and
device-independent MetaFont for the shading).  The author of
[`backgrnd`](https://ctan.org/pkg/backgrnd) claims that the package works with LaTeX 2.09, but
there are reasons to suspect that it may be unstable working with
current LaTeX.

