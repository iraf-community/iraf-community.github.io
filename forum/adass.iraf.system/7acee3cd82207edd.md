---
title: "Multiple Plots on a Screen"
---

# Multiple Plots on a Screen

**Mike Fitzpatrick** wrote on Jun 25, 1998

<pre style="background: transparent; box-shadow: none; border: none;">

&gt; A user wants to use &quot;graph&quot; or the STSDAS &quot;sgraph&quot; to plot 4 plots on the
&gt; same gterm. However, when he uses graph the two graphs are placed in their
&gt; respective corners but when the second graph appears on the graphics
&gt; window the first get erased.  I played with the &quot;overplot&quot; and &quot;append&quot;
&gt; keywords but I can not make it so that the second graph does not clear the
&gt; first one.  The behaviour of &quot;sgraph&quot; is similar.  Is there another
&gt; program he can use, which will enable him to have multiple plots on the
&gt; screen?
&gt; 
&gt; We use IRAF 2.11 and xgterm as the stty.

	In reality the plots are being drawn correctly, but the colors of
the xgterm window are getting in the way.  For example try the following:

 cl&gt; graph dev$pix[*,23] vx1=0.6 vx2=0.95 vy1=0.1 vy2=0.45 
 cl&gt; graph dev$pix[*,34] vx1=0.6 vx2=0.95 vy1=0.6 vy2=0.95 append- overplot+

It looks like the second plot erases the first, but what really happens is
that when the second plot gets drawn the screen is filled with the
&#x27;viewport frame&#x27; color (which effectively erases the first plot) before
drawing the second plot.  The trick is to get rid of the colors, e.g. when
using xgterm before calling graph/sgraph use

	cl&gt; stty vt640

Alternatively you could &#x27;reset glbcolor = &quot;&quot;&#x27; but with the above it&#x27;s
easier to go back to making color plots.  Now try the example above and
you should see both plots on the sreen.
	If you want the plot labels/axis colors for each graph then using
gkimosaic on the saved metacode files (e.g. created with &quot;:.write&quot; from a
cursor mode) is the only way to retain that, but keep in mind that for
most hardcopy choices you&#x27;ll lose this anyway.

-Mike
</pre>

---

*Last post on Jun 25, 1998*
