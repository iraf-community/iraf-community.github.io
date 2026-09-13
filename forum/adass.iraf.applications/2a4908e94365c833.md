---
title: "dictionary full message"
---

# dictionary full message

**Mike Fitzpatrick** wrote on Jul 05, 1998

<pre style="background: transparent; box-shadow: none; border: none;">

&gt; I&#x27;ve been working in an IRAF script which takes a long time to be
&gt; executed (tipically three days or more). It consist on a multi loop of
&gt; different parameters which makes use of some IRAF tasks, like lucy in
&gt; STSDAS and fitpsf in DIGIPHOTX.  It also deals with a lot of system
&gt; calls as:
&gt; 
&gt; print(&quot;!program.exe &quot; // par1 // &quot; &quot;// par2) | cl()

The bug you are seeing is caused by an apparent bug in the CL that we
haven&#x27;t tracked down yet in which each statement that pipes a command to a
&#x27;cl&#x27; or &#x27;clbye&#x27; increases the size of the dictionary stack (what it uses
to catalog tasks, packages, parameters, etc.) a small amount on each
iteration until the limit is reached.  The workaround is to either use a
&#x27;!&#x27; escape explicitly (only useful if you don&#x27;t need to pass script
variables as arguments) or else have the task declared as foreign and then
call it as though it were a normal iraf task.  For example,

        task $program   = $foreign

and in your script you would

        program (par1, par2)

Note that since extensions have meaning when declaring a task you&#x27;ll have
to drop the &quot;.exe&quot; from the task declaration, and &#x27;program&#x27; will need to
be in the path defined in your .cshrc file (since foreign commands are
run in spawned C-shells that source this file).

Mike Fitzpatrick
</pre>

---

*Last post on Jul 05, 1998*
