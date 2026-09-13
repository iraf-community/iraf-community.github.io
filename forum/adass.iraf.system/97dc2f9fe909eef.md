---
title: "CCDPROC question."
---

# CCDPROC question.

**Sergei Naumov** wrote on Dec 19, 1997

<pre style="background: transparent; box-shadow: none; border: none;">



Hi!
I was wondering about something. Why after I process bias frames with
the ccdproc I get the frame that has an average of 1.0 as if it
subtracted the average from the image? I do not really know how to
interpret this. On one hand, for the photometry I am doing it does
not really matter as long as the final image retains the variations:
the average number will just be implicitely included in the zero
order term in the photometry transformation. But... It bothers me
somehow.

Any comments on that?

Thanks much,
			Sergei
</pre>

---

**Frank Valdes** wrote on Dec 22, 1997

<pre style="background: transparent; box-shadow: none; border: none;">

Hi Sergei,

What you are seeing is correct.  By a bias frame I assume you mean an
exposure of zero exposure time with the shutter closed.  The overscan
correction removes the electronic bias level and leaves just the signal
from the zero exposure time.  In a perfect CCD the mean of a zero
exposure time should be zero.  Maybe your mean of 1 is just statistical
scatter and it is also consistent with zero.  But even if not the point
of a zero exposure is that there may be some level left over due to
other effects and that is why a zero or bias frame is subtracted from
the data.  The zero frame may also contain pattern noise to be
removed.  So it would actually be more surprising if your bias frame
did not have a mean near zero.  A mean of one should not be a source of
concern.

Cheers,
Frank Valdes
NOAO/IRAF Group
</pre>

---

*Last post on Dec 22, 1997*
