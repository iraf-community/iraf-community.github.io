---
title: "cl command line"
---

## cl command line

**Mike Fitzpatrick** wrote on Apr 21, 2003

<pre style="background: transparent; box-shadow: none; border: none;">

&gt; ...it might be interesting to start a more general discussion of what
&gt; features the user community would *really* like to see in IRAF

	This was more of a rhetorical statement than a request but I&#x27;m
glad to see it&#x27;s at least generated some interest.  Some of the comments
are familiar (all are useful) but I was amused the &quot;backspace key
problem&quot; and &quot;24-bit ximtool&quot; weren&#x27;t on the list since those always seem
to be the top complaints.
	A few comments follow to help keep the discission going...

Michael Ashley wrote: 

&gt; - Command-line editing that really works (I use NCL, and it is robust;
&gt;   the xterm keymap idea, while ingenious, is a kludge that (1) isn&#x27;t
&gt;   bullet-proof, and (2) less than 0.1% of users would bother to install).

	I agree it&#x27;s not bullet-proof but it is a solution users can
implement and customize themselves to make the &quot;IRAF experience&quot; as easy
as they like.  As for installation, it could be done as a default set of
translations in the distributed XGterm which users can enable or not with
the F2 key, but given all the tweaking people do to e.g. customize emacs
with special modes I thought somebody might find it kinda cool and extend.
Personally, I think more keys have been typed exchanging mail on the
subject than all of the &quot;e&lt;cr&gt;&quot; keystroke savings it takes to start
ehistory, but arrow-history a feature I would use myself (and find myself
expecting to be available so I feel your pain).

&gt; - Consistent reliable handling of CNTL-C interruption of scripts.
&gt; - The removal of the need to type &quot;flpr; flpr&quot; at mysterious times for
&gt;   mysterious purposes.
&gt; - Error handling. This is the biggest problem with IRAF, in my opinion.
&gt;   We need a status return codes on all scripts, and all operating system
&gt;   processes.
&gt; - Improved error messages for IRAF scripts.

	These are all CL improvements and it&#x27;s almost certain that there
will be some work done on the CL this summer to add things like error
recovery and other features.  The &#x27;flpr;flpr&#x27; is either a CL bug or task
problem but nobody&#x27;s ever been able to give a reproduce case for it and
there&#x27;s no logical explanation for why this should work at all (i.e. one
should be enough).  I assume reporting the correct line number from script
crashes is what&#x27;s meant by the last comment, but are there other examples?
(&quot;floating point exception&quot; and &quot;segmentation violation&quot; don&#x27;t count
unless somebody can tell me how the script can debug the task in real-time
to report &quot;parameter &#x27;foo&#x27; is set to zero and that&#x27;s why it died&quot;).

&gt; - Installation via an RPM rather than an interactive shell script.

	That&#x27;s nice for RedHat and similar systems but the Debian folks
have their installer, as do Sun, HP, FreeBSD, Mac, etc.  Somewhere I&#x27;ve got
an unfinished project for auto-installers but keep in mind we have a dozen
or so platforms and a very limited support staff.  Users with a special
interest in a platform do distribute their own installers (e.g. for RPMs
see http://caliente.as.arizona.edu/~tim/RPMS/8.0-custom/RPMS/, for OS X
pkg installers see the link on our homepage for the OS X support page, 
IRAF (okay so it&#x27;s an old version) is included with Debian, etc).

&gt; - The IRAF parameter system has a number of problems, e.g.,
&gt; 
&gt;      - it makes it difficult to have multiple simultaneously running
&gt;        scripts under the same username, since the parameter files clash
&gt;        (I use a temporary directory to get around this).

	Only when the tasks being run update their parameter files, and
there may be cases where you want different parameter environments for
different projects.  See the CL help page on the &#x27;cache&#x27; command that 
will let you cache the parameters for a background script to avoid this
problem.

&gt;      - new releases often add new parameters, which can then cause
&gt;        inconsistent behaviour in existing scripts (unless you are
&gt;        careful to &quot;unlearn&quot; every program you use).

	Other than freezing/renaming the tasks with each release there&#x27;s
not much that can be done about this.  Parameter changes are considered as
a last resort to specifically avoid breaking scripts and we try to document
all the parameter changes for a release to simplify updating the scripts,
but problems still occur.  For major releases you should *always&quot; just
reinitialize your uparm with a new MKIRAF rather than rely on uparm.
	At one time we did have a project that would statically check
scripts and alert you to parameter changes in your code but the programmer
left before that was completed.  Something like this (e.g. as a web-service
where you upload a script and get back a report) would be a nice thing to
have for users, but we&#x27;re open to other suggestions.

&gt; - SPP was a good idea at the time (when FORTRAN-IV was the only standard
&gt;   you could depend on), but it is now a liability, primarily because it
&gt;   is usually not a good career move for programmers to become proficient
&gt;   in it. The GNU C compiler is widespread enough to be a good substitute.

	Well then you&#x27;ll be glad to know the GNU C compiler been used in
IRAF since the initial V2.10.3 Linux port (the fortran compilers are used
on most systems, PC-IRAF uses F2C to convert to C code for compilation in
the final stage).  IRAF programming was never a growth industry (now more
than ever) but it&#x27;s naive to say SPP is a liability given that&#x27;s the main
reason we&#x27;ve been able to port a million lines of code to twenty or more
platforms over 20 years with minimal effort and staff.  A C language
binding for the IRAF system may get more people to look at programming in
iraf but they&#x27;ll still face the same learning curve for all the system
interfaces long after they&#x27;ve picked up the SPP syntax in the first week
or two.

&gt; - I think the time has come to drop the cl and move to a good scripting
&gt;   language such as python or perl. The PyRAF project is on the right track
&gt;   here.

	No argument that there are better scripting environments around
and we would love to be able to use them.  Dropping the CL isn&#x27;t an option
given we have to continue to support all the code currently developed,
but there are things which could be done to improve it and we hope to
do that soon (really).

&gt; OK, that&#x27;s probably enough to go on with! I have an affection for IRAF,
&gt; and it would be nice to see it continue to be used for the next several
&gt; decades, but if it is to prosper and grow I suspect that some big
&gt; decisions will have to be made soon, and some long-held ideas abandoned.

	That&#x27;s a whole other discussion that&#x27;s been had already in various
circles.  What it really needs to be pulled off are the resources and 
political/community backing required to do development on a scale similar
to building the system in the first place, so start the letter-writing 
campaign soon folks.



Eric Jensen writes:

&gt; First, let me say that I use IRAF a lot and I think it has a lot of
&gt; things going for it.  Thanks for a very useful software package. ...

	This would be a good opening to the letter mentioned above 8-)


&gt; I&#x27;ll second this (both the need for it and the unacceptability of the
&gt; keymap workaround).  I teach a lot of people how to use IRAF (we have
&gt; only undergraduate students here), and just the lack of a
&gt; straightforward way to type and edit commands is a big stumbling block
&gt; for people in becoming comfortable with IRAF.  In addition to
&gt; command-line recall, I&#x27;ll note a few other, related things:
&gt; 
&gt; * While ehistory allows one to recall and edit previous commands, it
&gt; is not easy to edit the *current* command one is typing (e.g. to arrow
&gt; back and insert a letter you missed typing).

	This is because in the CL the command is entered via a normal
text read terminated with a newline, while in the NCL (and e.g. tcsh) the
terminal is put into raw mode so an arrow key can be &quot;intercepted&quot; and
an editing function used.  Raw terminal mode has some side-effects with
some (admittedly obscure) CL features such as tty playback which is used
in our test scripts and so the NCL solution wasn&#x27;t adopted for the released
code.  It might be possible to integrate this functionality by means of
CL parameter to toggle the behavior and would be a feature that users
would certainly appreciate.

&gt; * The behavior of the backspace and delete keys is different in
&gt; ehistory than it is in editing the current command.  ....

	The epar/ehist modes are controlled by the type of editor you have
defined (where the actual keystrokes are defined by the e.g. dev$vi.ed or
dev$emacs.ed file), while the command line backspace is just the normal
unix backspace char.  This last statement needs to be qualified by saying
that a user&#x27;s backspace can be overridden in a number of ways (e.g. the
xmodmap, stty/tset commands, system defaults) and the most confusing thing
is that what the user defines in their environment can be trumped by what
the system sets since the &#x27;cl command is a C-shell script and will read
the system cshrc file.  For example, recent RedHat systems don&#x27;t use
either of the BS or DEL keystrokes to backspace a character, the
/etc/csh.login file uses &#x27;bindkey&#x27; to reset the backspace to some escape
sequence and default X translation for XTerm to make it work.  Even if IRAF
in raw mode were looking or a BS char it may never get it!  All told there
are some six different ways to reset the backspace char and none of them
have to agree, but outside of the epar/ehist mode there&#x27;s nothing in IRAF
which sets/assumes any particular character.

&gt; * Parameter editing suffers from some of the same difficulties as
&gt; command line editing; no easy way to fix what you&#x27;ve typed, etc.

	Try doing an ESC-? in epar to view the edit commands.  If you use
the default &#x27;vi&#x27; editor then a ^U^L (where &#x27;^&#x27; is Ctrl) sequence will let
you edit the line.

&gt; * The xiraf script by Vassilis Charmandaris
&gt; (http://astrosun.tn.cornell.edu/staff/vassilis/xiraf/) is a great
&gt; service to the IRAF community, but there&#x27;s no reason (that I can see)
&gt; that these things shouldn&#x27;t just be built into IRAF itself.  For
&gt; example, I can&#x27;t think of another program that won&#x27;t even look in a
&gt; *default* location (i.e. ~/iraf/login.cl) to find its startup file.
&gt; And is there a good reason not to name the default binary &quot;iraf&quot;, or
&gt; at least to have a symlink from cl to iraf?

	Things like the &#x27;cl&#x27; startup name are historical and difficult to
change as a default, but there are reasons why you may want to have a
specific (and separate) directory for iraf sessions.  Default
login/startup files often mean hidden setups which carry their own
difficulties for new users.  I agree something like xiraf should be part
of the default user environment (but with a GUI front-end and additional
controls for the iraf env such as printers, task declarations, etc), alas
this is another unfinished project....

&gt; P.S. Is ncl no longer being distributed/maintained?  I couldn&#x27;t find
&gt; it on the SAORD pages.  I&#x27;ll have to try pyraf.

	Last I looked NCL was being kept alive by the arrow-history feature
but not really being developed.  It&#x27;s distributed as part of the &#x27;saord&#x27;
suite and not really as a separate product.


Cheers,
-Mike
</pre>

---

*Last post on Apr 21, 2003*
