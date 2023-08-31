Assignment
==========

The general idea is to be declarative as far as possible rather than imperative.
So for example, in many languages:

	x = 2

Means assign the value 2 to the variable x.
It's kind of an operation, an action, a verb.

In mathematics, however it's a statement of fact or truth, so it's a boolean expression.
I'd like to retain the mathematical idea, and come up with something different for assignment.

The best option I can come up so far is a colon, a-la

	name : value

This falls in line with other more declarative or data style formats such as json.
It say name IS value, though to be fair, once you know what it is doing it could be read either way.
But I'd prefer to steer away, as much as is reasonable, from thinking imperatively.

So that is the the one line version of assignment.
What about where the value is complex, such as a structure?

This is the form I like:

	name
		foo : value
		bar : value2

In that case the colon after 'name' is optional, but redundant.
I think, though I'm not sure yet, that I'd like whitespace around the colon.
	(Just in case I decide that contiguous non-whitespace can amount to a single identifier)

Note (and this needs to be clarified) that not just anything can be the name.
If it is a reserved word, then other parsing rules apply.
If the token isn't found, then it's a structure.


Update
------
In the example given above the colon is now required:

	name:
		foo : value
		bar : value2

A line without a colon is a value (a type and/or an expresssion), so in the earlier example 'name' could be a type, but would be meaningless as say a literal.



Outcomes
========

Assignment of a single value

	foo : bar

Assignment of a compound value

	fooCollection:
		foo1: bar1
		foo2: bar2
		foo3: bar3


Equality comparison - this is a boolean or truth statement

	foo = bar










References
==========
https://en.wikipedia.org/wiki/Assignment_(computer_science)#Assignment_versus_equality
