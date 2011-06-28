---
title: Yasm 0.5.0rc1
longtitle: Yasm 0.5.0rc1 Release Notes
layout: default
---

Target Audience
===============

Welcome to the first release candidate for the fifth milestone release of the Yasm Modular Assembler.  The purpose of this release is to shake down some bugs prior to the 0.5.0 release, as there have been some significant new features added since the previous release.  Its target audience includes people who:

 * want to try out a NASM-syntax AMD64 assembler;
 * want to try out the newly supported GAS syntax or DWARF2 debugging support;
 * want to keep track of Yasm's progress in terms of stability and feature set;
 * want to test Yasm with their own code to help test it;
 * want to get started on Yasm development from a new release;
 * want to ensure high quality of the 0.5.0 final release;
 * are just interested in the Yasm project.

Features
========

New features in this release candidate (compared to 0.4.0):
-----------------------------------------------------------

 * Aliases for AMD64 object formats: "win64" and "elf64" (these automatically set the machine to "amd64").
 * "x64" alias for Win64 object format (for easier use with Visual Studio).
 * DWARF2 debugging format (enable with "-g dwarf2").
 * GAS parser good enough to take GCC output for both AMD64 and 32-bit x86 (including DWARF2 debug information).
 * Dozens of bugfixes in x86 and AMD64 support.
 * Specifying "amd64" as the machine (or using a 64-bit object format) automatically sets BITS 64.

Features available in previous version of Yasm include:
-------------------------------------------------------

 * Full support for ELF, including support for both AMD64 and 32-bit x86 static and shared objects.
 * Full warnings for integer overflow.
 * Full support for AMD64 RIP-relative addressing; the two forms supported are `[rip+val]` (direct index) and `[sym wrt rip]` (relocated relative).
 * Full support for COFF (DJGPP) and Win32 (PE32) and Win64 (PE32+) object formats.
 * STABS debugging format (enable with "-g stabs").
 * NASM-like list format.
 * XDF object format (64-bit basic format, similar in spirit to NASM's RDF).
 * "Real" NASM preprocessor (imported from NASM tree).
 * Support for AMD64 instruction set, registers, and addressing modes (mostly untested). This is enabled in one of three ways: using the `[BITS 64]` directive, using a 64-bit object format such as win64 or elf64, or setting the machine to "amd64".  Only the last two will actually generate a 64-bit object file.
 * Numerous bug fixes and code cleanups.
 * Most code licensed under 2-clause BSD license, although some portions are still LGPL-licensed (NASM preprocessor module).
 * Support for the -I option to specify include directories.
 * Support for CALL/JMP FAR, including proper handling of "location EQU seg:off; jmp location".
 * Man pages: yasm(1) and yasm_arch(7).

Important Differences from NASM
===============================

 * Yasm defaults to reading from standard input if no files are specified. When an input file is specified, Yasm behaves like NASM.
 * A number of command line options are different. Run "yasm --help" for a quick command line option summary, or read the full yasm(1) manpage for detailed descriptions of all command line options.

Known Issues
============

As Yasm is still under development, there are some caveats and features that do not yet work or are not yet fully functional.  The following are the known issues at the time of release:

 * List output is buggy and often outright wrong.
 * The optimizer is a very basic 2-pass style and generates very inefficient code at times.  We're hoping to fix this before the 0.5.0 final release.

Download Yasm 0.5.0rc1
======================

A number of download forms are available. For Windows and DOS users, we recommend downloading the prebuilt binaries. The source tarball contains all sources needed to build Yasm on UNIX-compatible systems, Windows, and DOS.

 * [Source .tar.gz]({{site.releases}}/yasm-0.5.0rc1.tar.gz)
 * [Win32 .exe]({{site.releases}}/yasm-0.5.0rc1-win.exe) (for "normal" (Visual Studio or similar) use on 32-bit Windows)
 * [Win64 .exe]({{site.releases}}/yasm-0.5.0rc1-win64.exe) (for "normal" (Visual Studio or similar) use on 64-bit Windows)
 * [Win32 .exe]({{site.releases}}/yasm-0.5.0rc1-cygwin.exe) (for [CygWin](http://www.cygwin.com/) use)
 * [DOS .exe]({{site.releases}}/yasm-0.5.0rc1-dos.exe) (for use on pure DOS or for use with [DJGPP](http://www.delorie.com/djgpp))

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

Assemble test.asm to Win32 object file test.obj:

    yasm -f win32 test.asm

Assemble test2.asm to Win64 object file test.obj:

    yasm -f win64 test2.asm

Assemble test3.asm to AMD64 ELF object file test3.o with DWARF2 debugging information:

    yasm -f elf64 -g dwarf2 test3.asm

Alternative to above:

    yasm -f elf -m amd64 -g dwarf2 test3.asm

Assemble test4.s to 32-bit x86 ELF object file testo.o with DWARF2 debugging information:

    yasm -f elf32 -g dwarf2 -o testo.o test4.asm

