---
title: "CNSHD103243 Re: STSDAS programming help"
---

## CNSHD103243 Re: STSDAS programming help

**Help@stsci.edu** wrote on Jun 24, 1999

<pre style="background: transparent; box-shadow: none; border: none;">
If you need to respond to this message please do so by replying to this message or create a new message with call number CNSHD103243 included in the subject line.

Current call log entry : Shel,
   
   I created a &#x27;child call&#x27; from our previous discussion, because it was
   getting to be too long a message for our &#x27;help&#x27; logging software to 
   handle gracefully.
   
   &gt; How long have you been working with IRAF?   
   I have been using IRAF for &gt; 11 years.  
   
   I learned about &#x27;ukey&#x27; after I had communicated with you, and countless
   others on the adass-exploder email address that you use.
   
   Your &#x27;final&#x27; program looks darn respectable!  Good work!
   
   I noticed that you added &#x27;delete&#x27; lines to clean up temporary files and
   that you direct all output to dev$null.  This can be dangerous because
   you won&#x27;t see error messages, if for example, you attempted to delete
   a file that did not exist or you didn&#x27;t have permission to delete.
   
   &gt; delete (tempmean, ver-, &gt;&amp; &quot;dev$null&quot;)
   
   In my scripts I check for the existance of a file before I try to
   delete.  This way you can be certain that the file actually was
   created.  This makes debugging esier.  
   
   Here is a snippet from a script of mine that does that:
   
   if (access(ellip)){
           imdel (ellip,
           yes, verify=no, default_acti=yes)
           print (&quot;Found and deleted &quot;//ellip//&quot;, the old ellipse image.&quot;)
                     }
   
   Eric
</pre>

---

*Last post on Jun 24, 1999*
