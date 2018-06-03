---
title: Why doesn't `\linespread` work?
category: usage
permalink: /FAQ-linespread
---

The command `\linespread{factor}` is supposed to multiply
the current `\baselineskip` by &lsaquo;_factor_&rsaquo;; but, to all
appearances, it doesn't.

In fact, the command is equivalent to
`\renewcommand{`\baselinestretch`}{factor}`: written that
way, it somehow feels less surprising that the effect isn't immediate.
The `\baselinestretch` factor is only used when a font is selected;
a mere change of `\baselinestretch` doesn't change the font, any
more than does the command
`\fontsize{size}{baselineskip}`&nbsp;&mdash; you have to follow
either command with `\selectfont`.  So:
```latex
\fontsize{10}{12}%
\selectfont
```
or:
```latex
\linespread{1.2}%
\selectfont
```
Of course, a package such as [`setspace`](https://ctan.org/pkg/setspace), whose job is to
manage the baseline, will deal with all this stuff&nbsp;&mdash; see
"[managing double-spaced documents](FAQ-linespace)".  If
you want to avoid [`setspace`](https://ctan.org/pkg/setspace), beware the behaviour of
linespread changes within a paragraph: read 
"[`\baselineskip` is a paragraph parameter](FAQ-baselinepar)".

