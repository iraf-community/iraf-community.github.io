---
title: PyRAF -- Command language for IRAF based on Python
---

[![ascl:1207.011](https://img.shields.io/badge/ascl-1207.011-blue.svg?colorB=262255)](http://ascl.net/1207.011)
[![GitHub release](https://img.shields.io/github/release/iraf-community/pyraf.svg)](https://github.com/iraf-community/pyraf/releases/latest)
[![PyRAF CI test](https://github.com/iraf-community/pyraf/actions/workflows/citest.yml/badge.svg)](https://github.com/iraf-community/pyraf/actions)

# PyRAF

PyRAF is a command language for IRAF based on the Python scripting language
that can be used in place of the existing IRAF CL. It allows such things as
importing Python modules, starting in any directory, GUI parameter editing and
help. It can be importedinto Python allowing you to run IRAF commands from
within a larger script.

PyRAF was developed since 1999 at the Space Telescope Science Institute
(STScI). Development and Support were stopped in 2019. Further maintainance
will be in the framework of the IRAF Community.

## Contributing

The PyRAF package is maintained on
[Github](https://github.com/iraf-community/pyraf). The preferred way to report
a bug is to create a new issue on the [pyraf GitHub
issue](https://github.com/iraf-community/pyraf/issues) page.  To contribute
patches, we suggest to create a [pull request on
GitHub](https://github.com/iraf-community/pyraf/pulls).

## Installation

To install PyRAF, it is required to have both IRAF and
[Python](https://www.python.org) already installed. Both a
self-compiled and a binary IRAF package (f.e. in
[Ubuntu](https://www.ubuntu.com)) will work.

The IRAF installation should have a properly configured environment,
especially the `iraf` environment variable must be set to point to
the IRAF installation directory (i.e. to `/usr/lib/iraf/` on Ubuntu
or Debian systems). On multi-arch IRAF installations, the `IRAFARCH`
environment variable should specify the architecture to use. This is
usually already set during the IRAF installation procedure.

The minimal Python required for PyRAF is 3.6, but it is recommended to
use the latest available version. An installation in an virtual
environment like [venv](https://docs.python.org/3/library/venv.html)
or [conda](https://docs.conda.io/) is possible.

On some Linux distributions, PyRAF is readily available as a binary
package and can be installed with the package installer, like `sudo
apt install python3-pyraf` on Debian or Ubuntu. On all other systems,
the package can be installed via
[PyPI](https://pypi.org/project/pyraf) with the command `pip3 install
pyraf`. Note that if no binary installation is available on PyPI, the
package requires a compilation, so aside from pip3, the C compiler and
development libraries should be installed.

## Documentation

* Richard L. White & Perry Greenfield: [The PyRAF Tutorial](doc/pyraf_tutorial.pdf)
  (2002)
