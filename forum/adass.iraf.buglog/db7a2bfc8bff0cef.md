---
title: "buglog.411: module = imutil.imarith, author = davis"
---

# buglog.411: module = imutil.imarith, author = davis

**Lindsey Davis** wrote on Sep 16, 1998

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	411
MODULE:	imutil.imarith
SYSTEM:	V2.11
DATE:	Wed Sep 16 08:44:02 MST 1998
FROM:	davis

BUG:	Imarith fails with a segmentation violation if the noact parameter
	is set to &quot;yes&quot;. The bug was occurring because the code was trying
	to update the header of a non- existent output image.

STATUS:	Fixed for the next release of IRAF. There is no workaround.
</pre>

---

*Last post on Sep 16, 1998*
