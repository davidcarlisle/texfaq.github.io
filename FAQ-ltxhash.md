---
title: Defining LaTeX commands within other commands
category: programming
tags: macros latex
permalink: /FAQ-ltxhash
date: 2014-06-10
---

LaTeX command definition is significantly different from the TeX
primitive form discussed in an 
[earlier question](FAQ-hash) about definitions within
macros.

In most ways, the LaTeX situation is simpler (at least in part
because it imposes more restrictions on the user); however, defining a
command within a command still requires some care.

The earlier question said you have to double the `#` signs in command
definitions: in fact, the same rule holds, except that LaTeX
already takes care of some of the issues, by generating argument lists
for you.

The basic problem is that:
<!-- {% raw %} -->
```latex
\newcommand{\abc}[1]{joy, oh #1!%
  \newcommand{\ghi}[1]{gloom, oh #1!}%
}
```
<!-- {% endraw %} -->
followed by a call:
```latex
\cmdinvoke{abc}{joy}
```
typesets ''joy, oh joy!'', but defines a command `\ghi` that takes
one parameter, which it ignores; `\ghi{gloom}` will expand to
''gloom, oh joy!'', which is presumably not what was expected.

And (as you will probably guess, if you've read the earlier question)
the definition:
<!-- {% raw %} -->
```latex
\newcommand{\abc}[1]{joy, oh #1!%
  \newcommand{\ghi}[1]{gloom, oh ##1!}%
}
```
<!-- {% endraw %} -->
does what is required, and `\ghi{gloom}` will expand to
''gloom, oh gloom!'', whatever the argument to `\abc`.

The doubling is needed whether or not the enclosing command has an
argument, so:
<!-- {% raw %} -->
```latex
\newcommand{\abc}{joy, oh joy!%
  \newcommand{\ghi}[1]{gloom, oh ##1!}%
}
```
<!-- {% endraw %} -->
is needed to produce a replica of the `\ghi` we defined earlier.

