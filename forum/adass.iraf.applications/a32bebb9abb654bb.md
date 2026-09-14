---
title: "Mosaic IMEDIT, MSCCMD, and replacing extensions in MEF files"
---

## Mosaic IMEDIT, MSCCMD, and replacing extensions in MEF files

**Frank Valdes** wrote on Jun 04, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
Q;  I&#x27;m in the midsts of reducing some Mosaic data.  Unfortunately on my sky
flats I didn&#x27;t move the telescope quite far enough and I now want to run
&quot;imedit&quot; to get rid of one bright residual star.  However, I am having a devil
of a time getting this to work:

msccmd &quot;imedit $input $output&quot;

fails. (I give it a new image name for output, but it complains that the
image already exists).

I did try imcopy skyflat.fits[2] testb.fits
imedit testb.fits testc.fits
imcopy testc.fits skyflat.fits[2]

and it SEEMED to sort of work, but in a most mysterious manner: if I then
do a 
mscdisplay skyflat.fits

the &quot;bad&quot; im2 shows up initially but after im8  is displayed, im2 is
then overwritten on the display with the edited image.  But needless to
say I&#x27;m terrified of trying to use this as a flat.

So, I guess two basic questions:
a) is there some simply way of getting &quot;imedit&quot; to work on a Mosaic image?
b) in general, how do I substitute a fixed imN into the Mosaic fits image?



A:  On first glance IMEDIT with MSCCMD
should work.  However, the way MSCCMD
works is by relying on tasks to attempt to write to the same output
name (once for each extension).  First it creates the global header and
then lets tasks append their output to the file.  The FITS kernel, as
setup in MSCRED, lets the task append to an existing file without an
error about the image existing.  Most tasks do not explicitly check
first but produce an error only when they actually try to write to the
output image.  IMEDIT does check because a user can spend significant
time editing in the temporary image buffer and then when quiting it
would be annoying to be told the output image exists and so can&#x27;t be
written to.  So MSCCMD does not work with this task because of this
feature; IMEDIT sees that the global header file exists and assumes the
output image already exists.

With Mosaic data unless the task works in-place it is hard to update a
single extension.  Your second attempt is bad.  In MSCRED the default
behavior for FITS data is that if you write to an existing image, such
as an IMCOPY, it appends an extension.  To get rid of the offending
extension requires either copying all the previous extensions to a new
file or use FXDEL in the FITSUTIL package; i.e. load FITSUTIL and use
the task in that package.

Ok, to do what you want proceed as you did before by copying out the
image you want to edit.  Then edit that image.  Then to replace
a file requires the following set of copy operations.

ms&gt; imcopy skyflat[0] newskyflat
ms&gt; imcopy skyflat[im1] newskyflat
ms&gt; imcopy testb newskyflat[im2]
ms&gt; imcopy skyflat[im3] newskyflat
    etc.
    
The first copy creates the global header.  The other copies append.
You need the [im2] on the output to get the extension name.

There are other ways that might work.  You could use the FXDEL and FXINSERT
commands from the FITSUTIL package.  The problem with FXINSERT is that
it does not set the extension name so then you would need an HEDIT.
The FITSUTIL tasks seem to require the .fits extension be explicit.

ms&gt; fxdelete skyflat.fits 2
ms&gt; fxinsert testb.fits skyflat.fits[1] &quot;&quot;
ms&gt; hedit skyflat[2] extname im2 add+

You could also do

ms&gt; fxdelete skyflat.fits 2
ms&gt; imcopy testb skyflat[im2]

However this would get the extensions in a different order.  In principle
the order does not matter other than possibly confusing you.  I have not
done much with the fxdel type of approach (the MSCRED scripts generally
build a new image from scratch each time as in the first method).

There probably is a need for an MSCREPLACE command that hides the mechanics
of the above.
</pre>

---

*Last post on Jun 04, 1999*
