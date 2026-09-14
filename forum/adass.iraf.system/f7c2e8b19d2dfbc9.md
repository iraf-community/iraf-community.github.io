---
title: "IRAF under Red Hat 6.0 no go"
---

## IRAF under Red Hat 6.0 no go

**Tim Pickering** wrote on Apr 30, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
i corresponded with mike fitzpatrick about this, but thought i&#x27;d also
share it with the list.  after upgrading my systems to redhat 6.0 (i.e.
glibc 2.1), the redhat version of IRAF croaked and would die with
undefined reference errors.  cl.e is looking for some subroutine that
existed in glibc 2.0 and disappeared in 2.1. the workaround i used to
revive IRAF was to replace the redhat binaries with linux (i.e. libc5)
binaries.  this gets IRAF running, but breaks any ability to build my
own packages under IRAF. 

i&#x27;ve seen some mentions about an upcoming V2.11.2 patch in some previous
posts w.r.t. some f2c weirdness as well as solaris 7 support.  any
possibility glibc 2.1 support will also appear with that patch?

tim

-- 
+----------------------------------------------------------------------+
|  Tim Pickering                 |     Kapteyn Institute, Postbus 800 
|  
|  tim@astro.rug.nl              | 9700 AV Groningen, The Netherlands  |
|  http://www.astro.rug.nl/~tim/ |                    +31-50-363-6519  |
+----------------------------------------------------------------------+
The best thing about growing older is that it takes such a long time.
</pre>

---

**Doug Tody** wrote on Apr 30, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
Tim, we (Mike and I) are looking at this now to see if a simple emergency
patch to support RedHat 6 is possible, since we have had a flurry of
inquiries about this in just the past several days.  We haven&#x27;t received
6.0 here yet, and to minimize disruption we have a policy of not messing
with these systems until it comes out on video (CD that is).  However one
of the early RH6.0 testers (Tony Ferro) happens to be accross the street
and has been kind enough to let us poke around on his system.  We should
have some sort of solution within a couple of days.  Within a few weeks
we will have RH6.0 installed on our RH system here as well.

The subroutine RH6.0 systems complain about is used to set up the IEEE
floating point handling and exceptions.  It is still present on RH6.0
systems, they are just being nasty and won&#x27;t let us call it any longer
(to be fair IRAF is guilty of an interface violation).  Unfortunately
there is no standard way to set up IEEE exception handling in C code,
which is what IRAF is to the host system.  On some systems we sometimes
even have to resort to assembler.

&gt; i corresponded with mike fitzpatrick about this, but thought i&#x27;d also
&gt; share it with the list.  after upgrading my systems to redhat 6.0 (i.e.
&gt; glibc 2.1), the redhat version of IRAF croaked and would die with
&gt; undefined reference errors.  cl.e is looking for some subroutine that
&gt; existed in glibc 2.0 and disappeared in 2.1. the workaround i used to
&gt; revive IRAF was to replace the redhat binaries with linux (i.e. libc5)
&gt; binaries.  this gets IRAF running, but breaks any ability to build my
&gt; own packages under IRAF. 
&gt; 
&gt; i&#x27;ve seen some mentions about an upcoming V2.11.2 patch in some previous
&gt; posts w.r.t. some f2c weirdness as well as solaris 7 support.  any
&gt; possibility glibc 2.1 support will also appear with that patch?

As you say the Slackware (&quot;linux&quot; architecture) binaries will run under
all recent Intel Linux versions since they are statically linked.
Compilation however requires full support which can only come from a
native, up to date port.  We don&#x27;t know yet whether patching the current
V2.11.1 IRAF release for RH6.0 will permit normal compilation within IRAF.
If there are problems, this may have to wait for the PC-IRAF upgrade.
Yes, glibc 2.1, or whatever the latest version is at the time, will be
supported in the next upgrade.

	- Doug
</pre>

---

**tim** wrote on May 02, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
thanks for clarifying things, doug.  hopefully patching for glibc 2.1
will be relatively straightforward.  

tim

-- 
+----------------------------------------------------------------------+
|  Tim Pickering                 |     Kapteyn Institute, Postbus 800 
|  
|  tim@astro.rug.nl              | 9700 AV Groningen, The Netherlands  |
|  http://www.astro.rug.nl/~tim/ |                    +31-50-363-6519  |
+----------------------------------------------------------------------+
Torque is cheap.
</pre>

---

**Doug Tody** wrote on May 23, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
Many people have installed the recently released RedHat 6.0 and have written
to us to complain that IRAF no longer runs.  Trying to execute any process
results in an immediate &quot;undefined symbol: __setfpucw&quot; error.

We looked into this initially hoping that there would be a quick fix, such
as patching libc.so, installing some compatibility libraries at the host
level, replacing the Linux loader, etc.  Unfortunately this proved to not
be possible.  Redhat 6.0 introduces the EGCS compilers, a major rewrite
of the GNU compilers, and a major new version of libc, glibc2.  glibc2 in
particular is a major rewrite of Unix standard i/o and, while the new
implementation is completely within the technical specification of Unix
stdio, it does things quite differently than most Unix stdio implementations,
and this broke some code in IRAF which has worked for a long time on a
lot of Unix platforms!  In any case, the changes to the system stdio
include files for glibc2 are major enough that any old dynamically linked
executables or i/o libraries will probably have to be recompiled (not just
IRAF programs).

Given this situation we decided to just go ahead and do a fresh port of
IRAF (the public V2.11.1 release) to RedHat 6.0.  We needed to do this
anyway soon to support the EGCS compilers and glibc2, which will appear
soon in other platforms.  In the process we fixed some old (fairly minor)
PC-IRAF problems, such as the &quot;f2c.h not found&quot; message sometimes seen
when compiling IRAF external packages.

The upgrade files will be found in the &quot;rhux-6.0&quot; subdirectory of the
V2.11 PCIX (PC-IRAF) distribution.

A full install is required to install the new version, since all the HSI
binaries (included in the AS distribution) were updated, as well as the
RedHat Linux (RHUX) BINs.  However, since the IRAF version has not changed
you can keep all your old local configuration files and move them into
the new system.  In other words, don&#x27;t merely update the &quot;bin.redhat&quot;
directories at $iraf and $iraf/noao!  You need to install the &quot;AS&quot; (all
sources) distribution as well to get the updated HSI binaries and related
HSI source changes.  If this is not clear, just follow the directions for
installing or updating IRAF as documented in the README and the installation
documentation.

This release should not be confused with the upcoming IRAF V2.11 patch
and PC-IRAF upgrade.  This will be a new version of IRAF.  It will support
RedHat 6.0 or later versions, but will be a major upgrade of IRAF itself
as well.  The current release is only for people installing RedHat Linux/IRAF
on a RedHat 6.0 system.  If you are running IRAF on a RedHat 5.2 or
earlier system, you do not need to upgrade.

An excerpt from the PC-IRAF README containing more detailed upgrade
information follows.

May 23 1999


--------- Excerpt from /iraf/v211/PCIX/README ---------

Sun May 23 1999 -- RedHat 6.0 Emergency Port
==========================================================

The recent (April/May 99) RedHat 6.0 release features new compilers and a
new version of the glibc libraries which broke the existing RHUX
distribution, which is linked shared (i.e. dynamically loads libc).  The
characteristic error is &quot;...undefined symbol: __setfpucw&quot; when trying to run
any IRAF executable linked under RedHat 5.X.  An emergency mini-port of
V2.11.1 system to RedHat 6.0 been done since the RedHat release of IRAF
would no longer run at all on this platform.

RedHat 6.0 users should follow the normal RHUX architecture installation
instructions, but download *all* distribution files from the &#x27;rhux-6.0&#x27;
subdirectory.  Specifically, the distribution is contained in the
following subdirectories:

    rhux-6.0/as.pcix.gen        PC-IRAF distribution for RedHat 6.0 systems
    rhux-6.0/ib.rhux.x86        Core IRAF binaries for RedHat 6.0 systems
    rhux-6.0/ib.rhux.x86        NOAO package binaries for RedHat 6.0 systems

A full installation will be required since the current HSI binaries (e.g.
the XC and MKPKG binaries used in compilation, SGI translators used for
hardcopy, etc) will not work under RedHat 6.   The IRAF version has not
changed, but some system files have been modified and everything has been
recompiled.  Local configuration files, including everything in DEV and
most things in HLIB, are unchanged and do not have to be diff/merged
(exceptions are irafuser.csh and f77.sh in HLIB, and hlib$libc/kernel.h,
which are not normally modified when the system is installed).

Anyone with problems or questions should feel free to contact site support
(iraf@noao.edu).
</pre>

---

*Last post on May 23, 1999*
