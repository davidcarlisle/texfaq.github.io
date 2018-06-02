---
title: `\spacefactor` complaints
category: errors
permalink: /FAQ-atvert
date: 2014-06-10
---

The errors
```latex
! You can't use `\spacefactor' in vertical mode.
\@->\spacefactor 
                 \@m 
```
or
```latex
! You can't use `\spacefactor' in math mode.
\@->\spacefactor 
                 \@m 
```
or simply
```latex
! Improper \spacefactor.
...
```
bite the LaTeX programmer who uses an internal command without
taking ''precautions''.  An internal-style command such as `\@foo`
has been defined or used in a private macro, and it is interpreted as
`\@`, followed by the ''text'' `foo`.  (`\@` is used, for
real, to set up end-of-sentence space in some circumstances; it uses
`\spacefactor` to do that.)

The problem is discussed in detail in
''[`@` in macro names](FAQ-atsigns)'',
together with solutions.

