---
title: "buglog.472: module = mscred.ccdproc, author = valdes"
---

# buglog.472: module = mscred.ccdproc, author = valdes

**Frank Valdes** wrote on Oct 02, 2000

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	472
MODULE:	mscred.ccdproc
SYSTEM:	V4.0 - V4.1: September 20, 2000
DATE:	Mon Oct  2 10:27:34 MST 2000
FROM:	valdes

BUG:	When a dependent calibration exposure, one that is not being processed
	directly but needs to be processed to continue with the specified
	target exposure, is processed a query

	List of output bad pixel masks:

	is given.  The workaround is to respond with carriage return or
	the equivalent of a null string &quot;&quot;.  There will be two queries
	per calibration image.

STATUS:	Fixed in the V4.1: October 2, 2000 release.
</pre>

---

*Last post on Oct 02, 2000*
