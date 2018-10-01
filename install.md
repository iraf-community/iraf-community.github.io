---
title: IRAF 2.16.1+ Installation Instructions
---

# Installation Instructions

## Distribution Files

The IRAF v2.16.1 snapshots are available from github at

[https://github.com/iraf-community/iraf/releases/latest/](https://github.com/iraf-community/iraf/releases/latest/)

The snapshot has the release date as a suffix in the version number
and in the file name.


## System Requirements and Dependencies

The distributed binaries require the readline or libedit, curl, and
expat libraries to be installed.

On Debian and its derivatives (Ubuntu, Mint, Devuan, Raspbian etc.):

    $ sudo apt install gcc make flex
    $ sudo apt install libcurl4-openssl-dev libexpat-dev libreadline-dev

On Fedora and its derivatives (Redhat, Scientific Linux etc.)

    $ sudo dnf install gcc make perl flex
    $ sudo dnf install libcurl-devel expat-devel readline-devel

On MacOS X, you need to have the XCode tools installed. If you
haven't, you can install them with:

    $ xcode-select --install

Click "Install" to download and install Xcode Command Line Tools.


## Unpack the IRAF Distribution

The source distribution file is built as a tarball with the package
name and version as base directory. Thus, distribution files can be
unpacked with the command

    $ tar zxf /<path>/iraf-2.16.1-2018.06.15.tar.gz
    $ cd iraf-2.16.1-2018.06.15/


## Build from Sources

In the source directory, execute the install script to create needed
links:

    $ ./install 		# execute the install script

Usually, you can everywhere use the default settings when asked from
the install script.  Configure the system for the proper architecture
and build:

    $ make <arch>
    $ make sysgen 2>&1 | tee build.log

For `<arch>`, use the proper IRAF architecture name:

`<arch>`   | Description
-----------|----------------
`linux64`  | Linux 64 bit
`linux`    | Linux 32 bit
`macintel` | Mac OS X 64 bit
`macosx`   | Mac OS X 32 bit (Intel)
`freebsd64`| FreeBSD 64 bit
`freebsd`  | FreeBSD 32 bit
`hurd`     | GNU HURD 32 bit

Note that the PowerPC architecture of MacOS X is not supported anymore.


## Test the Build

IRAF comes with a small set of basic tests to ensure that the build
works fine.  To execute the tests, run:

    $ ./test/run_tests

The details of the tests are described [here](https://github.com/iraf-community/iraf/blob/master/test/README.md)

