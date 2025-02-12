
Conditional
===========

The classic conditionals

	if (then, else...)
	?:
	switch/case

Ideally i'd rather go with a more general approach like pattern matching
https://en.wikipedia.org/wiki/Conditional_(computer_programming)#Pattern_matching


	match value
		test1
		test2
		test3
		... etc



Match syntax
------------

	match [thing to be tested]
		match condition
			code to be executed
		match condition
			code to be executed
		match conditions
			code to be executed
		match conditions
			code to be executed



That would be fine for basic stuff, but there might be other kinds of things that would be nice that might require more syntax/metadata.
For example:

* a default case if nothing else matches, akin to an 'else'
* a way to specify match all, or match first, or other kinds of things
* anti-match: kind of like an 'else' or a 'not'
* a way for the match to be an expression of some sort, ie not literal

Metadata
--------
And this is kind of where the metadata question comes in...
How can i easily and succinctly embellish or decorate simple language contructs?

Usually a structure is

	key
		[key:] value
		[key:] value
		[key:] value

In a match, the 'match' is the value, so there's a syntax problem here that needs to be resolved.
So we




