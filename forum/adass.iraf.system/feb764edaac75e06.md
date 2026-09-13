---
title: "Anyone try 2.11 under Solaris 7?"
---

# Anyone try 2.11 under Solaris 7?

**Eric Williams** wrote on Jan 19, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
We just bought a new Sun Ultra 5 that came preinstalled with Solaris 7.
I am wondering if anyone has tried compiling IRAF 2.11 on this new
version of Solaris? I would like to be able to keep the newest OS on the
machine if it will work. 

Eric Williams
eric@astro.wesleyan.edu
</pre>

---

**Ellyne Kinney** wrote on Jan 19, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
Hi Eric,

At STScI, we tested IRAF and TABLES/STSDAS v2.0.2 with Solaris 7
(I believe the machine was an Ultra 20).  We installed the 
packages from binaries and did a smoke test of both the 
STIS and NICMOS calibration pipelines.  They both worked
as expected.  We then tried recompiling TABLES and STSDAS 
with the SC5.0 compilers, which worked without warning messages.  
The smoke test was rerun and again, worked as expected.

We did not do any extensive testing of individual IRAF tasks.

If you do come across any problems with TABLES/STSDAS and
Solaris 7, please let us know.  The best way to contact us is
at help@stsci.edu.

Ellyne Kinney
STSDAS Administrator
</pre>

---

**Doug Tody** wrote on Jan 19, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
&gt; We just bought a new Sun Ultra 5 that came preinstalled with Solaris 7.
&gt; I am wondering if anyone has tried compiling IRAF 2.11 on this new
&gt; version of Solaris? I would like to be able to keep the newest OS on the
&gt; machine if it will work. 
&gt; 
&gt; Eric Williams
&gt; eric@astro.wesleyan.edu

Eric, we have been trying to get Solaris 7 in here at NOAO, but haven&#x27;t
received it from Sun yet.  As soon as we can we will install Solaris 7 on an
IRAF server and release a patch to support it.  Most likely the current IRAF
V2.11 binary release will run on Solaris 7, but we can&#x27;t say for sure as we
haven&#x27;t had a chance to test this yet.  We have no idea whether V2.11 will
compile on Solaris 7 without changes; usually some tweaking is needed.  Even
if this is not the case, provided old binaries will run under Solaris 7, one
could install IRAF and layered package built on some older Solaris system.

Note that Solaris 7, and to some extent Solaris 2.6, contain new 64 bit
system calls which complicate multiversion support.  In addition Solaris 7
includes new support for full 64 bit applications (int=32 bits, long and
pointer are 64 bits).  In general IRAF software built on one of the newer
versions of Solaris will NOT run on older versions.

Sorry we don&#x27;t have a better answer, but we will resolve this as soon as
we can get the software in here for testing.

	- Doug
</pre>

---

*Last post on Jan 19, 1999*
