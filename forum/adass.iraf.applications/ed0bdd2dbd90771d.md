---
title: "Using TELLURIC task"
---

# Using TELLURIC task

**Ernesto Barrera** wrote on Sep 08, 2002

<pre style="background: transparent; box-shadow: none; border: none;">

Hi all,


I&#x27;m reducing some spectra by using IRAF standard procedures as described
on helps and tutorials.
At this point, my spectra are wavelength corrected and flux/extinction
calibrated. Now I&#x27;d like to use
TELLURIC to remove the strong atmospheric features on the red end of
spectra.

TELLURIC scales and shift a almost featureless spectrum (typically B
spectral type) so that the target spectrum
can be divided by it to remove telluric bands. The original target flux
level is recovered by multiplying by the average
spectrum of the B star.

The problem here is that continuum shape for corrected spectrum is
changed drastically since TELLURIC only keep
the average flux level from uncorrected spectra and no attempt is made
to keep its spectral distribution.

I&#x27;ve tried to use a continuum-normalized spectrum of the B-Star as
calibration for TELLURIC but it didn&#x27;t work probably
due to negative ratio values introduced appeared on deep atmospheric
bands (near 7600 A).

As far as I know there is a lack of information on the help page of
TELLURIC since no comments are made on this
matter.

I&#x27;d be grateful if you could give me some hints about this.

P.S.: I&#x27;ve see that FIGARO uses a continuum normalized spectrum of
B-Star to perform telluric corrections so continuum
shape of target star is conserved, but I would like to be able to
complete the reduction process on IRAF instead of switching
to another software which i&#x27;m not so familiarized.....


Thanks in advance
Ernesto Barrera
</pre>

---

*Last post on Sep 08, 2002*
