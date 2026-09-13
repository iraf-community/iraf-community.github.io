---
title: "buglog.452: module = mscred.msczero, author = valdes"
---

# buglog.452: module = mscred.msczero, author = valdes

**Frank Valdes** wrote on Dec 10, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	452
MODULE:	mscred.msczero
SYSTEM:	MSCRED V3.2.3 (releases between Nov 17 and Dec 2)
DATE:	Fri Dec 10 12:14:10 MST 1999
FROM:	valdes

BUG:	A change made to allow MSCZERO to work on single images, such as
	after resampling and stacking, introduced the error

	   Warning: MWCS: dimension mismatch (mw_open)

	when attempting to apply a zero point correction update.  While
	the message says warning actually the coordinate system is
	not updated at all.  There is no workaround and requires
	the package to be updated.

STATUS:	Fixed in the Dec. 10, 1999 release.
</pre>

---

*Last post on Dec 10, 1999*
