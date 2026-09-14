---
title: "hselect"
---

## hselect

**Jim Lewis** wrote on Apr 09, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
Is there any way to use hselect to test for the non-presence of a header
item?

cheers, Jim Lewis
</pre>

---

**Lindsey Davis** wrote on Apr 09, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
Jim,

&gt;Is there any way to use hselect to test for the non-presence of a header
&gt;item?

Hselect does not provide a place holder capability. If you are testing for
a single header item then hselect will return an empty string if the
item is missing from the image header.  If you are testing for several
items then you can test whether the number returned is equal to the number
requested, but without additional information it is hard to do more.

Trying looking at the imgets and asthedit tasks. I suspect you might be
able to do what you want with these.



						 Lindsey
</pre>

---

**Phil Hodge** wrote on Apr 09, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
&gt;Is there any way to use hselect to test for the non-presence of a header
&gt;item?

Another possibility is to use keypar in the stsdas.ttools package.  keypar
has a &#x27;found&#x27; parameter which is set depending on whether the keyword was
found in the header.

Phil
</pre>

---

**Mike Fitzpatrick** wrote on Apr 09, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
	Also, see the HCHECK task in STSDAS.TOOLBOX.HEADERS, according to
the help page it should do just what you asked.

-Mike
</pre>

---

*Last post on Apr 09, 1999*
