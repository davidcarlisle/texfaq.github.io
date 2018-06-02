---
title: [`Hyperref`](https://ctan.org/pkg/Hyperref) and repeated page numbers
category: usage
permalink: /FAQ-pdfpagelabels
date: 2014-06-10
---

# [`Hyperref`](https://ctan.org/pkg/Hyperref) and repeated page numbers

The [`book`](https://ctan.org/pkg/book) class (and its friends and relations) automatically
changes the display of page numbers in the frontmatter of the document
to lower-case roman.  This is fine for human readers, but if
[`hyperref`](https://ctan.org/pkg/hyperref) has been misconfigured, the existence of pages have
the same page number can cause problems.  Fortunately, the
configuration options to make [`hyperref`](https://ctan.org/pkg/hyperref) ''do the right
thing'' are (by default) set up to avoid problems.

The two options in question are:

- `plainpages=false` Make page anchors using the
  formatted form of the page number.  With this option,
  [`hyperref`](https://ctan.org/pkg/hyperref) writes different anchors for pages ''ii'' and ''2''.
  (This is the default value for the option, which is a 
  _good thing_&hellip;)
  If the option is set `true` [`hyperref`](https://ctan.org/pkg/hyperref) writes page
  anchors as the arabic form of the page number, rather than the
  formatted form that gets printed; this is not usually appropriate.
- `pdfpagelabels` Set PDF page labels; i.e.,
  write the value of `\thepage` to the PDF file so that
  Acrobat Reader can display the page number as (say) ''ii (4
  of 40)'' rather than simply ''4 of 40''.

The two should be used whenever page numbering is not just
''1&hellip;n''; they may be used independently, but
usually are not.

The recipe isn't perfect: it relies on `\thepage` being different
for every page in the document.  A common problem arises when there is
an unnumbered title page, after which page numbers are reset: the
pdfTeX warning of ''[duplicate destinations](FAQ-hyperdupdest)''
will happen in this case, regardless of the options.

