---
title: "SPLOT line fitting with fixed FWHM"
---

# SPLOT line fitting with fixed FWHM

**Frank Valdes** wrote on Jul 14, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
Q:  I am trying to make measurements of several absorption lines in several 
spectra.  I have been using the &quot;e&quot; and &quot;k&quot; cursor commands under splot 
and have been able to get the desired measurements; center, eqw, and 
FWHM.  I am now wanting to fix the FWHM at a certain value for all of the 
measurements and have been unable to find a task able to do this.  I am 
aware the the &quot;d&quot; command under splot is capable of holding the FWHM 
constant for all of the measurements of the lines, however it seems iraf 
is still in control of this parameter.  Thanks for the help.  


A:  The &quot;d&quot; option in SPLOT has an option for &quot;fixed&quot; sigmas.  As an example,
if there is a line near 4567.0 Angstroms and you want to fit a gaussian
constrained to a FWHM of 8.5 Angstroms, type the following into a text
file:

4567.0 INDEF g 8.5

Then mark the two sides of the line with the &quot;d&quot; key and use the &quot;f&quot;ile 
option and type in the name or your text file, then proceed through
the other options and select &quot;f&quot;ixed for the sigma width fitting.  The
other parameters can be constrained as well, or left free.  Many other
options are available, including fitting other profile types, deblending,
etc.  See the help page for more details, or write back if you have any
more questions.  You might also want to look at the FITPROFS task, which
can do the same types of line fitting as SPLOT, but is more suited for
automated fitting on many spectra.
(Answer by David Bell)
</pre>

---

*Last post on Jul 14, 1999*
