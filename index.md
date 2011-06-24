---
title: Home
layout: default
---

The Yasm Modular Assembler Project
==================================

**Yasm** is a complete rewrite of the [NASM assembler](http://nasm.sf.net/) under the ["new" BSD License]({{site.git}}/BSD.txt) (some portions are under other licenses, see [COPYING]({{site.git}}/COPYING) for details).

Yasm currently supports the x86 and AMD64 instruction sets, accepts NASM and GAS assembler syntaxes, outputs binary, ELF32, ELF64, 32 and 64-bit Mach-O, RDOFF2, COFF, Win32, and Win64 object formats, and generates source debugging information in STABS, DWARF 2, and CodeView 8 formats.

Yasm can be easily integrated into Visual Studio [2005/2008]({{site.wiki}}/VisualStudio2005) and [2010]({{site.manual}}/vsyasm.html) for assembly of NASM or GAS syntax code into Win32 or Win64 object files.

Key Current User-Visible Features
---------------------------------

* Nearly feature-complete lexing and parsing of [NASM syntax]({{site.wiki}}/NasmSyntax).
* Basic support for [TASM syntax]({{site.wiki}}/TasmSyntax).
* Nearly feature-complete lexing and parsing of [GAS (GNU assembler) syntax]({{site.wiki}}/GasSyntax).
* [AMD64]({{site.wiki}}/AMD64) support (enabled using "BITS 64", "-m amd64", or selecting an explicitly 64-bit object format output such as "-f win64" or "-f elf64")
* 64-bit (and larger) integer constants allowed (including math operations).
* A fast jump size optimizer equivalent to or better than other assemblers' multi-pass optimizers.
* Support for multiple object formats:
   * [Binary object file]({{site.wiki}}/BinaryObject) output (NASM style).
   * [COFF object file]({{site.wiki}}/CoffObject) output, for use with DJGPP.
   * [Win32 object file]({{site.wiki}}/Win32Object) output.
   * [Win64/AMD64 aka "x64" object file]({{site.wiki}}/Win64Object) output
     (supports [structured exception handling]({{site.manual}}/objfmt-win64-exception.html)).
   * [RDOFF2 object file]({{site.wiki}}/RdfObject) output.
   * [ELF32 and ELF64 object file]({{site.wiki}}/ElfObject) output.
   * [32 and 64-bit Mach-O object file]({{site.wiki}}/MachObject) output.
* [STABS]({{site.wiki}}/StabsDebug), [DWARF2]({{site.wiki}}/Dwarf2Debug), and [CodeView]({{site.wiki}}/CodeViewDebug) debug formats.
* Portability; currently compilable on:
   * UNIX and compatibles (32-bit and 64-bit FreeBSD and Linux tested, GNU configure based autoconfiguration)
   * DOS (using [DJGPP](http://www.delorie.com/djgpp/))
   * Windows (using [Visual C++](http://msdn.microsoft.com/vstudio/) or [CygWin](http://www.cygwin.com/)).
* Internationalization support via [GNU gettext](http://www.gnu.org/software/gettext/gettext.html).

Key Internal Features
---------------------

The core focus of **Yasm** is not the *yasm* commandline frontend; rather, it is the [Libyasm]({{site.wiki}}/Libyasm) library and associated [loadable modules]({{site.wiki}}/LoadableModules) (see the [programmer references]({{site.wiki}}/ProgrammerReferences) for documentation).  Libyasm and the modules are intended for reuse in other sorts of programs dealing with code at the assembly level (compilers, debuggers, etc). Someday, libyasm may be packaged separately from the rest of **Yasm**.

* A NASM syntax and GAS syntax recursive-descent parser.

* Architecture-specific instruction parsers hand-written for simplicity and size, as well as to make it easy to add additional architectures while retaining the same front-end syntax. The blend of recursive descent for syntax and a hand-written parser for instructions strikes a great balance between the strengths and weaknesses of each approach.

* A [NASM syntax]({{site.wiki}}/NasmSyntax) lexer written in re2c. A highly efficient scanner generator (almost always faster than lex/flex), it's also very embeddable due to its code generation methodology, allowing a number of re2c scanners to be used in various places in yasm without any worries about naming conflicts.

* A [GAS syntax]({{site.wiki}}/GasSyntax) lexer written in re2c.

* Many of the modular interfaces at least superficially finished. This is still an area that needs a lot of work.

* A small set of portable equivalents of useful functions that are standard on some systems (detected via configure), such as the [queue(3)](http://www.freebsd.org/cgi/man.cgi?query=queue&sektion=3) set of functions, strdup, [strcasecmp](http://www.freebsd.org/cgi/man.cgi?query=strcasecmp&sektion=3), and [mergesort](http://www.freebsd.org/cgi/man.cgi?query=mergesort&sektion=3).

* A decent (and growing) set of assembler test input files to test the entire assembler as well as specific modules. 

