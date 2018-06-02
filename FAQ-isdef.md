---
title: Is this command defined?
category: programming
tags: macros
permalink: /FAQ-isdef
date: 2014-06-10
---

# Is this command defined?

Macro sets from the earliest days of TeX programming may be
observed to test whether commands exist by using
`\ifx\<command>\undefined` &lsaquo;_stuff_&rsaquo; &hellip;
(which of course actually tests that the command _doesn't_
exist).  LaTeX programmers can make use of the internal command
  `\@ifundefined{cmd name}{action1}{action2}`
which executes `action1` if the command is undefined, and
`action2` if it is defined
(_cmd name_ is the command name only, omitting the `\` character).

The `\@ifundefined` command is based on the sequence
```latex
\expandafter \ifx \csname cmd name\endcsname \relax
```
which relies on the way `\csname` works: if the command doesn't
exist, it simply creates it as an alias for `\relax`.

So: what is wrong with these techniques?

Using `\undefined` blithely assumes that the command is indeed not
defined.  This isn't entirely safe; one could make the name more
improbable, but that may simply make it more difficult to spot a
problem when things go wrong.  LaTeX programmers who use the
technique will typically employ `\@undefined`, adding a single
level of obscurity.

The original `\@ifundefined` mechanism had the unfortunate property of
polluting the name space: each test that turns out undefined adds a
name to the set TeX is holding, and often all those `\relax`
names serve no purpose whatever. 

David Kastrup offers the (rather tricky)
```latex
{\expandafter}\expandafter\ifx \csname cmd name\endcsname\relax ...
```
which ''creates'' the `\relax`-command inside the group of the first
`\expandafter`, therefore forgets it again once the test is done.
The test is about as good as you can do with macros.

The [&epsilon;-TeX system](FAQ-etex) system comes to our help here: it
defines two new primitives:
  

-  `\ifdefined`, which tests whether a thing is defined (the
    negative of comparing with `\undefined`, as it were), and
-  `\ifcsname cmd name\endcsname`, which does the
    negative of `\@ifundefined` without the `\relax`-command
    side-effect.

So, in an &epsilon;-TeX-based system, the following two conditional clauses do
the same thing:
```latex
\ifdefined\foo
  \message{\string\foo\space is defined}%
\else
  \message{no command \string\foo}%
\fi
%
\ifcsname foo\endcsname
  \message{\string\foo\space is defined}%
\else
  \message{no command \string\foo}%
\fi
```
However, after using the original LaTeX
`\@ifundefined{foo}`&hellip;, the conditionals will detect the
command as ''existing'' (since it has been `\let` to `\relax`);
so it is important not to mix mechanisms for detecting the state of a
command.

In the 2016 LaTeX release, the definition of `\@ifundefined` was adapted
to use the &epsilon;-TeX `\ifcsname` and now tests for a command being undefined or `\relax`
without the side effect of defining undefined commands to `\relax`.
