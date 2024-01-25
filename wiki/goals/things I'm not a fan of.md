
Things I'm not a fan of
=======================

Stuff that's out there, no doubt exists for good reasons, but that I'm not particularly fond of.


Programming concepts
--------------------

Some of these make code hard, or ugly, or both.


Closures
	https://en.wikipedia.org/wiki/Closure_(computer_programming)

	Automatic creation of a hidden state
	Functions aren't pure

	https://en.wikipedia.org/wiki/Closure_(computer_programming)#State_representation

	Seem to be bread-and-butter in JavaScript these days, but dang they make code hard to reason about.

	See also the https://en.wikipedia.org/wiki/Funarg_problem for some more background on this.



Continuation passing
	https://en.wikipedia.org/wiki/Continuation-passing_style

	https://docs.microsoft.com/en-us/archive/blogs/ericlippert/continuation-passing-style-revisited-part-one

	Functions have unnecessary responsibilities
	Not a good look in high-level code.


Tail Calls
	https://en.wikipedia.org/wiki/Tail_call
	Same as above, unnecessary resonsibilities.
	Always thought they were ugly in ordinary code.




Run-of-the-mill stuff
---------------------
Just regular gripes about ordinary language features


	function arguments as arrays

	excessive use of 'if'

	nested callbacks

	deeply nested anything

	excessive use of lambdas


