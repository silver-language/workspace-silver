
Name - Colon - Value
====================

The basic assignment uses the pattern 'name:value'.

	foo: 1

	collection:
		member1 : hello
		member2	: world


Does it, or could it, make any sense to stack colons?

	foo: bar: 1

Written like that the interpretation is pretty obvious, but is that something we would want?



Equals sign
-----------
Can be used for actual equality expressions.


Types and schemas
-----------------

I need a way to specify type also...




No colon
--------
This is where things get a bit interesting. Take the simple collection above:

	collection:
		member1 : hello
		member2	: world

Anything to left of the colon is the name. What if we take the member names away:

	collection:
		hello
		world

The most obvious reading is that 'hello' and 'world' are values in 'collection', and that's what I want.

This means:
	lines without colons denote values
	the values are effectively nameless (for the time being at least)

It also mean you can't leave off the colon on a block assignment like this if you want a named array:

	collection
		member1 : hello
		member2	: world

In that style 'collection' becomes a value... and as I've discussed elsewhere a pretty handy use of this would be to denote a type.
But I'd better sort that out properly - see 'name type value'.



Wrapup
------
This has been resolved elsewhere - am moving to a done task to get it out of the wiki.
