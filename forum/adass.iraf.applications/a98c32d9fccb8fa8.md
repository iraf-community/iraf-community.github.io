---
title: "variables in simple CL scripts?"
---

## variables in simple CL scripts?

**Frank Valdes** wrote on Jun 06, 2000

<pre style="background: transparent; box-shadow: none; border: none;">
I am posting this since others may have the impression that simple CL
scripts cannot use variables.



Q:  I have a very simple script as follows:

mask2.cl
#
# good pix are 0, bad are 1 for IRAF mask
# the values 0.65 and 1.25 need to be checked on the histogram
#  each time you make the mask.
#
imrep mask lower=INDEF upper=0.7 val=-1
imrep mask lower=1.2 upper=INDEF val=-1
imrep mask lower=0.7 upper=1.2 val=0
imar mask * mask mask
imcopy mask.imh mask.pl
# make DAOPHOT mask where bad pix are 0 and good are 1
imrename mask.imh maskdao
imar maskdao - 1 maskdao
imar maskdao * -1 maskdao


I run it as 

cl &lt; mask2.cl

Now, sometimes I want to change the values of 0.7 or 1.2 to other
values. I can easily edit this task. But it seems to me that if
I was able to put some lines at the top, like:
lll=0.75 
uuu=1.25

and then somehow substitute these in the &quot;imrep&quot; commands, I could
speed up changing the file.

Now, if I was writing an IRAF task I know how to do this.  But for
quick scripts, it is a waste of my time to do this because I have to
put in all the {}s, begin/end, int/real/string, and then issue a &quot;task
mask = ...&quot;.


For a simple task, if I was just changing the lower or upper value, I
would just use:

imreplace.lower=0.75
imreplace.upper=1.2

and these values would remain for the life of the script. But I can&#x27;t
do this here, because sometimes 0.75 is the lower parameter and
sometimes the upper parameter.

Is there an easy way of temporarily defining a value and having it
substituted into the subsequent commands in a simple script?


A:  First of all you can do pretty much what you want even in a simple script.
The only thing you need to do is any statement where you want to substitute
a variable you have to use the task() form.  You can also declare variables
in the same way as a procedure script.  So you can have

real lll, uuu
lll = 0.75
uuu = 1.25
imrep (&quot;mask&quot;, lower=INDEF, upper=uuu, val=-1)
imrep (&quot;mask&quot;, lower=lll, upper=INDEF, val=-1)
imrep (&quot;mask&quot;, lower=lll, upper=uuu, val=0)
imar mask * mask mask
[etc]

So note that the imarith does not have () and then the names don&#x27;t have
to be capitalized.  But the imrep do use () in order to reference the
variables.

This script can still be run with &quot;cl &lt; mask2.cl&quot; without having to
declare it as a task, etc.  The only strong reason for using a procedure
script declared as a task is if you want parameters.  A less common reason
is if you have something in a script that reads from the standard input
in which case the &quot;cl &lt; task&quot; form would not work right.

Finally I want to call your attention to the task IMEXPR.  It takes a
little reading and experimenting to understand the more complex syntax
but it is perfect for the type of things you are doing in the script
and things can done in one step.  Below is an example.  I didn&#x27;t try
it so maybe I have a minor syntax error.

imexpr &quot;(a &gt; b || a &lt; c) ? 1 : 0&quot; mask.pl mask.imh 0.7 1.2
imexpr &quot;(a == 1) ? 0 : 1&quot; maskdao out

Another warning, using the same root name with two image types can lead
to confusion and problems; i.e. mask.imh and mask.pl.
</pre>

---

*Last post on Jun 06, 2000*
