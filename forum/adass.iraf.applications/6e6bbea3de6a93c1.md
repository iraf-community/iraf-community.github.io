---
title: "helplog.18: photometry, DAOFIND, CENTERPARS"
---

# helplog.18: photometry, DAOFIND, CENTERPARS

**Frank Valdes** wrote on Feb 03, 2005

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	18
KEYWORDS:	photometry, DAOFIND, CENTERPARS
DATE:	Thu Feb  3 16:43:14 MST 2005
FROM:	valdes

Q:	We are doing variability photometry and occasionally get about
	700 CCD images per night.  I do the reductions in IRAF, and mostly
	it goes pretty quickly, except dealing with coordinate files.  Is
	there any way to specify the positions of the stars to do
	photometry on, so you don&#x27;t have to edit 700 coodrdinate files that
	come out of DAOFIND?  The drift of the objects during the night is
	fairly small, but not zero, but the fields are not crowded, so if
	there is so me way to define a coordinate box where DAOFIND looks,
	that would save alot of editing and messing around with S/N
	cutoffs, and max brightness levels to try and reduce the number of
	stars DAO finds to a manageable level.


A:	There is no need to use DAOFIND before every exposure when the
	images have only small shifts.  Once you have a list of pixel
	positions of the stars, say from DAOFIND, in one exposure all you
	should have to do is recenter the pixel coordinates for each
	exposure rather than &quot;find&quot; them again?  The DAO package photometry
	tools have options to center on the sources provided by the input
	coordinates.  The centering option would be controled by the
	CENTERPARS parameter set.  So consult the CENTERPARS help file.

	Centering works when the shifts are fairly small and the field is
	not too crowed.  The CENTERPARS options work within a box around
	the starting coordinate.  So the box should be big enough for the
	shift but not so big as to include another star within a couple of
	magnitudes fainter (very faint stars should not affect the
	centroid).
</pre>

---

*Last post on Feb 03, 2005*
