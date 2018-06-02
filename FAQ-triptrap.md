---
title: How can I be sure it's really TeX?
category: background
permalink: /FAQ-triptrap
date: 2014-06-10
---

# How can I be sure it's really TeX?

TeX (and MetaFont and MetaPost) are written in a
  [''literate'' programming](FAQ-lit) language called `Web`
which is designed to be portable across a wide range of computer
systems.  How, then, is a new version of TeX checked?

Of course, any sensible software implementor will have his own suite
of tests to check that his software runs: those who port TeX and
its friends to other platforms do indeed perform such tests.

Knuth, however, provides a ''conformance test'' for both TeX
([`trip`](https://ctan.org/pkg/tex)) and MetaFont ([`trap`](https://ctan.org/pkg/metafont)).
He characterises these as ''torture tests'': they are designed not to
check the obvious things that ordinary typeset documents, or font
designs, will exercise, but rather to explore small alleyways off the
main path through the code of TeX.  They are, to the casual reader,
pretty incomprehensible!

Once an implementation of TeX has passed its [`trip`](https://ctan.org/pkg/tex) test, or
an implementation of MetaFont has passed its [`trap`](https://ctan.org/pkg/metafont) test, then it
may in principle be distributed as a working version.  (In practice,
any distributor would test new versions against ''real'' documents or
fonts, too; while [`trip`](https://ctan.org/pkg/tex) and [`trap`](https://ctan.org/pkg/metafont) test bits of
pathways within the program, they don't actually test for any real
world problem.)

