---
title: "IMEXAM/v plot: non-interactive, same endpoints, overplots"
---

# IMEXAM/v plot: non-interactive, same endpoints, overplots

**Frank Valdes** wrote on Sep 21, 1998

<pre style="background: transparent; box-shadow: none; border: none;">
Q:  Within the task imexamine I&#x27;m trying to create vector profiles
across vectors. This works quite well using the pair of v commands
indicated in the help file for imexamine. I really want to do this on
several images (one at a time) from specific pairs of coordinates, i.e.
create plots over the same vectors.  This can be done, but it is tedious,
using the cursor on the ximtool display. Within the imexamine help file
it looks like there may be a way of doing this with a colon command,
however, I&#x27;ve not found the right combination of commands to do this.

If this can be done, please give me the series of commands, including
information about where the cursor should be located while the entries
are being made.

Also, once this is done (either by the cursor or colon command), can I
make an overplot of the second vector profile? How?


A: There is no way to explicitly set the endpoints for a v plot in IMEXAM
when done interactively.  However, you can do this using a cursor
input file in place of the interactive cursor.  Let me show you an
example that will do what you want.  First prepare a cursor file with
an editor so that it is something like:

200 250 101 v
310 330 101 v
n
o
200 250 101 v
310 330 101 v
q

The first line gives the image cursor position (200,250), the cursor
id (which you can leave as 101) and the cursor key, in this case the first
v key.  The second line gives the second v key.  If the cursor position
does not matter then you can simply give the cursor key.  The third line
is the n key which means go to the next image.  The o key says to overplot
the next graph.  Then the same v endpoints are given.  Finally quit the
program.  To execute this command file:

cl&gt; imexam image1,image2 imagecur=cursor.dat use-

The name of the cursor file in this example is &quot;cursor.dat&quot;.  The use-
means don&#x27;t use the image display.  You can make this cursor file do as
much as you want.

Once you get your graph you can make a hard copy by entering the graphics
cursor mode:

cl&gt; =gcur
[type = or :snap as you normally do for a hard copy]
q

Or you can just add the hardcopy command to the cursor file.


Q: Thanks for the help, this works fine, it is just what I needed.

You may know the answer to this one too. 
I want to vary the width over which the average is taken along
the vector. I can do this vi going to the vimexam parameter file
and setting the parameter naverage to the desired number. But since
this value will vary from vector to vector, I&#x27;d rather adjust it
by a command on the line. When I try this it doesn&#x27;t work. e.g.

on&gt;imexam pc2geonorm,pc1 imagecur=v1697.1045 use- naverage=2
   ERROR: parameter `naverage&#x27; not found

Got a suggestion on easily adjusting this parameter?


A:  There are two suggestions.  One is that you can set it as needed in
the cursor file (v1697.1045) with a line like

:naverage 2

You can also set it with a command just before imexam:

on&gt; vimexam.naverage=2
on&gt; imexam pc2geonorm,pc1 imagecur=v1697.1045 use-

Note that you can use epar too &quot;epar vimexam&quot;.
</pre>

---

*Last post on Sep 21, 1998*
