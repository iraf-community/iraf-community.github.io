---
title: IRAF 2.16.1+ Installation Instructions
---

[![GitHub release](https://img.shields.io/github/release/iraf-community/iraf.svg)](https://github.com/iraf-community/iraf/releases/latest)

# Binary packages

On some systems, IRAF can be directly installed from the package
repositories:

 * Ubuntu 18.04 LTS and later,
 * Debian 10 "Buster" (also in Debian 9 "Stretch" [backports](https://backports.debian.org/)),
 * Mageia 6.1.

Packages for Fedora are currently in preparation. Please contact us if
you want to help packaging for macOS or other Linux versions.

# Installation from source

## Distribution Files

The IRAF v2.16.1 snapshots are available from github at

[https://github.com/iraf-community/iraf/releases/latest/](https://github.com/iraf-community/iraf/releases/latest/)

The snapshot has the release date as a suffix in the version number
and in the file name.


## System Requirements and Dependencies

Additionally to the tar file, a C compiler, the "make" program, flex, and some development packages are required.

On Debian and its derivatives (Ubuntu, Mint, Devuan, Raspbian etc.):

    $ sudo apt install libcurl4-openssl-dev libexpat-dev libreadline-dev
    $ sudo apt install gcc make flex

On Fedora and its derivatives (Redhat, Scientific Linux etc.)

    $ sudo dnf install libcurl-devel expat-devel readline-devel
    $ sudo dnf install gcc make perl flex

On MacOS X, you need to have the XCode tools installed to build from
source. If you haven't, you can install them with:

    $ xcode-select --install

Click "Install" to download and install Xcode Command Line Tools.


## Compile the Sources

The source distribution file is built as a tarball with the package
name and version as base directory. Thus, distribution files can be
unpacked with the command

    $ tar zxf /<path>/iraf-2.16.1-2018.11.01.tar.gz
    $ cd iraf-2.16.1-2018.11.01/

In the source directory, execute the install script to create needed
links:

    $ ./install 		# execute the install script

The script will prompt you for the path to the default image
directory, the cache directory and the binary files directory.
Usually, you can everywhere use the default settings when asked from
the install script. You will need to include the binary files
directory in your PATH before proceeding to the `<make>` step.
In BASH this can be done with the command:

    $ export PATH=/path/to/iraf/bin/:$PATH

where `</path/to/iraf/bin/>` is the binary files path specified to
the install script.

Now you can configure the system for the proper architecture and build:

    $ make <arch>
    $ make sysgen 2>&1 | tee build.log

For `<arch>`, use the proper IRAF architecture name:

`<arch>`   | Operating system | Supported CPU types
-----------|------------------|---------------------------------------
`linux64`  | Linux 64 bit     | x86_64, arm64, mips64, ppc64, riscv64
`linux`    | Linux 32 bit     | i386, x32, arm, mips
`macintel` | Mac OS X 64 bit  | x86_64
`macosx`   | Mac OS X 32 bit  | i386
`freebsd64`| FreeBSD 64 bit   | x86_64
`freebsd`  | FreeBSD 32 bit   | i386, arm
`hurd`     | GNU HURD 32 bit  | i386

Note that Cygwin and big endian architectures like macosx/ppc are not
supported anymore.


## Test the Build

IRAF comes with a small set of basic tests to ensure that the build
works fine.  To execute the tests, run:

    $ ./test/run_tests

The details of the tests are described [here](https://github.com/iraf-community/iraf/blob/master/test/README.md)

