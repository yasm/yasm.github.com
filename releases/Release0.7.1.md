---
title: Yasm 0.7.1
longtitle: Yasm 0.7.1 Release Notes
layout: default
---

Target Audience
===============

Welcome to the 0.7.1 release of the Yasm Modular Assembler.  Its target audience includes people who want to:

 * use a mature NASM-syntax x86 and AMD64 assembler that can target Win32, Win64, MacOS X, and Unix derivatives;
 * use a GAS-syntax assembler other than GAS;
 * have assembly source-level debugging using either DWARF2 or CodeView 8.0 (2005);
 * have a free software assembler that supports Win32/Win64 structured exception handling (SEH) and ELF32/ELF64 thread local storage (TLS);
 * target the new AMD SSE5 or Intel AVX instruction sets;
 * keep track of Yasm's progress in terms of stability and feature set;
 * contribute to Yasm development from a new release.

Download Yasm 0.7.1
===================

A number of download formats are available. For Windows and DOS users, we recommend downloading the prebuilt binaries. The source tarball contains all sources needed to build Yasm on UNIX-compatible systems, Windows, and DOS.

 * [Source .tar.gz]({{site.releases}}/yasm-0.7.1.tar.gz)
 * [Win32 .exe]({{site.releases}}/yasm-0.7.1-win32.exe) (for "normal" (Visual Studio or similar) use on 32-bit Windows)
 * [Win64 .exe]({{site.releases}}/yasm-0.7.1-win64.exe) (for "normal" (Visual Studio or similar) use on 64-bit Windows)
 * [Win32 .exe]({{site.releases}}/yasm-0.7.1-cygwin.exe) (for [CygWin](http://www.cygwin.com/) use)
 * [DOS .exe]({{site.releases}}/yasm-0.7.1-dos.exe) (for use on pure DOS or for use with [DJGPP](http://www.delorie.com/djgpp))

Features
========

Changes from 0.7.0 to 0.7.1:
----------------------------

 * AVX instruction bugfixes (0.7.0 errata)
 * Build fixes (crashes on some machines)
 * Minor CPU flags fixes

Changes from 0.6.2 to 0.7.0:
----------------------------

 * Intel Advanced Vector Extensions (AVX) instruction support.
 * Multi-section binary support (see #71, #99, r2010).
 * Add support for ELF32 and ELF64 TLS (thread local storage) relocations.
 * Allow use of 0X in addition to 0x to prefix hex constants (#127).
 * Allow underscores in hex, binary, and octal constants (e.g. 0111_1111b).
 * Fix memory sizes on SSE/SSE2 instructions (#119).
 * Allow standalone prefixes (#122).
 * Simplify new varieties of sym-sym values (#124).
 * Support SAFESEH directive for win32 SEH handlers (#130).
 * Enable sym@FOO constructs in GAS parser.
 * SSE5 condition code support.
 * Other bugfixes.

Features also include:
----------------------

### Object and debugging format support:

 * Full support for ELF, including support for both AMD64 and 32-bit x86 static and shared objects and thread local storage.
 * Support for Mach-O object format used in MacOS X, including both the 32-bit (x86) and 64-bit (AMD64) versions (contributed by Henryk Richter).
 * Full support for COFF (DJGPP) and Win32 (PE32) and Win64 (PE32+) object formats.
 * Support for [structured exception handling]({{site.manual}}/objfmt-win64-exception.html) on Win64 and Win32.
 * Support for RDOFF2 (.rdf) object format.
 * XDF object format (64-bit basic format, similar in spirit to NASM's RDF).
 * Multi-section binary support (compatible but slightly more advanced than NASM's).

 * STABS, DWARF2, and CodeView 8 debugging formats (enable with "-g ...").

### Assembler syntax support:

 * Full NASM-compatible parser, including the "real" NASM preprocessor (imported from NASM tree).
 * GAS parser good enough to take GCC output for both AMD64 and 32-bit x86 (including DWARF2 debug information).

### Architecture support:

 * Support for AMD64 instruction set, registers, and addressing modes. This is enabled in one of three ways: using the `[BITS 64]` directive, using a 64-bit object format such as win64 or elf64, or setting the machine to "amd64".  Only the last two will actually generate a 64-bit object file.
 * Full support for AMD64 RIP-relative addressing; the two forms supported are `[rip+val]` (direct index) and `[sym wrt rip]` (relocated relative).

### Other features:

 * Fast and efficient "virtual multi-pass" optimizer that automatically generates much smaller code for jumps and immediates.
 * Full warnings for integer overflow.
 * NASM-like list format.
 * Most code licensed under 2-clause BSD license, although some portions are still LGPL-licensed (NASM preprocessor module).
 * Support for the -I option to specify include directories, with a search pattern essentially identical to most C compilers.
 * Support for CALL/JMP FAR, including proper handling of `location EQU seg:off`; `jmp location`.
 * Man pages: yasm(1), yasm_objfmts(7), yasm_dbgfmts(7), and yasm_arch(7).

Important Differences from NASM
===============================

 * A number of command line options are different. Run "yasm --help" for a quick command line option summary, or read the full yasm(1) manpage for detailed descriptions of all command line options.
 * Include files with relative paths are not searched in the same way.  Yasm's search behavior is essentially that of most C compilers.

Known Issues
============

As Yasm is still under development, there are some caveats and features that do not yet work or are not yet fully functional.  See the Tickets area of Yasm's website for a list of active issues.

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

Assemble test.asm to Win32 object file test.obj with CodeView 8.0 (VS2005) source debug info:

    yasm -f win32 -g cv8 test.asm

Assemble test2.asm to Win64 object file test.obj with CodeView 8.0 source debug info:

    yasm -f win64 -g cv8 test2.asm

Assemble test3.asm to AMD64 ELF object file test3.o with DWARF2 debugging information:

    yasm -f elf64 -g dwarf2 test3.asm

Alternative to above:

    yasm -f elf -m amd64 -g dwarf2 test3.asm

Assemble test4.s (GAS syntax file) to 32-bit x86 ELF object file testo.o with DWARF2 debugging information:

    yasm -p gas -f elf32 -g dwarf2 -o testo.o test4.s

