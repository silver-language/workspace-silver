
Everything is a collection
==========================

This is something that i'd kind of wanted, but no idea how practical it might be, either in terms of implementation, or end-use.


In simple terms the idea was that one of something was simply a collection with one member.


The reasoning was that so much of the time singles end up becoming multiples, and there are whole domains where multiples are everything.

But that belies a sort of turtles all the way down approach that everything can be multiplied or subdivided, which whilst maybe true physically or philosophically, isn't realistsic for programming.
For actual programming there need to be end-points to multiplicity.


In reality what i'd probaly really need are just simple ways of easily handling one vs many, and only having to write one piece of code for one-vs-many.

It would also be nice to be able to write function signatures that don't assume one or many (or even zero).
But not sure how realistic that will be.
Something to revisit further down the track.



Have a look at the discussion in the Data section for the basics in terms of data description.




Here are some of the kinds of things I think I wanted when i originally had the idea for everything is a collection:




One function, separate strategies
---------------------------------

Functions for single and multiple processing could be identical, but strategies specified separately.

Eg in bulk processing, being able to write one function that could equally handle a single as a group.

Say you have a collection of x, and want to frobnicate them, you write this function:

	frobnicate(x)
	{
		...
	}

or in silver:

	frobnicate:
		type: function
		parameter: { x: integer }

		...


Can you have just a single function signature that will accept (within some reason) various kinds of collections of x such as arrays, lists, matrices etc?

The operation itself is same in any case.

My naive thought is to have some way of intercepting the call when strategies exist, and pattern match or whatever for the conditions (eg what the actual collection is), and delegate to an available strategy based upon that.

That way you could have different strategies for one, 1000, structs, arrays, matrices etc
But to make it properly useful you could have different strategies for daytime, nighttime, Christmas, debug, dev, local, remote, mobile, combinations thereof and fallbacks.

But the point is that the method call in your client code *does not change*.
Not necessarily at least.
This lets you lay out your high level code cleanly, and implement the contingencies separately.








