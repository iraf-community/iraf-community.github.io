---
title: External packages
---

## External IRAF packages

Several external packages are maintained in repositories within the
iraf-community organization on github:

* [ctio](https://github.com/iraf-community/iraf-ctio) -
  Tools for the Cerro Tololo Inter-American Observatory
* [fitsutil](https://github.com/iraf-community/iraf-fitsutil) -
  Utilities for single and multiple FITS files
* [mscred](https://github.com/iraf-community/iraf-mscred) -
  Mosaic CCD reduction package
* [nfextern](https://github.com/iraf-community/iraf-nfextern) -
  General IR reductions/NEWFIRM package 
* [sptable](https://github.com/iraf-community/iraf-sptable) -
  IRAF package for tabular spectra
* [vo](https://github.com/iraf-community/iraf-vo) -
  Virtual Observatory package and vocl from the NOAO v2.16.1 release
* [xdimsum](https://github.com/iraf-community/iraf-xdimsum) -
   Deep Infrared Mosaicing Software

The documentation of many external packages is availale on [Read the
Docs](https://iraf.readthedocs.io/en/latest/tasks/external/index.html).

Please note that the repositories only contain the source code and often did
not receive an update yet. If there are more packages that should be
maintained in the repositories please contact us to get them included.

### IRAF packages from STScI

The STScI has developed a number of popular external packages for IRAF:

* *stsdas* - Software system for calibrating and analyzing data from the
  Hubble Space Telescope
* *tables* - Support of the TABLES format used by the STSDAS package
* *stecf* - IRAF tasks developed at the Space Telescope European Coordinating 
  Facility

Due to license restrictions (mainly the use of Numerical Recipes code)
the available source of these packages is not complete. They are also
not ported to 64 bit. As STScI is transitioning away from IRAF, this
is unlikely to change in the future. For reference, the free portion
is stored in a [Git repository](https://github.com/iraf-community/stsdas).

Parts of the TABLES package are however included as 
[NTTOOLS package](https://iraf.readthedocs.io/en/latest/tasks/utilities/nttools/index.html)
in the IRAF core.
