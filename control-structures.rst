.. _control-structures:

Control Structures
==================

Overview
--------

Go provides flexible control structure for branching and looping
logics.  We will go through all the controll structures in this
chapter.

If Condition
------------

One of the common logic that is required for programming is branching
logic.  On certain condition, perform a particular action.  To achive
this, `if` condition is used, where when an expression evaluted as a
true, action is performed.  Conside this example::

  if 1 < 2 {
    fmt.Println("1 is less than 2")
  }


The first line starts with the `if` keyword followed by an expression
and the line ends with an opening curly bracket.  If the expression is
getting evaluated as true, the statements given within the curly brace
will get evaluated.  In the above example, the expression ``1 < 2``
will be evaluated as true so the print statement given below that will
get executed.  You can add any number of statements within the braces.

Sometimes you need to perform different set of action if the condition
is not ture.  Go provides a variation of the `if` syntax with `else`
block for that.

Consider another example::

  if 3 > 4 {
    fmt.Println("3 is greater than 4")
  } else {
    fmt.Println("3 is not greater than 4")
  }

In the above code, the code will not be evaluated as true.  So the
statements within else block will get executed.

For Loop
--------

Switch Cases
------------

Exercises
---------

Problems
--------

Summary
-------

.. raw:: html

   <div id="disqus_thread"></div> <script type="text/javascript"> var
   disqus_shortname = 'comprehensivego'; (function() { var dsq =
   document.createElement('script'); dsq.type = 'text/javascript';
   dsq.async = true; dsq.src = '//' + disqus_shortname +
   '.disqus.com/embed.js'; (document.getElementsByTagName('head')[0]
   || document.getElementsByTagName('body')[0]).appendChild(dsq);
   })(); </script> <noscript>Please enable JavaScript to view the <a
   href="https://disqus.com/?ref_noscript" rel="nofollow">comments
   powered by Disqus.</a></noscript>
