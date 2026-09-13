---
title: "buglog.425: module = focas, author = valdes"
---

# buglog.425: module = focas, author = valdes

**Frank Valdes** wrote on May 21, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	425
MODULE:	focas
SYSTEM:	external package
DATE:	Fri May 21 10:28:59 MST 1999
FROM:	valdes

BUG:	The command FDISPLAY in the IRAF FOCAS external package fails to
	find the command.  There is an error in the focas.cl file which
	defines how FOCAS tasks are called by IRAF.

	Within IRAF the FOCAS display command was changed to be &quot;fdisplay&quot;
	to avoid conflict with the IRAF display command.  Initially this
	was done by translating the command FDISPLAY in IRAF to execute the
	command DISPLAY in Unix (which was the name of the executable).
	However, in Unix there was also a common conflict with another
	command having the name DISPLAY.  So the Makefile was modified to
	create an executable fdisplay (from the display.c source).  So now
	IRAF needs to call fdisplay in Unix when fdisplay is typed.

	The file focas.cl needs to be changed from

	    task $fdisplay = $display

	to

	    task $fdisplay = $foreign

	Bye out of the package and reload it after making the change to
	have it take effect.


STATUS:	Will be fixed in a future release.
</pre>

---

*Last post on May 21, 1999*
