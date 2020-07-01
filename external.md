---
title: External packages
---

## External IRAF packages

Several external packages are maintained in repositories within the
iraf-community organization on github:

* [fitsutil](https://github.com/iraf-community/iraf-fitsutil) -
  Utilities for single and multiple FITS files
* [sptable](https://github.com/iraf-community/iraf-sptable) -
  IRAF package for tabular spectra
* [mscred](https://github.com/iraf-community/iraf-mscred) -
  Mosaic CCD reduction package
* [nfextern](https://github.com/iraf-community/iraf-nfextern) -
  General IR reductions/NEWFIRM package 
* [vo](https://github.com/iraf-community/iraf-vo) -
  Virtual Observatory package and vocl from the original v2.16.1 release
* [mscdb](https://github.com/iraf-community/iraf-mscdb) -
  MSCRED support files
* [xdimsum](https://github.com/iraf-community/iraf-xdimsum) -
  IR reductions
* [ucsclris](https://github.com/iraf-community/iraf-ucsclris) -
  UCSC LRIS mask making
* [guiapps](https://github.com/iraf-community/iraf-guiapps) -
  Prototype GUI application 
* [deitab](https://github.com/iraf-community/iraf-deitab) -
  DEIMOS tables package 
* [adccdrom](https://github.com/iraf-community/iraf-adccdrom) -
  Astronomical Data Center (ADC) CD-ROM tools
* [ctio](https://github.com/iraf-community/iraf-ctio) -
  Tools for the Cerro Tololo Inter-American Observatory

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
the source of these packages is not available anymore. They are also
not ported to 64 bit. As STScI is transitioning away from IRAF, this
is unlikely to change in the future.

Parts of the TABLES package are however included as NTTOOLS package in
the IRAF core.
