---
title: Old LaTeX font references such as `\tenrm`
category: errors
tags: deprecated
permalink: /FAQ-oldfontnames
---

LaTeX 2.09 defined a large set of commands for access to the fonts
that it had built in to itself.  For example, `cmr` might
appear as `\fivrm`, `\sixrm`, `\sevrm`,
`\egtrm`, `\ninrm`, `\tenrm`, `\elvrm`, `\twlrm`,
`\frtnrm`, `\svtnrm`, `\twtyrm` and `\twfvrm`, according
to the size it's being typeset at.
These commands were never documented, but certain packages
nevertheless used them to achieve effects they needed.

Since the commands weren't public, they weren't included in LaTeX2e;
to use the unconverted LaTeX 2.09 packages under LaTeX2e, you need
also to include the [`rawfonts`](https://ctan.org/pkg/rawfonts) package (which is part of the
LaTeX2e distribution).

