---
title: "buglog.544: module = echelle.scombine, author = valdes"
---

# buglog.544: module = echelle.scombine, author = valdes

**Frank Valdes** wrote on Jan 19, 2005

<pre style="background: transparent; box-shadow: none; border: none;">
NUMBER:	544
MODULE:	echelle.scombine
SYSTEM:	V2.12.2
DATE:	Wed Jan 19 08:44:47 MST 2005
FROM:	valdes

BUG:	Changes to SCOMBINE in V2.12.2a made it a separate executable.  The
	ECHELLE package definitions, however, failed to be updated so when
	trying to run SCOMBINE from the echelle package the following error
	message is produced.

	    ERROR: task `scombine&#x27; has no param file

	The solution is editing the echelle$echelle.cl file so that it
	reads as shown below.  A simpler workaround is to load the onedspec
	package and run scombine from that package.

STATUS:	Fixed for the next release.

Modifications to echelle$echelle.cl:

...
task    continuum,
        deredden,
        dispcor,
        dopcor,
        ecidentify,
        ecreidentify,
        refspectra,
        sapertures,
        sarith,
        sflip,
        slist,
        specplot,
        specshift,
        splot           = &quot;onedspec$x_onedspec.e&quot;
task    scombine        = &quot;onedspec$scombine/x_scombine.e
...

Note that scombine has to be removed from the first block of task
definitions and added as a separate task statement.
</pre>

---

*Last post on Jan 19, 2005*
