---
title: "Using Telluric task"
---

# Using Telluric task

**Frank Valdes** wrote on Sep 13, 2002

<pre style="background: transparent; box-shadow: none; border: none;">
Hi Ernesto,

It is not clear what problem you have with continuum normalizing.  I have
done this before and it works fine.  Something else I do in that case
is replace regions where there are no telluric lines by 1 so that there is then
no noise added when it is divided into the target spectrum.

Another comment is that whether or not you care about the continuum of
your target being changed by the telluric correction depends both on
what measurements you will be making and whether the spectrum is later
flux calibrated.   When I&#x27;ve used it I was later going to flux calibrate
so I didn&#x27;t really care what the shape was as long as what was done
was also done to the standard stars.

Please let me know what it is that wrong with using a continuum
normalized hot star spectrum.  How are you doing the normalization?  It
might be simplest if you provided a target spectrum, a calibration
spectrum, and the parameters and command to demonstrate the problem.

Yours,
Frank Valdes
</pre>

---

*Last post on Sep 13, 2002*
