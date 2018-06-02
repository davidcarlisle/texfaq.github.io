---
title: The Principal Value Integral symbol
category: formatting
permalink: /FAQ-prinvalint
date: 2014-06-10
---

This symbol (an integral sign, ''crossed'') does not appear in any of
the fonts ordinarily available to (La)TeX users, but it can be
created by use of the following macros:
<!-- {% raw %} -->
```
\def\Xint#1{\mathchoice
   {\XXint\displaystyle\textstyle{#1}}%
   {\XXint\textstyle\scriptstyle{#1}}%
   {\XXint\scriptstyle\scriptscriptstyle{#1}}%
   {\XXint\scriptscriptstyle\scriptscriptstyle{#1}}%
   \!\int}
\def\XXint#1#2#3{{\setbox0=\hbox{$#1{#2#3}{\int}$}
     \vcenter{\hbox{$#2#3$}}\kern-.5\wd0}}
\def\ddashint{\Xint=}
\def\dashint{\Xint-}
```
<!-- {% endraw %} -->
`\dashint` gives a single-dashed integral sign, `\ddashint` a
double-dashed one.

