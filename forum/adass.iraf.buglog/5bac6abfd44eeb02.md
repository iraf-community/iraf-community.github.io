---
title: "buglog.428: module = display, author = valdes"
---

# buglog.428: module = display, author = valdes

**Frank Valdes** wrote on Jun 15, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	428
MODULE:	display
SYSTEM:	V2.11-V2.11.1
DATE:	Tue Jun 15 10:00:10 MST 1999
FROM:	valdes

BUG:    For large images when the fill option is used, bad pixel overlays
	do not work correctly.  The image data or bad pixel masks will
	appear scrunched up and the image data may appear streaked as the
	last line is replicated from the scrunched edge to the edge of the
	display.  The behavior depends on whether the overlay mask is given
	in the &quot;overlay&quot; parameter or in the &quot;bpmask&quot; parameter with
	&quot;bpdisplay=overlay&quot;.  There is no workaround other than to avoid
	the fill option until the next release.

STATUS:	Fixed for the next release.
</pre>

---

*Last post on Jun 15, 1999*
