---
title: "helplog.12: cosmic rays, crutil"
---

## helplog.12: cosmic rays, crutil

**Frank Valdes** wrote on Jan 21, 2005

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	12
KEYWORDS:	cosmic rays, crutil
DATE:	Fri Jan 21 11:38:07 MST 2005
FROM:	valdes

Q:	Last year, Wojtek Pych (Copernicus Center, Poland; also Dunlap Obs.)
	published an interesting paper on a fast algorithm for CR removal
	from single CCD images, suited especially for 2-D spectral images
	(Pych, PASP 116, 148, 2004 Feb).  His C code is available at

	    http://www.camk.edu.pl/~pych/

	Do you by any chance know whether anyone has written an IRAF task
	that runs this code?  (I have asked Pych directly, who does not
	know of any such task.)

	If that hasn&#x27;t been done yet, I&#x27;ll try to have one written, since
	Pych&#x27;s code seems to be very efficient and good at CR removal from
	single 2-D spectra.

A:	I am not aware of anyone that has implemented this in an IRAF task.
	I just quickly read the paper and the method is simple enough that
	it should not be hard, particularly with the code available.  It
	would be a interesting addition to the suite of tasks recently
	collected together in a CRUTIL package.
</pre>

---

*Last post on Jan 21, 2005*
