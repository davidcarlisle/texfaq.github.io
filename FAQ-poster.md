---
title: Creating posters with LaTeX
category: formatting
tags: classes
permalink: /FAQ-poster
date: 2014-06-10
---

There is no complete ''canned solution'' to creating a poster (as, for
example, classes like [`seminar`](https://ctan.org/pkg/seminar), [`powerdot`](https://ctan.org/pkg/powerdot) and
[`beamer`](https://ctan.org/pkg/beamer) serve for creating presentations in a variety of
styles).

The nearest approach to the complete solution is the [`sciposter`](https://ctan.org/pkg/sciposter)
class, which provides the means to produce really rather good posters
according to the author's required style.  A complete worked example
is provided with the distribution

Otherwise, there is a range of tools, most of which are based on the
[`a0poster`](https://ctan.org/pkg/a0poster) class, which sets up an appropriately-sized piece of
paper, sets font sizes appropriately, and leaves you to your own
devices.

Having used [`a0poster`](https://ctan.org/pkg/a0poster), you can of course slog it out, and write
all your poster as an unadorned LaTeX document (presumably in
multiple columns, using the [`multicol`](https://ctan.org/pkg/multicol) package), but it's not really
necessary: the (straightforward) [`textpos`](https://ctan.org/pkg/textpos) package provides a
simple way of positioning chunks of text, or tables or figures, on the
poster page.

More sophisticated is the [`flowfram`](https://ctan.org/pkg/flowfram) package, whose basic aim
in life is flowing text from one box on the page to the next.  One of
the package's design aims seems to have been the production of
posters, and a worked example is provided.  The author of
[`flowfram`](https://ctan.org/pkg/flowfram) has an experimental tool called
[FlowframTk (formerly called JpgfDraw)](https://www.dickimaw-books.com/software.html#flowframtk), which
allows you to construct the outline of frames for use with
[`flowfram`](https://ctan.org/pkg/flowfram).

The [`beamerposter`](https://ctan.org/pkg/beamerposter) package is added to a 
[`beamer`](https://ctan.org/pkg/beamer) document to enable the user to work
as if in a [`a0poster`](https://ctan.org/pkg/a0poster) class.  Thus [`beamer`](https://ctan.org/pkg/beamer)'s neat
provisions for layout may be used when creating the poster.
Documentation of [`beamerposter`](https://ctan.org/pkg/beamerposter) is sparse, but an example file
allows the user to get a grip on what's available.

Despite the relative shortage of tools, there are a fair few web pages
that explain the process (mostly in terms of the [`a0poster`](https://ctan.org/pkg/a0poster)
route):
  

-  from Norman Gray, 
    [Producing posters using LaTeX](https://nxg.me.uk/docs/posters/);
-  from Nicola Talbot, 
    [Creating technical posters with LaTeX](https://www.dickimaw-books.com/latex/posters/)
-  From Rob Clark 
    [Advanced LaTeX Posters](http://homepages.inf.ed.ac.uk/robert/posters/advanced.html) 
    (which has links to code samples);
-  from Brian Wolven, 
    [LaTeX Poster Macros, Examples, and Accessories (Internet Archive)](https://web.archive.org/web/20040204003003/http://fuse.pha.jhu.edu/~wolven/posters.html) 
    (this page also provides macros and other support suggestions).

