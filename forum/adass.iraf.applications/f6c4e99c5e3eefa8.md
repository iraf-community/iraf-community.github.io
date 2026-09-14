---
title: "Text-to-iraf conversion"
---

## Text-to-iraf conversion

**Lic. Mónica G. Grosso** wrote on Mar 16, 2000

<pre style="background: transparent; box-shadow: none; border: none;">
Hi!
      I was tryng to convert an ASCII file in IRAF image and I couldnï¿½t.
When I use the rtextimage task in dataio package I obtain an file.imh but I
can not display with splot the image.
I obtain a follow message:

error: MWCS: dimension mismatch (mw-open)

I do not understand what is the problem. My ASCII file have 2 columns
(wavelength and flux).
Please, may you help me or said something do you think that is happening??

Regards,
                    Monica


Lic. Mï¿½nica G. Grosso
CASLEO
Casilla de Correo 467
5400 San Juan- Argentina
phone: 0054 264 4213653
fax: 0054 264 4213693
</pre>

---

**Phil Hodge** wrote on Mar 16, 2000

<pre style="background: transparent; box-shadow: none; border: none;">
M���nica,

You can convert an ascii table to a multispec image in the following way.
Load the following packages:  stsdas (an external package), hst_calib,
and I presume you already have loaded noao and onedspec.  Suppose your
input ASCII file is called file.txt.  You can do the following:

	cl&gt; titable file.txt file.tab row=1
	cl&gt; tomultispec file.tab file.imh flux_col=c2 wave_col=c1
	cl&gt; delete file.tab	# this was a temporary file

Then file.imh will be in multispec format, and you can work on it with splot.
The above assumes that you have wavelengths in the first column and fluxes
in the second.  If they are reversed, use flux_col=c1 and wave_col=c2 when
you run tomultispec.

Phil

&gt; Hi!
&gt;       I was tryng to convert an ASCII file in IRAF image and I couldn���t.
&gt; When I use the rtextimage task in dataio package I obtain an file.imh but I
&gt; can not display with splot the image.
&gt; I obtain a follow message:
&gt;
&gt; error: MWCS: dimension mismatch (mw-open)
&gt;
&gt; I do not understand what is the problem. My ASCII file have 2 columns
&gt; (wavelength and flux).
&gt; Please, may you help me or said something do you think that is happening??
&gt;
&gt; Regards,
&gt;                     Monica
</pre>

---

**Olga Kuhn** wrote on Mar 16, 2000

<pre style="background: transparent; box-shadow: none; border: none;">


Hi,   I was wondering about this when the question on ascii to *.imh came
up ---

If the wavelengths read in from the ascii table are not equally spaced, 
will splot then be able to correctly compute line equivalent widths
or fluxes? (assuming no header information to give the dispersion)

   Thanks,
	Olga Kuhn

&gt; 
&gt; You can convert an ascii table to a multispec image in the following way.
&gt; Load the following packages:  stsdas (an external package), hst_calib,
&gt; and I presume you already have loaded noao and onedspec.  Suppose your
&gt; input ASCII file is called file.txt.  You can do the following:
&gt; 
&gt; 	cl&gt; titable file.txt file.tab row=1
&gt; 	cl&gt; tomultispec file.tab file.imh flux_col=c2 wave_col=c1
&gt; 	cl&gt; delete file.tab	# this was a temporary file
&gt; 
&gt; Then file.imh will be in multispec format, and you can work on it with splot.
&gt; The above assumes that you have wavelengths in the first column and fluxes
&gt; in the second.  If they are reversed, use flux_col=c1 and wave_col=c2 when
&gt; you run tomultispec.
&gt;
</pre>

---

**Rica S. French** wrote on Mar 16, 2000

<pre style="background: transparent; box-shadow: none; border: none;">
titable requires input already in stsdas tables format. you can create
a table from ascii using tcreate, but it might be simpler to use
rspectext to go straight from an ascii spectrum to an iraf image (if
this works for you).

[&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;][&lt;&gt;]

A bus station is where a bus stops. A train station is where a train
stops. On my desk I have a work station............. &lt;Steven Wright&gt;

Rica Sirbaugh French            rfrench@astro.as.utexas.edu
Department of Astronomy         http://physics.mtsu.edu/~sirbaugh/
University of Texas at Austin   OFC: 512.471.8443   RLM 16.212
Austin, TX 78712 USA            FAX: 512.471.6016

On Thu, 16 Mar 2000, Phil Hodge wrote:

&gt; M�nica,
&gt; 
&gt; You can convert an ascii table to a multispec image in the following way.
&gt; Load the following packages:  stsdas (an external package), hst_calib,
&gt; and I presume you already have loaded noao and onedspec.  Suppose your
&gt; input ASCII file is called file.txt.  You can do the following:
&gt; 
&gt; 	cl&gt; titable file.txt file.tab row=1
&gt; 	cl&gt; tomultispec file.tab file.imh flux_col=c2 wave_col=c1
&gt; 	cl&gt; delete file.tab	# this was a temporary file
&gt; 
&gt; Then file.imh will be in multispec format, and you can work on it with splot.
&gt; The above assumes that you have wavelengths in the first column and fluxes
&gt; in the second.  If they are reversed, use flux_col=c1 and wave_col=c2 when
&gt; you run tomultispec.
&gt; 
&gt; Phil
&gt; 
&gt; &gt; Hi!
&gt; &gt;       I was tryng to convert an ASCII file in IRAF image and I couldn�t.
&gt; &gt; When I use the rtextimage task in dataio package I obtain an file.imh but I
&gt; &gt; can not display with splot the image.
&gt; &gt; I obtain a follow message:
&gt; &gt;
&gt; &gt; error: MWCS: dimension mismatch (mw-open)
&gt; &gt;
&gt; &gt; I do not understand what is the problem. My ASCII file have 2 columns
&gt; &gt; (wavelength and flux).
&gt; &gt; Please, may you help me or said something do you think that is happening??
&gt; &gt;
&gt; &gt; Regards,
&gt; &gt;                     Monica
&gt;
</pre>

---

**Ludovic Murat** wrote on Mar 16, 2000

<pre style="background: transparent; box-shadow: none; border: none;">
Actually im not to sure ,,so I wont give you an answer that is incorrect
,,,so hows your day??/ 

	-----Original Message-----
	From:	irafmail-gateway@noao.edu [SMTP:irafmail-gateway@noao.edu]
	Sent:	Thursday, March 16, 2000 2:33 PM
	To:	lmurat@ubisoft.qc.ca
	Subject:	Re: Text-to-iraf conversion



	Hi,   I was wondering about this when the question on ascii to *.imh
came
	up ---

	If the wavelengths read in from the ascii table are not equally
spaced, 
	will splot then be able to correctly compute line equivalent widths
	or fluxes? (assuming no header information to give the dispersion)

	   Thanks,
		Olga Kuhn

	&gt; 
	&gt; You can convert an ascii table to a multispec image in the
following way.
	&gt; Load the following packages:  stsdas (an external package),
hst_calib,
	&gt; and I presume you already have loaded noao and onedspec.  Suppose
your
	&gt; input ASCII file is called file.txt.  You can do the following:
	&gt; 
	&gt; 	cl&gt; titable file.txt file.tab row=1
	&gt; 	cl&gt; tomultispec file.tab file.imh flux_col=c2 wave_col=c1
	&gt; 	cl&gt; delete file.tab	# this was a temporary file
	&gt; 
	&gt; Then file.imh will be in multispec format, and you can work on it
with splot.
	&gt; The above assumes that you have wavelengths in the first column
and fluxes
	&gt; in the second.  If they are reversed, use flux_col=c1 and
wave_col=c2 when
	&gt; you run tomultispec.
	&gt;
</pre>

---

**Phil Hodge** wrote on Mar 16, 2000

<pre style="background: transparent; box-shadow: none; border: none;">
&gt; titable requires input already in stsdas tables format.

No, the ttools tasks can read ascii text files.  The default column
names are c1, c2, c3, etc.  That&#x27;s why I specified the column names
for flux and wavelength as c2 and c1 respectively.

&gt; but it might be simpler to use
&gt; rspectext to go straight from an ascii spectrum to an iraf image (if
&gt; this works for you).

If there are not too many lines, that would indeed be simpler.  Using
tomultispec assumes that the wavelengths vary smoothly so they can be
fit using a polynomial.

Phil
</pre>

---

**Frank Valdes** wrote on Mar 16, 2000

<pre style="background: transparent; box-shadow: none; border: none;">
In addition to the STSDAS MKMULTISPEC method described by Phil there is
also the task RSPECTEXT in the ONEDSPEC package.  This works on just a
simple wavelength/pixel value ASCII file with an optional header.  You can
think of it as a  version of RTEXTIMAGE for spectra.  You can select
whether to define the linear wavelength scale, take the values from
FITS keyword type of header, or have it fit a dispersion function to
the lines.  The latter case does not require evenly spaced data and
functionally is pretty much like MKMULTISPEC.

It is easy to use and requires no intermediate files.  There is also
the reverse task called WSPECTEXT that creates a two column text file
of a spectrum in an image.

Frank Valdes
</pre>

---

**Frank Valdes** wrote on Mar 16, 2000

<pre style="background: transparent; box-shadow: none; border: none;">
&gt; If the wavelengths read in from the ascii table are not equally spaced, 
&gt; will splot then be able to correctly compute line equivalent widths
&gt; or fluxes? (assuming no header information to give the dispersion)

I forgot to add that once a spectrum is stored in an image, either
with mkmultispec or rspectext, and whether the pixels are spaced evenly
in wavelength with a linear dispersion function or unevenly with a non-linear
dispersion function, SPLOT will correctly measure equivalent widths, etc.

Frank Valdes
</pre>

---

*Last post on Mar 16, 2000*
