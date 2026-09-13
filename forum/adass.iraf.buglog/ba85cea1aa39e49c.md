---
title: "buglog.445: module = ared.quad.quadproc, author = valdes"
---

# buglog.445: module = ared.quad.quadproc, author = valdes

**Frank Valdes** wrote on Oct 08, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	445
MODULE:	ared.quad.quadproc
SYSTEM:	V2.11.2
DATE:	Fri Oct  8 16:25:14 MST 1999
FROM:	valdes

BUG:	ARED external package versions prior to &quot;Rev 1.32 - Oct 8, 1999&quot;
	installed with IRAF V2.11.2 cause the QUADPROC task to produce
	the error:

	ERROR: parameter `output&#x27; not found
	    quadproc (images=tryme.fits)

	QUADPROC is a script that calls CCDPROC and the parameter &quot;output&quot;
	is a new parameter in that task.  Installation of ARED includes
	copying the CCDPROC executable but not the parameter file.
	The workaround is either to get the latest version of ARED or
	edit the file quad$ccdproc.par (quad is defined after loading
	the quad package) to add the line:

	output,s,h,&quot;&quot;,,,List of output CCD images

	after the first line.

STATUS:	ARED package updated to include the revised ccdproc.par file.
</pre>

---

*Last post on Oct 08, 1999*
