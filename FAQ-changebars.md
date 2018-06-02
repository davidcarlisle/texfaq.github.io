---
title: Marking changed parts of your document
category: usage
permalink: /FAQ-changebars
date: 2014-06-10
---

One often needs clear indications of how a document has changed, but
the commonest technique, ''change bars'' (also known as ''revision
bars''), requires surprisingly much
trickery of the programmer.  The problem is that TeX ''proper''
doesn't provide the programmer with any information about the
''current position'' from which a putative start- or end-point of a
bar might be calculated.   pdfTeX _does_ provide that
information, but no pdfTeX-based changebar package has been
published, that takes advantage of that.

The simplest package that offers change bars is Peter Schmitt's
[`backgrnd.tex`](https://ctan.org/pkg/backgrnd); this was written as a Plain TeX application
that patches the output routine, but it appears to work at least on
simple LaTeX documents.  Wise LaTeX users will be alerted by the
information that [`backgrnd`](https://ctan.org/pkg/backgrnd) patches their output routine, and
will watch its behaviour very carefully (patching the LaTeX output
routine is not something to undertake lightly&hellip;).

The longest-established LaTeX-specific solution is the
[`changebar`](https://ctan.org/pkg/changebar) package,
which uses `\special` commands supplied by the driver you're using.
You need therefore to tell the package which driver to you're using
(in the same way that you need to tell the [`graphics`](https://ctan.org/pkg/graphics)
package); the list of available drivers is pretty
wide, but does not include `dvipdfm`.  The package comes with
a shell script `chbar.sh` (for use on Unix machines) that
will compare two documents and generate a third which is marked-up
with [`changebar`](https://ctan.org/pkg/changebar) macros to highlight changes.

The shareware `WinEDT` editor has a macro that will generate
[`changebar`](https://ctan.org/pkg/changebar) (or other) macros to show differences from an
earlier version of your file, stored in an `RCS`-controlled
repository&nbsp;&mdash; see
[http://www.winedt.org/Macros/LaTeX/RCSdiff.php]

The [`vertbars`](https://ctan.org/pkg/vertbars) package uses the techniques of the
[`lineno`](https://ctan.org/pkg/lineno) package (which it loads, so the [`lineno`](https://ctan.org/pkg/lineno)
itself must be installed); it's thus the smallest of the packages for
change bar marking, since it leaves all the trickery to another
package.  [`Vertbars`](https://ctan.org/pkg/Vertbars) defines a `vertbar`
environment to create changebars.

The [`framed`](https://ctan.org/pkg/framed) package is
another that provides bars as a side-effect of other desirable
functionality: its `leftbar` environment is simply a
stripped-down frame (note, though, that the environment makes a
separate paragraph of its contents, so it is best used when the
convention is to mark a whole changed paragraph.

Finally, the [`memoir`](https://ctan.org/pkg/memoir) class allows marginal editorial comments,
which you can obviously use to delimit areas of changed text.

An even more comprehensive way to keep track of changes is employed by
some word-processors&nbsp;&mdash; to produce a document that embodies both
''old'' and ''new'' versions.

To this end, the package [`changes`](https://ctan.org/pkg/changes) allows the user to manually
markup changes of text, such as additions, deletions, or replacements.
Changed text is shown in a different color; deleted text is crossed
out.  The package allows you to define additional authors and their
associated color; it also allows you to define a markup for authors
or annotations.  The documentation (very clearly) demonstrates how the
various functions work.

The `Perl` script `latexdiff` may also be used to
generate such markup for LaTeX documents; you feed it the two
documents, and it produces a new LaTeX document in which the
changes are very visible.  An example of the output is embedded in the
documentation,
  [latexdiff-man.pdf](https://ctan.org/pkg/latexdiff)
  (part of the distribution).
A rudimentary revision facility is provided by another
`Perl` script, `latexrevise`, which accepts or rejects
all changes.  Manual editing of the difference file can be used to 
accept or reject selected changes only.

