---
title: License problems in IRAF
---


## Numerical Recipes

Up to version 2.16.1 (released 2013), IRAF contains a number of routines adopted from the book "Numerical Recipes in Fortran". The [FAQ of the NR book](http://www.nr.com/licenses/redistribute.html) about licensing says:
>*  [...] Can you include Numerical Recipes routines as part of that source code, including a notice that they are only allowed to be used with your application?
>      -  Sorry, no. We never give permission for Numerical Recipes source code to be posted on any public server, or distributed with any freeware or shareware package [...]
>* You want to translate some (or all) the Numerical Recipes routines to a different computer language, and then redistribute the resulting translations.
>     -  [...] However, you can't redistribute the translations in any manner, since they are "derivative works" and still subject to our copyright.

It [seems](https://iraf.net/forum/viewtopic.php?forum=4&showtopic=1468264) that IRAF was allowed to "use" this code as long as the following lines are included:
```
# Based on Numerical Recipes by Press, Flannery, Teukolsky, and Vetterling.
# Used by permission of the authors.
# Copyright(c) 1986 Numerical Recipes Software.
```

This looks however questionable here: First it says "used" and not "distribute" or "modify", which makes these files unsuitable for an Open Source project. It is also impossible to link these files with [GPL](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html) code (like `math/slalib/`) and redistribute the binaries, as it is done in the binary distributions of IRAF 2.16.1.

The following files are affected:

* [`pkg/xtools/numrecipes.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/pkg/xtools/numrecipes.x) _(Currently unused)_
  - `GAMMLN`: natural log of gamma function
  - `POIDEV`: Poisson deviates for a given mean
  - `GASDEV`:  normally distributed deviate of zero mean and unit var
  - `TWOFFT`: complex FFTs of two input real arrays
  - `REALFT`: FFT of a set of 2N real valued data points
  - `FOUR1`: forward or inverse FFT of the input array
  - `LUDCMP`: LU decomposition of a square matrix
  - `LUBKSB`: backsubstitution to solve a system
* [`noao/onedspec/splot/spdeblend.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/noao/onedspec/splot/spdeblend.x)
  - `GASDEV`:  normally distributed deviate of zero mean and unit var
* [`noao/rv/numrep.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/noao/rv/numrep.x)
  - `FOUR1`: forward or inverse FFT of the input array
  - `REALFT`: FFT of a set of 2N real valued data points
  - `TWOFFT`: complex FFTs of two input real arrays
* [`noao/artdata/numrecipes.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/noao/artdata/numrecipes.x)
  - `GAMMLN`: natural log of gamma function
  - `POIDEV`: Poisson deviates for a given mean
  - `GASDEV`:  normally distributed deviate of zero mean and unit var
* [`noao/imred/ccdred/ccdtest/t_mkimage.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/noao/imred/ccdred/ccdtest/t_mkimage.x#L174-L204)
   - `MKSIGMA`: Sequence of random numbers of the specified sigma
* [`sys/mwcs/mwlu.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/sys/mwcs/mwlu.x) _(no NR copyright statement)_
  - `MW_LUDECOMPOSE`: LU decomposition of a square matrix
  - `MW_LUBACKSUB`: backsubstitution to solve a system
* `pkg/utilities/nttools/stxtools/` _(no NR copyright statement)_
  - [`ludcmd.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/pkg/utilities/nttools/stxtools/ludcmd.x) `ludcmd`: lower-upper decomposition
  - [`ludcmp.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/pkg/utilities/nttools/stxtools/ludcmp.x) `ludcmp`: lower-upper decomposition
  - [`lubksd.f`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/pkg/utilities/nttools/stxtools/lubksd.f) `LUBKSD`: Solves a matrix equation AX = B
  - [`lubksb.f`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/pkg/utilities/nttools/stxtools/lubksb.f) `LUBKSB`: Solves a matrix equation AX = B
  - [`savgol.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/pkg/utilities/nttools/stxtools/savgol.x) `SAVGOL`:   Savitzky-Golay filtering
* [`noao/astutil/asttools/asttimes.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/noao/astutil/asttools/asttimes.x) _(no NR copyright statement)_
  - `AST_JULDAY_TO_DATE`: Convert Julian date to calendar date
* `noao/digiphot/daophot/daolib/` _(no NR copyright statement)_
  - [`daoran.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/noao/digiphot/daophot/daolib/daoran.x) `DAORAN`: random number generator RAN2
  - [`ran3.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/noao/digiphot/daophot/daolib/ran3.x) `RAN3`: uniform random deviate between 0.0 and 1.0
* [`noao/imred/vtel/mrqmin.x`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/noao/imred/vtel/mrqmin.x) _(no NR copyright statement)_
  - `MRQMIN`: Levenberg-Marquard nonlinear chi square minimization
  - `MRQCOF`: Evaluate linearized matrix coefficients
  - `GAUSSJ`: Linear equation solution by Gauss-Jordan elimination
  - `COVSRT`: Sort covariance matrix
* `pkg/utilities/nttools/trebin/` _(no NR copyright statement)_
  - [`tucspl.f`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/pkg/utilities/nttools/trebin/tucspl.f) `tucspl`: copied from Numerical Recipes SPLINE
  - [`tuispl.f`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/pkg/utilities/nttools/trebin/tuispl.f) `tuispl`: copied from Numerical Recipes SPLINT
  - [`tuiep3.f`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/pkg/utilities/nttools/trebin/tuiep3.f) `tuiep3`: copied from Numerical Recipes POLINT
  - [`tuhunt.f`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/pkg/utilities/nttools/trebin/tuhunt.f) `tuhunt`: copied from Numerical Recipes HUNT
 * [`vendor/cfitsio/eval.y`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/vendor/cfitsio/eval.y), [`vendor/cfitsio/eval_y.c`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/vendor/cfitsio/eval_y.c) _(no NR copyright statement)_
   - `gammln`: natural log of gamma function
   - `poidev`: Poisson deviates for a given mean
   - `gasdev`:  normally distributed deviate of zero mean and unit var

This problem was reported as issue [#21](https://iraf-community.github.io/iraf-v216/issues/21) and resolved in pull request [#37](https://iraf-community.github.io/iraf-v216/issues/37) in the github repository iraf/iraf-v216.

_**All Numerical Recipes code is removed and replaced by free code in the community distribution of IRAF.**_

## Code taken from the iraf64 project

The IRAF versions with 64 bit support include code taken from the [IRAF64 project](https://www.ir.isas.jaxa.jp/~cyamauch/iraf64/index.html), without acknowledging the author, and by violating the [license conditions](https://sourceforge.net/p/iraf64/code/HEAD/tree/trunk/src/LICENCE_IRAF64):
```
See COPYRIGHTS file for original IRAF.

Do not remove CREDITS_IRAF64 and LICENCE_IRAF64 from IRAF package.

Please display following message when starting IRAF shells;

  This product includes results achieved by the IRAF64 project in 2006-
  2009 directed by Chisato Yamauchi (C-SODA/ISAS/JAXA).
```
So far, the following files are found to be affected:

* [`sys/osb/i32to64.c`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/sys/osb/i32to64.c)
* [`sys/osb/i64to32.c`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/sys/osb/i64to32.c)
* [`unix/as.linux64/zsvjmp.s`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/unix/as.linux64/zsvjmp.s)
* [`unix/as.macintel/zsvjmp.s`](https://github.com/iraf-community/iraf/blob/9590f45760a4791f3305407fb51c87f1282b32be/unix/as.macintel/zsvjmp.s)

This was reported as issue
[#92](https://iraf-community.github.io/iraf-v216/issues/92) and
resolved with pull request
[#125](https://iraf-community.github.io/iraf-v216/issues/125) in the
github repository iraf/iraf-v216.

_**The community distribution of IRAF correctly acknowledges the contributions of the IRAF64 project.**_

## Code adapted from Berkeley UNIX

The directory
[`unix/os/net`](https://github.com/iraf-community/iraf/tree/3eea23e7ece09523d3770ab6b227be69d8924947/unix/os/net)
contains code that is not Open Source, as documented in its
[README](https://github.com/iraf-community/iraf/tree/3eea23e7ece09523d3770ab6b227be69d8924947/unix/os/net):

> NOTE -- This directory contains software which is adapted from the
  Berkeley UNIX networking software, hence a UNIX source license is
  required to use this software. […]

Although this code is present until version 2.16.1, it is unused and
removed in pull request [#274](https://github.com/iraf-community/iraf/pull/274).

_**This directory is removed from the community distribution of IRAF.**_
