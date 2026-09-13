---
title: "buglog.441: module = utilities.curfit, author = cheselka"
---

# buglog.441: module = utilities.curfit, author = cheselka

**Matt Cheselka** wrote on Sep 21, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	441
MODULE:	utilities.curfit
SYSTEM:	V2.11.2 (only)
DATE:	Tue Sep 21 14:01:15 MST 1999
FROM:	cheselka

BUG:	If run in non-interactive mode (in scripts, for example), a
	segmentation fault occurs.

	A workaround is to run the task interactively, set the &#x27;cursor&#x27; 
	parameter to a disk file containing the command &#x27;q&#x27;, send graphics 
	output to dev$null, and the text output to a disk file.

	From the command line:

	cl&gt; curfit dev$pix inter+ cursor=quit_command &gt;G dev$null &gt;&amp; fit.info

	Or from a script:

	utilities.curfit (input=&quot;dev$pix&quot;, inter+, cursor=&quot;quit_command&quot;, \
		&gt;G &quot;dev$null&quot;, &gt;&amp; &quot;fit.info&quot;)

	The resulting file (fit.info) will have a single line of junk at
	the top of the file, but will otherwise contain the fit data.

STATUS:	Fixed for the next release.
</pre>

---

*Last post on Sep 21, 1999*
