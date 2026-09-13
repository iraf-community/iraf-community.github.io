---
title: "Talking to XGterm from another application ??"
---

# Talking to XGterm from another application ??

**Sergei Naumov** wrote on Apr 15, 1998

<pre style="background: transparent; box-shadow: none; border: none;">


Hi!
I was wondering about one thing. Is there any way to know what XgTerm is
displaying in the Tek window? The reason is the following...

I wrote a little Gtk+/MySQL application (that I am planning to release
for general public quite soon -- I am doing the docs) that is an
electronic solar atlas. This application is displaying a piece from a 
solar spectrum together with lines, etc.

Some Iraf tasks like splot display a spectrum in a Tek window and a user
can &quot;expand&quot; the plot effectively specifying the wavelength range.
My question is wthether there is a way to get this wavelength range 
somehow from another application (my solar atlas). I truly suspect that
there is no any kind of protocol, that this plotting information
is not stored anywhere, and that splot is written in such a way that none
can get it from there but...

I just thought I can give it a shot. It would be absolutely wonderful to
implement some sort of platting/drawing protocol that can provide this
kind of information for the external applications.

Thanks much,

		-- Sergei Naumov
	   	   serge@astro.unc.edu
</pre>

---

*Last post on Apr 15, 1998*
