---
title: "MKOBJECTS - magnitudes for objects given as image templates"
---

# MKOBJECTS - magnitudes for objects given as image templates

**Frank Valdes** wrote on Mar 19, 1998

<pre style="background: transparent; box-shadow: none; border: none;">

Q:  I am using the mkobject package in artdata, but there is one
point which I cannot figure out: if I am using another image (of an
extended object) as object template (i.e. as done for dev$pix in
example 6 of the mkobjects help page) how does the task compute the
flux scaling? Specifically, one has to specify, in the object list, a
magnitude, but what does this magnitude mean? How does the task know
which is the magnitude of the template image? Is it an &quot;integrated&quot;
magnitude? Does the magzero apply to both the template and the output
image?


A:  When you request an object with magnitude m the desired flux is
(ignoring exptime and distance scaling):

	target flux = 10 ** (-0.4 * (m - m0))

When the target object is created by interpolation and seeing
convolution to the desired scale the total integrated flux (over the
rectangular region of the template image) is computed.  The output
object to be added to the image is scaled by (target flux)/(integrated
flux of template).  So basically the object you get has an integrated
flux given by the target flux as specified by the magnitude relative to
the magnitude zero point.
</pre>

---

*Last post on Mar 19, 1998*
