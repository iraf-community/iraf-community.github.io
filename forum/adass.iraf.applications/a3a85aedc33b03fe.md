---
title: "HEDIT, ASTHEDIT: dealing with sexigesimal numbers"
---

# HEDIT, ASTHEDIT: dealing with sexigesimal numbers

**Frank Valdes** wrote on Aug 11, 1998

<pre style="background: transparent; box-shadow: none; border: none;">
Q:  I have a header which has RA and ST information as sexigesimal. I
want to form the HA as (ST-RA). I can&#x27;t figure out how to get hedit to
do this. The command

hedit test ha &#x27;(st - ra)&#x27; add+

complains that the ST and RA are strings and not numbers. I don&#x27;t see
a function in the hedit help file that will convert the ST and RA from
strings in hh:mm:ss form into real format.

Is there an easy way of doing this?


A:  This is an old misfeature.  The function evaluation should convert
sexigesimal numbers automatically (as it does in other parts of IRAF)
but even if not the function &quot;real&quot; should do it.  The only reason
the numbers are strings is because they have to be represented as
strings in FITS.

The standard trick is to first create dummy keywords as real values,
copy the string values to those keywords, then do your operation.  A
sequence would be:

	cl&gt; hedit obj228 streal 1. add+
	cl&gt; hedit obj228 rareal 1. add+
	cl&gt; hedit obj228 streal &#x27;(st)&#x27;
	cl&gt; hedit obj228 rareal &#x27;(ra)&#x27;
	cl&gt; hedit obj228 ha &#x27;(streal-rareal)&#x27; add+
	cl&gt; hedit obj228 streal,rareal del+
	
You can also use astutil.asthedit interactively or with a command file.
Interactively it would be:

as&gt; asthedit obj228 &quot;&quot;
asthedit&gt; ha=st-ra
asthedit&gt; quit
</pre>

---

*Last post on Aug 11, 1998*
