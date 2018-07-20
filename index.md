---
title: IRAF community edition
---
## This is a draft!

IRAF is the Image Reduction and Analysis Facility, a general purpose software system for the reduction and analysis of astronomical data. IRAF was written by the National Optical Astronomy Observatories (NOAO) in Tucson, Arizona. However, development and maintenance of IRAF is discontinued since 2012. The  latest release had a large number of problems, including major license issues and security bugs.

To keep the software away from  bitrotting, and to fix bugs that are in the package despite (or because) of its age, the iraf-community works on integrating the available patches into the IRAF source code.

## IRAF snaphot release

![GitHub release](https://img.shields.io/github/release/iraf-community/iraf.svg)

The latest official IRAF release is 2.16.1 from March 2012. Our releases are snapshots based on the latest available source code. The snapshots are tagged with their release date in the version number. Changes to the original [2.16.1 sources](http://iraf.noao.edu/iraf/ftp/iraf/v216/PCIX/) (and upstreams [master branch](https://github.com/iraf/iraf-v216/tree/9590f45760a4791f3305407fb51c87f1282b32be)) include:

* __Fixes to build and run IRAF on non-historic platforms__
  The original code produced errornous executables when build on Linux versions later than 2012, due to some funny hacks in the IRAF code. It also did not build from scratch, but required an already compiled IRAF version. 

* __Major bug fixes__
  Many [bugs](https://github.com/iraf/iraf-v216/issues) of the 2.16.1 release are fixed. Some of he major ones are:
   - Linux systems crashed with "Out of memory" (13 year old bug; [2.12 release notes](https://github.com/iraf/iraf-v216/blob/9590f45760a4791f3305407fb51c87f1282b32be/doc/notes.v212#L1065-L1075))
   - `noao.digiphot.photcal.fitparams` failed with a segmentation fault on 64-bit systems ([iraf.net](http://iraf.net/forum/viewtopic.php?showtopic=1467834))
   - The system wide IRAF installation changed the permissions of `/tmp/`, creating a major security hole in the system (iraf/iraf-v216#23)
   - On Linux systems, self-compiled tasks gave wrong results ([iraf.net](http://iraf.net/forum/viewtopic.php?showtopic=1467841))
   - On modern systems, background execution did not work ([iraf.net](http://iraf.net/forum/viewtopic.php?showtopic=1467431))

* __All known non-free code removed__
    Although IRAF 2.16.1 was claimed to be "free software", it contained source code that is not freely distributable; namely code copied from the book ["Numerical Recipes in Fortran"](http://numerical.recipes/). This code is replaced with free equivalents.

* __VO package and vocl removed__
    The VO package, and the vocl shell heavily depend on a number of Java jars, where the creation from sources is undocumented. The package also uses outdated VO standards. A discussion with Mike Fitzpatrick resulted in his plan to [move the VO functionality into an external package](https://github.com/iraf/iraf-v216/issues/90#issuecomment-310968834). Therefore, no attempt was put into getting these problems fixed, and the VO stuff was cut out.
    The VOTable functionality, however, remains available

* __IRAF ported to other architectures__
    IRAF is now ported to a number of little endian architectures (ARM, PowerPC, MIPS, x32) and operating systems (GNU Hurd and FreeBSD).

* __Simple CI test framework added__
    The tests are defined and documented in [MarkDown](https://github.com/olebole/iraf-v216/blob/v2.16.1%2B2018.03.10/test/README.md) files. Tests are run on Travis CI on all supported platforms.

## Download and install IRAF

### IRAF packages

IRAF is distributed as packages for some major Linux systems:

* Ubuntu ships IRAF with 18.04 LTS Bionic Beaver

* Debian 10 Buster will come with IRAF

* An IRAF package for Fedora Linux is currently under review

On supported Ubuntu and Debian systems, IRAF can be installed with the package manager. From the command line, this can be done running the following command as root:

```
apt install iraf
```

### Binary and source tarballs

IRAF is currently distributed as a source tarball. From the next snapshot, binary tarballs will be distributed for 64 and 32 bin Linux and MacOS X systems with Intel compatible CPUs. All tarballs can be downloaded from the [release directory](https://github.com/iraf-community/iraf/releases/latest/).

After unpackaging the tarball into a separate subdirectory, follow the README to install the package.

## Development, Report bugs and Contribute

IRAF is developed in an open way in a [github repository](https://github.com/iraf-community/iraf). Join the development by contributing bug reports or bug fixes.

If you encounter something you believe to be a mistake, error, or bug, the best way to get it addressed is to report it on the [github issue tracker](https://github.com/iraf-community/iraf/issues). If you believe you know how to fix the problem, please consider [contributing](https://github.com/iraf-community/iraf/pulls)!
