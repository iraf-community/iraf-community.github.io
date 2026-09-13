---
title: "buglog.460: module = dispcor, author = valdes"
---

# buglog.460: module = dispcor, author = valdes

**Frank Valdes** wrote on Jan 27, 2000

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	460
MODULE:	dispcor
SYSTEM:	V2.11.3
DATE:	Thu Jan 27 13:07:38 MST 2000
FROM:	valdes

BUG:	In V2.11.3 DISPCOR was enhanced to work on 2D (long slit) data.
	In the processes the &quot;global&quot; option was broken resulting
	in a segmentation violation if selected.  There is no workaround
	other than not to use the global option and, instead, manually
	set the target dispersion sampling to be the same for all
	spectra.

STATUS:	Fixed for the next release.
</pre>

---

*Last post on Jan 27, 2000*
