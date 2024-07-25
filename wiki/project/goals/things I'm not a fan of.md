
Things I'm not a fan of
=======================

Stuff that's out there, no doubt exists for good reasons, but that I'm not particularly fond of.

Some of these make code confusing, ugly, difficult etc.

Some I'll actively try to exclude from Silver (variadic functions), but others are just consequences of things like first-class functions (tail calls, continuations).

Some could perhaps be implemented as libraries if needed (closures, currying).



Closures
--------

https://en.wikipedia.org/wiki/Closure_(computer_programming)

Automatic creation of a hidden state
Functions aren't pure or deterministic.

https://en.wikipedia.org/wiki/Closure_(computer_programming)#State_representation

Seem to be bread-and-butter in JavaScript these days, but dang they make code hard to reason about.

See also the https://en.wikipedia.org/wiki/Funarg_problem for some more background on this.

I won't add these to Silver if i can help it.



Continuation passing
--------------------

https://en.wikipedia.org/wiki/Continuation-passing_style

https://docs.microsoft.com/en-us/archive/blogs/ericlippert/continuation-passing-style-revisited-part-one

Functions have unnecessary responsibilities.
Not a good look in high-level code.

With first-class functions this can't be prevented and becomes a stylistic choice for the dev.


Tail Calls
----------

https://en.wikipedia.org/wiki/Tail_call
Same as above, unnecessary resonsibilities.
Always thought they were ugly in ordinary code.

Again, with first-class functions this can't be prevented and becomes a stylistic choice for the dev.


Variadic functions
------------------

aka 'Varargs'

https://en.wikipedia.org/wiki/Variadic_function

In particular variadic functions of mixed types, eg:

	C's  printf
	https://pkg.go.dev/fmt#pkg-functions

I'm sure I've seen examples where languages/libraries have wanted to add extra arguments and shot themselves in the foot.

These should be named typed arrays of the argument structure, so instead of having something like:

	print(template,var,var,var...)

It should be something like:

	print(template:'...', variables:{var1:value1, var2:value2, ...})


I also suspect there might be typing issues with variadic functions, see for example: https://en.wikipedia.org/wiki/Uncontrolled_format_string

I won't add variadic functions to silver.


Currying
--------

...

Run-of-the-mill stuff
---------------------
Just regular gripes about ordinary language features and patterns


*	function arguments as arrays - see variadic functions
*	excessive use of 'if'
*	nested callbacks
*	deeply nested anything
*	excessive use of lambdas
*	some uses of method chaining, eg methods returning 'this'

