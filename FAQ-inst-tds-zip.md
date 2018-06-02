---
title: Installing using ready-built ZIP files
category: installing
permalink: /FAQ-inst-tds-zip
date: 2014-06-10
---

Installing packages, as they (''traditionally'') appear on
CTAN, involves:
  

-  identifying where to put the various files on an TDS
    tree,
-  installing them, and
-  a few housekeeping operations.

Most people, for most packages, find the first two steps onerous, the
last being easy (unless it is forgotten!).

Ready-built ZIP files&nbsp;&mdash; also known as 
[TDS-ZIP files](FAQ-tds-zip)&nbsp;&mdash; are designed to lighten
the load of performing the first two steps of installation: they
contain all the files that are to be installed for a given
package, in their ''correct'' locations in a 
[TDS tree](FAQ-tds).

To install such a file on a Unix system (we assume that you'll install
into the local TEXMF tree, at `$TEXMFLOCAL`):
```
cd $TEXMFLOCAL
unzip $package.tds.zip
```

On a Windows system that is modern enough that it has a built-in
ZIP unpacker, simply double-click on the file, and browse to
where it's to be unpacked.  (We trust that those using earlier
versions of Windows will already have experience of using
`WinZIP` or the like.)

Having unpacked the `zip` archive, in most cases the only
remaining chore is to update the file indexes&nbsp;&mdash; as in 
[normal installation instructions](FAQ-inst-wlcf).  However, if
the package provides a font, you also need to enable the font's map,
which is discussed in 
''[Installing a Type&nbsp;1 font](FAQ-instt1font)''

