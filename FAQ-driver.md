---
title: What is a DVI driver?
category: concepts
permalink: /FAQ-driver
date: 2014-06-10
redirect_from: /FAQ-HPdrivers
---

# What is a DVI driver?

A DVI driver is a program that takes as input a
[DVI file](FAQ-dvi)
and (usually) produces a file in a format that something _other_
than a TeX-related program can process.

A driver may be designed for producing output for printing (e.g.,
PostScript), for later processing (e.g., PostScript for inclusion in a later
document), or for document exchange (e.g., PDF).

As well as the DVI file, the driver typically also needs font
information.  Font information may be held as bitmaps or as outlines,
or simply as a set of pointers into the fonts that a printer itself
provides.  Each driver will expect the font information in a particular
form.

For more information on the forms of font information, see
[PK files](FAQ-pk),
[TFM files](FAQ-tfm),
[virtual fonts](FAQ-virtualfonts)
and [Using PostScript fonts with TeX](FAQ-usepsfont).

