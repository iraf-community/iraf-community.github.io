---
title: "Using SAOtng on a 16-bit (or higher) display under Linux"
---

# Using SAOtng on a 16-bit (or higher) display under Linux

**John Ouellette** wrote on Jun 18, 1998

<pre style="background: transparent; box-shadow: none; border: none;">

 For those people running Linux and who normally use a 16-bit or higher
display, there
is a possible workaround for the nuisance of having to start an 8-bit
XServer whenever
they want to use SAOtng (or XImtool).  The IRAF FAQ suggests using XNest
to start a
nested XServer  which runs inside your 16-bit display, but is itself an
8-bit display.  Ideally,
it would be possible to run an SAOtng within this nested XServer while
still using various
&#x27;colour-intensive&#x27; applications, such as netscape, in the 16-bit
Xserver.  The unfortunate
reality is that many  video cards don&#x27;t support multiple display depths:
you can use XNest,
but it has to run at the same depth as the main XServer....

Under Linux it is possible to use one of the virtual terminals
(Ctrl-Alt-F1..12) as a second display.
Normally when you start Xwindows, your display (usually :0.0) starts up
on the  virtual terminal
accessed through Ctrl-Alt-F7.  If you were to start second Xsession
(called, say, :1.0) it would
start under a different virtual terminal (usually Ctrl-Alt-F8).  Here&#x27;s
what I do, which is probably
not the most elegant solution:

o start Xwindows normally (e.g. startx -- -bpp 16)  using the following
.xinitrc:
==========================
    #!/bin/csh
    xrdb -load $HOME/.Xdefaults
    xset c off s 600

    xterm -ls -T ${HOST} -display :0.0 -cr red -g 80x24+0+0 -fg black
-bg white &amp;
    sleep 2
    xload -display :0.0 -update 2  -g 150x80-135-0 &amp;
    sleep 2
    xbiff  -display :1.0 -g -5+0 &amp;

    xsetroot -gray
    fvwm  -display :0.0
==========================

    This starts an Xwindows session on the virtual terminal F7.

o go to virtual terminal F2 (Ctr-Alt-F2 -- the usual login screen is F1)
and login.

o start the second Xserver with &#x27;startx ~/.xinitrc.2 -- :1 -bpp 8&#x27; where
.xinitrc.2 is:
========================
#!/bin/csh
    xrdb -load $HOME/.Xdefaults
    xset c off s 600

    xterm -ls -T ${HOST} -display :1.0 -cr red -g 80x24+0+0 -fg black
-bg white &amp;
    sleep 2
    xload -display :1.0 -update 2  -g 150x80-135-0 &amp;
    sleep 2
    xbiff  -display :1.0 -g -5+0 &amp;

    xsetroot -gray
    fvwm  -display :1.0
==========================

    This starts an Xwindows session on the virutal terminal F8

o the two Xsessions can be switched between using Ctrl-Alt-F7 (the
16-bit session) and
   Ctrl-Alt-F8 (the 8-bit session)


This uses a fair bit of memory (each Xserver is going to be ~10MB, plus
whatever utilities you
start) but is still much faster and more convenient than logging off to
start an 8-bit display....
The two servers can be treated like separate XTerminals running off the
same server.

I have no idea if the XServers for Solaris, SunOs, Alphas, etc.  allow
virtual terminals, but
it may be that XNest will work on their video cards.

John Ouellette
</pre>

---

*Last post on Jun 18, 1998*
