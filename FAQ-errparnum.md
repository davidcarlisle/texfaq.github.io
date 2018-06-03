---
title: Illegal parameter number in definition
category: errors
permalink: /FAQ-errparnum
---

The error message means what it says.  In the simple case, you've
attempted a definition like:
```latex
\newcommand{\abc}{joy, oh #1!}
```
or (using TeX primitive definitions):
```latex
\def\abc{joy, oh #1!}
```
In either of the above, the definition uses an argument, but the
programmer did not tell (La)TeX, in advance, that she was going to.
The fix is simple&nbsp;&mdash; `\newcommand{`\abc`}`[1], in the
LaTeX case, `\def\abc#1` in the basic TeX case.

The more complicated case is exemplified by the attempted definition:
<!-- {% raw %} -->
```latex
\newcommand{\abc}{joy, oh joy!%
  \newcommand{\ghi}[1]{gloom, oh #1!}%
}
```
<!-- {% endraw %} -->
will also produce this error, as will its TeX primitive equivalent:
<!-- {% raw %} -->
```latex
\def\abc{joy, oh joy!%
  \def\ghi#1{gloom, oh #1!}%
}
```
<!-- {% endraw %} -->
This is because special care is needed when defining one macro within
the code of another macro.  This is explained elsewhere, separately
for [LaTeX definitions](FAQ-ltxhash) and for
[TeX primitive definitions](FAQ-hash)

