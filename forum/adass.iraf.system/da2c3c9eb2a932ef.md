---
title: "mkimage and imdebug in 2.11 ??"
---

## mkimage and imdebug in 2.11 ??

**Mike Fitzpatrick** wrote on Aug 13, 1998

<pre style="background: transparent; box-shadow: none; border: none;">
&gt; Then we upgraded to Iraf 2.11 and I found that it yells at me saying that
&gt; &quot;imdebug&quot; amd &quot;mkimage&quot; tasks (that I am using in the script) are not
&gt; found. Could someone, please, explain what happened to those tasks in 2.11
&gt; and it they disappeared to the blue, which ones I should use instead.

	The IMDEBUG package was an ad hoc and rarely used set of tasks
written in the early days of the IMAGES package that was removed in V2.11.
The only really useful task it had was MKIMAGE, which has been supplanted
by the MKPATTERN task in the ARTDATA package and which is what you should
be using now.

Cheers,
-Mike
</pre>

---

**Sergei O. Naoumov** wrote on Aug 14, 1998

<pre style="background: transparent; box-shadow: none; border: none;">
Once at a time Mike Fitzpatrick &lt;fitz@tucana.tuc.noao.edu&gt; wrote:
&gt;&gt; &quot;imdebug&quot; amd &quot;mkimage&quot; tasks (that I am using in the script) are not

MF&gt; 	The IMDEBUG package was an ad hoc and rarely used set of tasks
MF&gt; written in the early days of the IMAGES package that was removed in V2.11.
MF&gt; The only really useful task it had was MKIMAGE, which has been supplanted
MF&gt; by the MKPATTERN task in the ARTDATA package and which is what you should
MF&gt; be using now.

Well, I kinda went around it with imslice+imtile tasks. It took much
longer to do what I needed but it finally worked.

	Sergei
</pre>

---

*Last post on Aug 14, 1998*
