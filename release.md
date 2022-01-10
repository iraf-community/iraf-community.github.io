---
title: IRAF 2.17 Release notes
---

[![GitHub release](https://img.shields.io/github/release/iraf-community/iraf.svg)](https://github.com/iraf-community/iraf/releases/latest)

## Release notes

The current IRAF version 2.17 is available from github at

[https://github.com/iraf-community/iraf/releases/latest/](https://github.com/iraf-community/iraf/releases/latest/)

Changes to the NOAO 2.16.1 sources include:

* __Community maintainance__

	IRAF is no longer maintained by NOAO, but by the community of
    volunteers. Contributions of bug fixes, documentation or
    improvements are welcome.

* __All known non-free code removed__

    Although IRAF 2.16.1 was claimed to be "free software", [it contained
    source code that is not freely distributable](iraf-v216/license-problems);
    namely code copied from the book ["Numerical Recipes in Fortran"](http://numerical.recipes/).
    This code is replaced with free equivalents. The IRAF community edition is
    [Open Source](https://opensource.org/docs/osd), and as such included in
    Debian.

* __IRAF ported to other architectures__

    IRAF is now ported to a number of little endian architectures
    (ARM, PowerPC, MIPS, x32, RISC-V64) and operating systems (GNU Hurd and
    FreeBSD). Specifically, the Mac M1 processor is supported now.

* __Major bug fixes__

  Many bugs of the 2.16.1 release are fixed. Some of he major ones are:
  
   - Linux systems crashed with "Out of memory" 
     ([2.12 release notes](https://github.com/iraf-community/iraf/blob/9590f4/doc/notes.v212#L1065-L1075))
   - `noao.digiphot.photcal.fitparams` failed with a segmentation
     fault on 64-bit systems
     ([iraf.net#1467834](https://iraf.net/forum/viewtopic.php?showtopic=1467834))
   - The system wide IRAF installation changed the permissions of
     `/tmp/`, creating a major security hole in the system
     ([iraf-v216#23](https://iraf-community.github.io/iraf-v216/issues/23))
   - On Linux systems, self-compiled tasks gave wrong results
     ([iraf.net#1467841](https://iraf.net/forum/viewtopic.php?showtopic=1467841))
   - On modern systems, background execution did not work
     ([iraf.net#1467431](https://iraf.net/forum/viewtopic.php?showtopic=1467431))
   - The original code produced errornous executables when build on
     Linux versions later than 2012. It also did not build from
     scratch, but required an already compiled IRAF version.

* __Simple CI test framework added__

    The tests are defined and documented in
    [MarkDown](https://github.com/iraf-community/iraf/blob/main/test/README.md)
    files. Tests are run with Github Actions on Linux and MacOS X platforms.

* __VO package and vocl removed__

    The VO package, and the vocl shell heavily depend on a number of
    Java jars, where the creation from sources is undocumented. The
    package also uses outdated VO standards. A discussion with Mike
    Fitzpatrick resulted in his plan to [move the VO functionality
    into an external package](iraf-v216/issues/90).
    Therefore, no attempt was put into getting these problems fixed,
    and the VO stuff was cut out.  The VOTable functionality, however,
    remains available

## Detailed list of changes

This list shows all pull requests that were merged since 2.16.1.

### Since 2.16.1+2021.06.14

* Consistently format doc/help examples
  ([#195](https://github.com/iraf-community/iraf/pull/195))
* Fix some HTML help output glitches
  ([#194](https://github.com/iraf-community/iraf/pull/194))
* Remove duplicate argument in call
  ([#189](https://github.com/iraf-community/iraf/pull/189))
* Revert corruption of unix/os/net/rexec.c file
  ([#180](https://github.com/iraf-community/iraf/pull/180))
* Force using POSIX shell in extpkg.cl script
  ([#179](https://github.com/iraf-community/iraf/pull/179))
* Support freeBSD variants
  ([#174](https://github.com/iraf-community/iraf/pull/174))
* Separate development (softools) packages
  ([#172](https://github.com/iraf-community/iraf/pull/172))
* Remove obsolete tasks and links to iraf.noao.edu
  ([#170](https://github.com/iraf-community/iraf/pull/170))


### Since 2.16.1+2018.11.01

 * Cleanup for unneeded and obsolete files
   ([#166](https://github.com/iraf-community/iraf/pull/166))
 * fix slalib bug in sla_EQEQX
   ([#160](https://github.com/iraf-community/iraf/pull/160))
 * Ignore existing iraf env var in ./install
   ([#157](https://github.com/iraf-community/iraf/pull/157))
 * Cleanup ecl and cl
   ([#156](https://github.com/iraf-community/iraf/pull/156))
 * Add macOS arm64 support
   ([#131](https://github.com/iraf-community/iraf/pull/131))
 * Replace hard-coded host$bin paths by IRAFPATH
   ([#128](https://github.com/iraf-community/iraf/pull/128))
 * Remove include/drvrsmem.h
   ([#126](https://github.com/iraf-community/iraf/pull/126))
 * Fix cpu_time calculation in unix/os/zgtime.c
   ([#118](https://github.com/iraf-community/iraf/pull/118),
    [#136](https://github.com/iraf-community/iraf/pull/136),
    [#173](https://github.com/iraf-community/iraf/pull/173))
 * Move zsvjmp assembler files to unix/os and merge them
   ([#117](https://github.com/iraf-community/iraf/pull/117))
 * Use PLT when calling sigsetjmp on i386
   ([#116](https://github.com/iraf-community/iraf/pull/116))
 * Adjust external licenses
   ([#115](https://github.com/iraf-community/iraf/pull/115))
 * Definitely use flex to generate `unix/generix/lexyy.c`
   ([#112](https://github.com/iraf-community/iraf/pull/112))
 * Avoid multiple definition of `errflag`
   ([#111](https://github.com/iraf-community/iraf/pull/111))
 * Enable the use of Public Domain Ratfor to process `.r` files
   ([#103](https://github.com/iraf-community/iraf/pull/103),
    [#171](https://github.com/iraf-community/iraf/pull/171))
 * Remove some C compiler warnings
   ([#97](https://github.com/iraf-community/iraf/pull/97))
 * Fix non-working fft841 code by replacing it
   ([#95](https://github.com/iraf-community/iraf/pull/95))
 * Add LAPACK license
   ([#88](https://github.com/iraf-community/iraf/pull/88))
 * Rename `mkfloat.sh` to `mkfloat`
   ([#87](https://github.com/iraf-community/iraf/pull/87))
 * Add support for the DEC Alpha processor
   ([#79](https://github.com/iraf-community/iraf/pull/79))
 * Fix and improve the shell scripts
   ([#75](https://github.com/iraf-community/iraf/pull/75),
    [#76](https://github.com/iraf-community/iraf/pull/76),
    [#77](https://github.com/iraf-community/iraf/pull/77),
    [#85](https://github.com/iraf-community/iraf/pull/85),
    [#86](https://github.com/iraf-community/iraf/pull/86),
    [#113](https://github.com/iraf-community/iraf/pull/113))


### Since 2.16.1+2018.06.15

* Add riscv64 support
  ([#72](https://github.com/iraf-community/iraf/pull/72))
* Fix buffer length in `urlget.x`
  ([#70](https://github.com/iraf-community/iraf/pull/70))
* Mention Chisato Yamauchi as copyright owner of the x86_64 `zsvjmp.s` code
  ([#67](https://github.com/iraf-community/iraf/pull/67))
* Adjust calling of nttools subdir in `pkg/utilities/mkpkg`
  ([#65](https://github.com/iraf-community/iraf/pull/65))
* Update and modernize top-level information files
  ([#64](https://github.com/iraf-community/iraf/pull/64),
   [#73](https://github.com/iraf-community/iraf/pull/73))
* Check for the existence of the `arch` variable before using it
  ([#63](https://github.com/iraf-community/iraf/pull/63))
* Improve prototyping in bootlib
  ([#62](https://github.com/iraf-community/iraf/pull/62))
* Appended `ZTTYSZ()` function to get width and height of terminal
  ([#58](https://github.com/iraf-community/iraf/pull/58))
* Replace readline library by libedit on macos
  ([#57](https://github.com/iraf-community/iraf/pull/57))
* Clean and fix shell scripts
  ([#50](https://github.com/iraf-community/iraf/pull/50),
   [#51](https://github.com/iraf-community/iraf/pull/51),
   [#53](https://github.com/iraf-community/iraf/pull/53),
   [#54](https://github.com/iraf-community/iraf/pull/54),
   [#55](https://github.com/iraf-community/iraf/pull/55),
   [#75](https://github.com/iraf-community/iraf/pull/75),
   [#76](https://github.com/iraf-community/iraf/pull/76),
   [#77](https://github.com/iraf-community/iraf/pull/77))
* Fix variable declaration in noao/obsutil/src/findgain.cl
  ([#47](https://github.com/iraf-community/iraf/pull/47))
* Remove unused empty files
  ([#45](https://github.com/iraf-community/iraf/pull/45))
* Add manpages
  ([#44](https://github.com/iraf-community/iraf/pull/44))
* Update cfitsio to 3.450
  ([#43](https://github.com/iraf-community/iraf/pull/43))
* votable: Fix data type of loop variable
  ([#41](https://github.com/iraf-community/iraf/pull/41))


### Since 2.16.1+2018.03.10

* Implement the 'apropos' command
  ([#37](https://github.com/iraf-community/iraf/pull/37))
* Don't check for updates
  ([#36](https://github.com/iraf-community/iraf/pull/36))
* Update cfitsio to 3.440
  ([#34](https://github.com/iraf-community/iraf/pull/34))
* Fix background execution in cl and ecl
  ([#32](https://github.com/iraf-community/iraf/pull/32))
* Port IRAF to several architectures
  ([#31](https://github.com/iraf-community/iraf/pull/31))
  

### Since 2.16.1+2018.02.04

(Pull Requests from
[iraf/iraf-v216](iraf-v216))

* Update cfitsio to 3.430
  ([#135](iraf-v216/issues/135))
* Fix off-by-one problem in xppcode.c
  ([#133](iraf-v216/issues/133))
* Remove files that were generated by `generic.e` or `xyacc.e`
  ([#132](iraf-v216/issues/132))

### Since 2.16.1+2017.12.28

(Pull Requests from
[iraf/iraf-v216](iraf-v216))

* Make photcal 64-bit capable
  ([#130](iraf-v216/issues/130))
* f2c: Fix allocated size of Dimblock
  ([#127](iraf-v216/issues/127))

### Since 2.16.1

(Pull Requests from
[iraf/iraf-v216](iraf-v216))

* Check filepointer for `NULL` in `envinit` before trying to close.
  ([#126](iraf-v216/issues/126))
* Add the required credits for the IRAF64 project.
  ([#125](iraf-v216/issues/125))
* Use `strncpy` and `snprintf` to fill file header in wtar
  ([#124](iraf-v216/issues/124))
* Specify explicit format for `fprintf()`
  ([#123](iraf-v216/issues/123))
* Limit number of `finfo` structs returned by `KI_ZFINFO` to `MAX_ARGS`
  ([#122](iraf-v216/issues/122))
* Fix `isalnum()` and friends for non-ascii values
  ([#121](iraf-v216/issues/121))
* Use curl in `pkgget`
  ([#115](iraf-v216/issues/115))
* Fix comparison for some optional command line arguments in xc
  ([#111](iraf-v216/issues/111))
* Add a trailing `\0` to the end of variable format strings in `pkg/tbtables/fitsio/`
  ([#110](iraf-v216/issues/110))
* Fix OS dirnames in `README`
  ([#108](iraf-v216/issues/108))
* Adjust f2c's internal `integer` size for ILP64
  ([#107](iraf-v216/issues/107))
* Replace `d1mach.f` and `r1mach.f` by C sources
  ([#106](iraf-v216/issues/106))
* Handle negative pointers in `sys/nmemio`
  ([#105](iraf-v216/issues/105))
* Remove all executables and binaries in `make src`
  ([#104](iraf-v216/issues/104))
* _[linux64]_ Correct underlines in `mem` symbol in `zsvjmp.s`
  ([#102](iraf-v216/issues/102))
* Correct string length of `baseurl` initialization in `chkupdate.x`
  ([#101](iraf-v216/issues/101))
* Fix segfault when opening a `STRING_FILE`
  ([#100](iraf-v216/issues/100))
* Fix statement order in `vfn_expand_ldir`
  ([#99](iraf-v216/issues/99))
* Fix linenumber generation with `xpp -x` (rpp and spp))
  ([#98](iraf-v216/issues/98))
* Fix template expansion in `generic.c`
  ([#94](iraf-v216/issues/94))
* Remove VO related packages and libraries
  ([#93](iraf-v216/issues/93),
* Initialize `oscwd` in `zglobl.c`
  ([#91](iraf-v216/issues/91))
* Check for identical addresses before `strcpy()` in `mkpkg/tok.c`
  ([#89](iraf-v216/issues/89))
* Fix type of arguments for several procedure calls
  ([#88](iraf-v216/issues/88))
* Bugfix for `unix/os/gmttolst.c` and `unix/zgmtco.c`
  ([#87](iraf-v216/issues/87))
* Fix location of `yaccpar.x`
  ([#84](iraf-v216/issues/84))
* _[macosx]_ Fix syntax error in `readline/mkpkg` on macosx
  ([#83](iraf-v216/issues/83))
* Remove absolute paths from header
  ([#82](iraf-v216/issues/82))
* Reverse the condition when iraf should be set
  ([#81](iraf-v216/issues/81))
* _[macosx]_ Fix MacOSX min version on `zsvjmp_i386.s`
  ([#80](iraf-v216/issues/80))
* Fix lex source files in xpp and generic
  ([#79](iraf-v216/issues/79))
* _[macintel]_ Replace `setpgrp(...)` with POSIX `setpgid()`
  ([#78](iraf-v216/issues/78))
* Avoid identical src/target in `strcpy()` when creating library names in xc
  ([#77](iraf-v216/issues/77))
* _[linux]_ Consequently add `-m32` flags if compiling for linux(32))
  ([#76](iraf-v216/issues/76))
* Convert to ANSI C to fix return types of functions in `memlog.c`
  ([#75](iraf-v216/issues/75))
* Limit entries in bitmask to 64 bit.
  ([#74](iraf-v216/issues/74))
* Accept zero date in archives
  ([#71](iraf-v216/issues/71))
* Fix computation of offset in memory allocation at 32 bit
  ([#67](iraf-v216/issues/67))
* Fix `ADDR_TO_LOC` for i386 (32 bit))
  ([#62](iraf-v216/issues/62))
* Fix declaration of `cdsmem` in rpp
  ([#60](iraf-v216/issues/60))
* Force iraf to align on 128-bit boundaries
  ([#57](iraf-v216/issues/57))
* Remove `curl/types.h` includes
  ([#51](iraf-v216/issues/51))
* Fixed spelling error, "the" not "teh".
  ([#47](iraf-v216/issues/47))
* _[linux64]_ Call the PLT for `__sigsetjmp` instead of calling directly
  ([#45](iraf-v216/issues/45))
* Removed an extra `linux64`
  ([#44](iraf-v216/issues/44))
* Build vendor libs before starting the `NOVOS` build
  ([#40](iraf-v216/issues/40))
* Fixed recursive error in definition of `LFLAGS`
  ([#39](iraf-v216/issues/39))
* Convert `mklibs` to `/bin/sh`
  ([#38](iraf-v216/issues/38))
* Replace or remove non-free code (Numerical Recipes etc.))
  ([#37](iraf-v216/issues/37))
* Add continious integration testing with travis-CI
  ([#36](iraf-v216/issues/36))
* Replace absolute symlinks in sys/osb by relative ones
  ([#33](iraf-v216/issues/33))
* Don't remove sticky bit from /tmp on install
  ([#24](iraf-v216/issues/24))
* Fix setting of non-default IRAF root
  ([#22](iraf-v216/issues/22))
* Clean up sources from unnecessary code
  ([#2](iraf-v216/issues/2),
  [#14](iraf-v216/issues/14),
  [#15](iraf-v216/issues/15),
  [#16](iraf-v216/issues/16),
  [#17](iraf-v216/issues/17),
  [#18](iraf-v216/issues/18),
  [#20](iraf-v216/issues/20),
  [#25](iraf-v216/issues/25),
  [#68](iraf-v216/issues/68),
  [#69](iraf-v216/issues/69),
  [#70](iraf-v216/issues/70),
  [#113](iraf-v216/issues/113),
  [#116](iraf-v216/issues/116),
  [#117](iraf-v216/issues/117))
  
