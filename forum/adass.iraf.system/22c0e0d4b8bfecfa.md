---
title: "Standalone fits <-> iraf"
---

# Standalone fits <-> iraf

**Mike Fitzpatrick** wrote on Mar 10, 1998

<pre style="background: transparent; box-shadow: none; border: none;">

&gt; Are there any stand-alone utilities that can cook a FITS file out of
&gt; an Iraf image and back?
	The traditional way to do this was with an IMFORT program using
some FITSIO library, I&#x27;m sure somebody has one but I don&#x27;t have the source.
Another approach now that V2.11 supports FITS as a native format is to
use the IMCOPY task in a standalone way, you do the conversion by spec-
ifying the image extension as &quot;.imh&quot; or &quot;.fits&quot;.  It only took a minute
to cook up the source for the by tweaking the IMCOPY task source, I&#x27;ve
put this in our /pub directory in iraf.noao.edu as t_imcopy.x.  
	To make use of it do the following:

1) Download the source file and on a machine of the same OS as the
   Enterprise server with IRAF V2.11 installed compile it as

	% xc -z -/Bstatic t_imcopy.x -o x_imcopy.e -lxtools

   The &#x27;-z&#x27; flag is needed to avoid using an iraf shared library, the
   &quot;-/Bstatic&quot; is needed to avoid system shared libs.

2) Move the x_imcopy.e binary to the target machine and make it executable.

3) On the target machine create an executable csh script like the
   following called &#x27;imcopy&#x27;:

    #!/bin/csh

    x_imcopy.e imcopy input=&quot;$1&quot; output=&quot;$2&quot;

4) To do the conversion use the new &#x27;imcopy&#x27; command as e.g.

    % imcopy foo.imh foo.fits		# convert IMH to FITS
    % imcopy foo.fits foo.imh		# convert FITS to IMH
    % imcopy @inlist @outlist		# use @-lists

    % foreach i (*.imh)			# copy all IMH files in the
    ?    imcopy $i $i:r.fits		# cwd to FITS files w/ same
    ? end				# root name

	You can do similar things with other IRAF tasks though perhaps not
quite as easily.  Making IRAF tasks executable in standalone mode is part
of the OpenIRAF project which will be addressed this year.
	Hope this helps.

-Mike
</pre>

---

**Doug Tody** wrote on Mar 10, 1998

<pre style="background: transparent; box-shadow: none; border: none;">

On Tue, 10 Mar 1998, Mike Fitzpatrick wrote:

&gt; &gt; Are there any stand-alone utilities that can cook a FITS file out of
&gt; &gt; an Iraf image and back?
&gt; 	The traditional way to do this was with an IMFORT program using
&gt; some FITSIO library, I&#x27;m sure somebody has one but I don&#x27;t have the source.
&gt; Another approach now that V2.11 supports FITS as a native format is to
&gt; use the IMCOPY task in a standalone way, you do the conversion by spec-
&gt; ifying the image extension as &quot;.imh&quot; or &quot;.fits&quot;.  It only took a minute
&gt; to cook up the source for the by tweaking the IMCOPY task source, I&#x27;ve
&gt; put this in our /pub directory in iraf.noao.edu as t_imcopy.x.  

I just checked with Mike about this, and what he did was extract the source
for the imcopy task into the above file, and supply instructions to link
it statically (under an existing iraf installation) to get a stand-alone
imcopy and image format conversion task.

This is what Sergei was asking for, but I just wanted to point out that
existing IRAF tasks like IMCOPY can always be called stand-alone.  You
don&#x27;t need the whole IRAF system, only the executable containing the
desired task, although if the executable is linked with the IRAF shared
image you would need that too.  In the case of IMCOPY, in a standard IRAF
installation you would call it as

	x_images.e imcopy &lt;params...&gt;

since the IMCOPY task is in the x_images.e executable, along with all the
other IMAGES package tasks.  The &quot;&lt;params...&gt;&quot; can go on the command line
or in a dparam-format file referenced as &quot;@&lt;parfile&gt;&quot;.

Another way to eliminate the shared image would be to link x_images.e (or
whatever) static, then you could run the executable stand-alone on any
host where IRAF is not installed.
</pre>

---

**Sergei Naumov** wrote on Mar 11, 1998

<pre style="background: transparent; box-shadow: none; border: none;">

Hi!
Are there any stand-alone utilities that can cook a FITS file out of am Iraf
image amd back? I need them because I want to run allframe tasks on a big
Ultra Enterprise machine, and I do not want to install Iraf there (too
much fuss and it is not needed, actually).

Thanks much,

		-- Sergei Naumov
	   	   serge@astro.unc.edu
</pre>

---

**Mike Fitzpatrick** wrote on Mar 11, 1998

<pre style="background: transparent; box-shadow: none; border: none;">


	Several issues came up with Sergei after my initial reply.  A 
binary for the imcopy executable is not in our /pub directory as 
x_imcopy.e.SSUN for sites which either don&#x27;t have V2.11 installed or
who have trouble compiling the task.
	Secondly, by default the task will put .pix files in the same
directory as the header file.  This can be changed by defining an &#x27;imdir&#x27;
environment variable as e.g.

	setenv imdir  /d1/user/pixels/		# trailing &#x27;/&#x27; required
	setenv imdir  HDR\$pixels/		# put in &#x27;pixels&#x27; subdir

Note that when using the HDR$ syntax the &#x27;$&#x27; character must be escaped
with a backslash.
	Lastly, on systems which don&#x27;t have IRAF installed at all you must
define the following environment variables in order for the task to run
and not complain about a missing /usr/include/iraf.h file:

	setenv iraf /iraf/iraf/
	setenv host /iraf/iraf/unix/
	setenv tmp  /tmp/

Note the trailing &#x27;/&#x27; on each path.  Aside from perhaps &#x27;tmp&#x27; these values
are never used so the path is arbitrary.  Please feel free to write back 
you still have problems or questions.

-Mike
</pre>

---

**Doug Mink** wrote on Mar 16, 1998

<pre style="background: transparent; box-shadow: none; border: none;">

I have a standalone C program, i2f, part of my WCSTools package,
which reads IRAF version 1 or 2 .imh files from either byte order
and writes FITS files.  I already had the code to read the IRAF
files--it&#x27;s in recent versions of SAOimage as well as WCSTools--
so I packaged it into a program.  Source code and documentation
are available at

http://tdc-www.harvard.edu/software/wcstools/

This code is independent of IRAF and is written entirely in C.

-Doug Mink
 Telescope Data Center
 Harvard-Smithsonian Center for Astrophysics
 Cambridge, Massachusetts
</pre>

---

*Last post on Mar 16, 1998*
