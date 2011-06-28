---
title: Yasm 0.4.0
longtitle: Yasm 0.4.0 Release Notes
layout: default
---

Target Audience
===============

Welcome to the fourth milestone release of the Yasm Modular Assembler.  As this is still a pre-1.0 product, there are certain to be many bugs and missing features. This release is intended to provide a stable snapshot of Yasm development as of 10/31/04.  Its target audience includes people who:

 * want to try out (and help test) a NASM-syntax AMD64 assembler;
 * want to keep track of Yasm's progress in terms of stability and feature set;
 * want to test Yasm with their own code to help test it;
 * want to get started on Yasm development from a new release;
 * are just interested in the Yasm project.

Features
========

New features in this release:
-----------------------------

 * ELF AMD64 and 32-bit shared object support (using the NASM notation "WRT ..got", etc).
 * STABS debugging format (enable with "-g stabs").
 * NASM-like list format.
 * XDF object format (64-bit basic format, similar in spirit to NASM's RDF).
 * Dozens of bugfixes in x86 and AMD64 support.
 * Numerous cross-platform build fixes.
 * No perl dependencies for standard build.
 * New man pages: yasm(1) and yasm_arch(7).

Features available in previous version of Yasm include:
-------------------------------------------------------

 * Full support for ELF, including support for both AMD64 and 32-bit x86 targets; note: for AMD64 output, the machine type must be set to "amd64" using the "-m" command line option, e.g. "yasm -m amd64 -f elf test.asm".
 * Full warnings for integer overflow.
 * Full support for AMD64 RIP-relative addressing; the two forms supported are `[rip+val]` (direct index) and `[sym wrt rip]` (relocated relative).
 * Full support for COFF (DJGPP) and Win32 object format output.
 * "Real" NASM preprocessor (imported from NASM tree).
 * Support for AMD64 instruction set, registers, and addressing modes (mostly untested). This is enabled using the `[BITS 64]` directive and "-m amd64" command line option; see the AMD64 tests for the x86 architecture and ELF64 tests for more details.
 * Numerous bug fixes and code cleanups.
 * Most code licensed under 2-clause BSD license, although some portions are still LGPL-licensed (NASM preprocessor module).
 * Support for the -I option to specify include directories.
 * Support for CALL/JMP FAR, including proper handling of `location EQU seg:off`; `jmp location`.

Important Differences from NASM
===============================

 * Yasm defaults to reading from standard input if no files are specified. When an input file is specified, Yasm behaves like NASM.
 * A number of command line options are different. Run "yasm --help" for a quick command line option summary, or read the full yasm(1) manpage for detailed descriptions of all command line options.

Known Issues
============

As Yasm is still under development, there are some caveats and features that do not yet work or are not yet fully functional.  The following are the known issues at the time of release:

 * Changing the machine to "amd64" does not automatically default to bits 64 mode; specify BITS 64 in the assembly source as a workaround.
 * The optimizer is very basic 2-pass style (even so it should be slightly better than NASM's 2-pass optimizer).

Download Yasm 0.4.0
===================

A number of download forms are available. For Windows and DOS users, we recommend downloading the prebuilt binaries. The source tarball contains all sources needed to build Yasm on UNIX-compatible systems, Windows, and DOS.

 * [Source .tar.gz]({{site.releases}}/yasm-0.4.0.tar.gz)
 * [Win32 .exe]({{site.releases}}/yasm-0.4.0-win.exe) (for "normal" (Visual Studio or similar) use)
 * [Win32 .exe]({{site.releases}}/yasm-0.4.0-cygwin.exe) (for [CygWin](http://www.cygwin.com/) use)
 * [DOS .exe]({{site.releases}}/yasm-0.4.0-dos.exe) (for use on pure DOS or for use with [DJGPP](http://www.delorie.com/djgpp))

Compiling Yasm from source
==========================

On UNIX-compatible operating systems, Yasm builds using the standard "./configure; make; make install" commands. GNU make is not required. While Yasm development requires a larger toolchain (see the HACKING file), building Yasm should not require more than just a C compiler.

For Windows and DOS systems, we recommend simply downloading the prebuilt executables. However, for those that want to build YASM directly using [DJGPP](http://www.delorie.com/djgpp/), [CygWin](http://www.cygwin.com/), or Visual C++, Makefiles and all required specialized files are provided in the Mkfiles/ directory of the distribution tarball.

Running Yasm
============

Version Information:

    yasm --version

Command Line Option Help:

    yasm --help

Assemble test.asm (using "real" NASM preprocessor) to Win32 object file test.obj:

    yasm -f win32 test.asm

Assemble test2.asm to AMD64 ELF object file test2.o:

    yasm -m amd64 -f elf test2.asm

