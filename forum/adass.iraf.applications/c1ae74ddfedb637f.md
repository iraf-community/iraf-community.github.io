---
title: "Ximtool and Saoimage on KDE (Linux)"
---

# Ximtool and Saoimage on KDE (Linux)

**Simon Anun** wrote on Apr 02, 2003

<pre style="background: transparent; box-shadow: none; border: none;">
On Wed, 2 Apr 2003, Simon Anun wrote:

 Helo:
        I have a problem with Ximtool and Saoimage on KDE. This image
 viwers do not work on KDE windows-manager, but on Gnome work fine.
        This problems was find on Redhat 7.1, Redhat 7.3, Mandrake 8.2...
        Can yuo help me to resolv this problem.
                     Sorry for my english.
 
                           Thank you very much 
 
 

 
##############################################################################

                         Simï¿½n Antonio Anï¿½n
                       anun@mail.oac.uncor.edu
                 Observatorio Astronï¿½mico de Cï¿½rdoba
                             Laprida 854
                        Tel: 0351-4331064/65
                         Fax : 0351-4331063
                               Cï¿½rdoba
                         Repï¿½blica Argentina

#############################################################################
</pre>

---

**Liliana Hernandez Cervantes** wrote on Apr 02, 2003

<pre style="background: transparent; box-shadow: none; border: none;">

Hi,

I am use ds9 for view images in kde.

 http://hea-www.harvard.edu/RD

Cheers

Liliana

On Wed, 2 Apr 2003, Simon Anun wrote:

&gt; On Wed, 2 Apr 2003, Simon Anun wrote:
&gt;
&gt;  Helo:
&gt;         I have a problem with Ximtool and Saoimage on KDE. This image
&gt;  viwers do not work on KDE windows-manager, but on Gnome work fine.
&gt;         This problems was find on Redhat 7.1, Redhat 7.3, Mandrake 8.2...
&gt;         Can yuo help me to resolv this problem.
&gt;                      Sorry for my english.
&gt;
&gt;                            Thank you very much
&gt;
&gt;
&gt;
&gt;
&gt; ##############################################################################
&gt;
&gt;                          Sim�n Antonio An�n
&gt;                        anun@mail.oac.uncor.edu
&gt;                  Observatorio Astron�mico de C�rdoba
&gt;                              Laprida 854
&gt;                         Tel: 0351-4331064/65
&gt;                          Fax : 0351-4331063
&gt;                                C�rdoba
&gt;                          Rep�blica Argentina
&gt;
&gt; #############################################################################
&gt;
</pre>

---

**Richard Hill** wrote on Apr 02, 2003

<pre style="background: transparent; box-shadow: none; border: none;">
On Wednesday 02 April 2003 12:11 pm, you wrote:
&gt; Hi,
&gt;
&gt; I am use ds9 for view images in kde.
&gt;
&gt;  http://hea-www.harvard.edu/RD
&gt;
&gt; Cheers
&gt;
&gt; Liliana
&gt;


We use this too and have run into a difficulty. We are using the DS9
in Linux Red Hat 7.3 and 8.0. We need to convert some of the
images and/or  portions of them, into JPEG format for inclusion
in HTML documents. Thus far I have had no success with the
Save Regions selection. Any suggestions how this might be
accomplished?

-Rik
</pre>

---

**Matthew Kenworthy** wrote on Apr 03, 2003

<pre style="background: transparent; box-shadow: none; border: none;">
&gt; We use this too and have run into a difficulty. We are using the DS9
&gt; in Linux Red Hat 7.3 and 8.0. We need to convert some of the
&gt; images and/or  portions of them, into JPEG format for inclusion
&gt; in HTML documents. Thus far I have had no success with the
&gt; Save Regions selection. Any suggestions how this might be
&gt; accomplished?

One option is to use GIMP to read in the FITS files, but I find the
colours tricky to match up after getting used to the colour/brightness
mouse action of DS9. Doing a conversion to a sensible log colour scaling
is not intuitive in GIMP.

An alternative I use is to do a screen grab using &#x27;xv&#x27;, and then save
that as a jpeg and trim it with other software. If you haven&#x27;t heard of
it, it&#x27;s an old but useful image capture and manipulation program:

http://www.trilon.com/xv/

This method is very kludgy, but it means you can capture *exactly* the
FITS image with the colour palette you want.

Matt

-- 
Dr. Matthew Kenworthy, Physics Department, University of Cincinnati,
Cincinnati, OH 45221, U.S.A.   vox:(513) 556-0542 fax:(513) 556-3425
</pre>

---

**Michael Koppelman** wrote on Apr 03, 2003

<pre style="background: transparent; box-shadow: none; border: none;">
Sometimes just using a screen grab program will get the job done. I run 
IRAF on Mac OS X, which has a great screen grab program called Grab.

Michael Koppelman
http://www.lolife.com/astronomy/

On Wednesday, April 2, 2003, at 11:58 PM, Richard Hill wrote:

&gt; We use this too and have run into a difficulty. We are using the DS9
&gt; in Linux Red Hat 7.3 and 8.0. We need to convert some of the
&gt; images and/or  portions of them, into JPEG format for inclusion
&gt; in HTML documents. Thus far I have had no success with the
&gt; Save Regions selection. Any suggestions how this might be
&gt; accomplished?
</pre>

---

**Shashikiran Ganesh** wrote on Apr 04, 2003

<pre style="background: transparent; box-shadow: none; border: none;">
On Wed, 2 Apr 2003, Richard Hill wrote:

&gt; We use this too and have run into a difficulty. We are using the DS9
&gt; in Linux Red Hat 7.3 and 8.0. We need to convert some of the
&gt; images and/or  portions of them, into JPEG format for inclusion
&gt; in HTML documents. Thus far I have had no success with the
&gt; Save Regions selection. Any suggestions how this might be
&gt; accomplished?

The Save Regions selection is to save whatever annotations etc you may
have made into a text format file.  The option you are looking for is the
File-&gt;save img menu item.  It allows to save whatever appears in the DS9
display as a jpg/tiff/png/ppm with quite superior resolution compared to
what can be achieved with xv or any other screen capture program.

For a few samples of what I have achieved with this option in ds9 you can
look up http://www.prl.ernet.in/~shashi/tmw/ and other links there.  I use
ds9 on linux with redhat 7.3

HTH,
shashi



-- 
2003-04-04 at 9:01am IST
-------------------------------------------------------------------------------
Shashikiran Ganesh                  |  shashi@prl.res.in
Physical Research Laboratory        |
Astronomy and Astrophysics Division |  http://www.prl.res.in/~shashi
Ahmedabad 380 009, India            |  http://www.iap.fr/users/shashi
-------------------------------------------------------------------------------
</pre>

---

*Last post on Apr 04, 2003*
