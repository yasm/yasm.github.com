---
title: Participate
longtitle: Participating in Yasm Development
layout: default
---

Joining the Team
================

The [Yasm development team]({{site.wiki}}/YasmTeam) is currently very small, but we're open to more developers joining us!  Now that the object format interface is reaching stability (except for debug format support), we're looking for developers interested in working on additional object format support as well as other portions of Yasm.  [Peter Johnson]({{site.wiki}}/PeterJohnson) is the contact person for object formats and for development in general.  Drop him a note if you're interested!

You can also work independently.  Just [download](/Download.html) a nightly snapshot or get [Git](http://git-scm.com) and use it to download (recommended), and start hacking!

Feedback / Bugs
===============

Feel free to report bugs either on our [mailing lists](/MailingList.html) or (preferably) by using the [bug tracker](http://tortall.lighthouseapp.com/projects/78676-yasm).  Other feedback and general discussion can be made to the yasm-devel mailing list.

Code Contributions
==================

These are *always* appreciated!  If you have a great idea to add to yasm (which is wonderful) and have already written the code to do it (even better!) just let us know via the yasm-devel mailing list.  If you just have a great idea, but no code, submit it as a ticket.. but it might take us a little bit to implement it!

Project Ideas
=============

If you want to work on something but don't know what, here are some suggestions.  These projects range from little to huge (hopefully the task descriptions will give you an idea of what's involved).

 * Documentation!  The [Yasm User Manual](/Guide.html) is a work in progress.  While it's written in AsciiDoc, contributions in any format will be accepted; we'll take care of the AsciiDoc conversion!  The object formats section of the documentation particularly needs work.  This can be done a little piece at a time.

 * Yasm-developer starter documentation: while architecture doc exists ([pdf]({{site.reference}}/design/design.pdf), [html]({{site.reference}}/design/html/)), it's a little out of date and only covers the bare minimum introduction. Base source files are documented [here]({{site.reference}}/libyasm-doc/html/files.html), but something like overall source files overview, at glance, is needed.

 * Other object formats.  Microsoft OMF (aka OBJ), as86, a.out, etc.  Check with us first to make sure someone's not already working on it.  The XDF object format source ([modules/objfmts/xdf/xdf-objfmt.c]({{site.git}}/modules/objfmts/xdf/xdf-objfmt.c)) will give you an idea of the amount of code required, as well as a good starting point.  The complexity really depends on the complexity of the object format itself.

 * MASM or TASM parser.  In fact [TASM parser]({{site.wiki}}/TasmSyntax) is started, but it needs yet some work. Any help is appreciated, since nearly everyone wants this, and it would gain you fame and fortune (well, fame at least).  A major part of this will be adding a type system to the core Yasm symbol table handling, or maintaining an additional one within the parser.

 * Add object format reading capability (aka objdump).  The core infrastructure's not there yet to support this, but if there's interest in this we'll get the core pieces done for it to happen.

 * Other architectures.  We have a preliminary Python-based code generation framework for RISC machines (e.g. PPC); let us know if you're interested in finishing this work and we'll send it your direction.
