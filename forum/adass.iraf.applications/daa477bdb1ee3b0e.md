---
title: "FOCAS: difference in magnitudes with different thresholds"
---

## FOCAS: difference in magnitudes with different thresholds

**Frank Valdes** wrote on Jul 24, 1998

<pre style="background: transparent; box-shadow: none; border: none;">
Q:  I ran the same image through FOCAS twice -- once getting 2-sigma
detections and the other time 3-sigma detections.  The only thing I
changed was the detection level.  Each time I measured an aperture
magnitude with the same aperture radius and found differences in the
2-sigma and 3-sigma cases of up to ~0.5 mag.  Why would this be?  I
thought the aperture magnitude was just counting up the flux within the
aperture and subtracting the sky flux from the object flux?


A: I believe the difference you see with the 2 and 3 sigma detections is
the sky estimation.  The 2 sigma detections will have larger isophotes.
The sky measurement uses the detection isophote to define the sky by
making a square sky annulus with a minimum distance from the isophote
of 2 pixels (the default).  So if the isophote is larger then the sky
region is farther out.  For the faintest objects you can get quite
a difference since the magnitude is dominated by the sky estimate.
In recent versions of SKY you can play with the sky region parameters
(the buffer distance and width).
</pre>

---

*Last post on Jul 24, 1998*
