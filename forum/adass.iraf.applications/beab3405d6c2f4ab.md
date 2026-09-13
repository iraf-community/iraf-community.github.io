---
title: "FeNe linelist, creating one by filtering existing lists"
---

# FeNe linelist, creating one by filtering existing lists

**Frank Valdes** wrote on May 21, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
Q: I have recently started doing reductions which use FeNe for a
comparison source and I have been unable to find the coresponding line
list to use with the identify function.  If you could pleas point me in
the right direction it would be greatly appreciated (I have looked at
the contrib directroy and found no reference to any linelists there).


A:  I assume you looked in the linelists$ directory in your version of
IRAF.  Those are the only line lists that I know anything about.  There
is an FeAr list (fear.dat) which also includes the element
identification.  A simple match could extract just the iron lines.
Similarly the HeNeAr high resolution list henearhres.dat or lower
resolution list henear.dat can be used to select Ne lines.  You could
then put them together into a list of FeNe lines.
</pre>

---

**Steve Heathcote** wrote on May 21, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
Frank,

Perhaps you might feed the following aditional info back to the
enquirer:

&gt; Q: I have recently started doing reductions which use FeNe for a
&gt; comparison source and I have been unable to find the coresponding line
&gt; list to use with the identify function.  If you could pleas point me in
&gt; the right direction it would be greatly appreciated (I have looked at
&gt; the contrib directroy and found no reference to any linelists there).
&gt; 
&gt; A:  I assume you looked in the linelists$ directory in your version of
&gt; IRAF.  Those are the only line lists that I know anything about.  There
&gt; is an FeAr list (fear.dat) which also includes the element
&gt; identification.  A simple match could extract just the iron lines.
&gt; Similarly the HeNeAr high resolution list henearhres.dat or lower
&gt; resolution list henear.dat can be used to select Ne lines.  You could
&gt; then put them together into a list of FeNe lines.

modified A:  Actually the gas in lamps like this is rarely pure and in 
particular most FeAr or FeNe lamps will show lines of BOTH Ar and Ne 
plus those of Fe.  I&#x27;m actually surprized that the fear.dat FeAr list 
contains no Ne lines. The relative strengths of the ArI/ArII and NeI
lines 
vary depending upon many factors such as the voltage the lamp is run at, 
its age and so on. This can make it quite difficult to recognize the
lamp
spectrum given only a line list unless you already have a pretty good 
idea of your wavelength coverage. In general the FeI lines will be much 
fainter than the lines from the gas. Thus rather than start by filtering
the lists as Frank suggests, I would begin by trying to identify the 
strongest few lines using e.g the henearhres.dat list with either Ar or
Ne 
lines (there probably won&#x27;t be any He lines). Once you have a
preliminary
wavelength calibration you can then add in Fe lines from the fear.dat
list
or make a composite list (containing Ar, Ne and Fe) as Frank suggests.
With a spectrum this busy though you will need to be careful to weed out
any possible blends.

Steve
</pre>

---

*Last post on May 21, 1999*
