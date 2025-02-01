Simple API
==========



So while I'm here and I'm thinking about it I'm going to do a little braindump.

The thing that I think that I want (and i might be th only person on earth to want this) is actually a far simpler api that relies more on options that methods.
Now there are probably very good reasons for creating a very low-level granular api in terms of control, and writing smaller, tighter methods.

But in terms of concept space it seems cluttered to me.
I kind of feel like reading a directory should be a single method, but with a way of specifying all sorts of filtering and nesting options.
It's one of those things that maybe there are nasty pitfalls for that I totally dont know about...

So for instance, take the read directory thing. If i had lots of options they be something like:
	name
	name regex
	extension
	recursive
	data return
	fail-on
	skip errors
	permissions
	newer-than
	owner
	expressions: and, not, greater than, union etc
	...etc

So you start building up a set of options like this to tackle every possible way to read a directory.
And I think i can see where this might be going:
	The interactions become difficult to predict.
	Fine grained control becomes difficult, especially cross-OS.
	Very specific queries become hard.

So what initially seems like a simple idea can quickly become complicated, but I still feel like there  might be lots of cases that aren't that complicated at all.


So what are the options here?
	Only provide the micro api and force the programmer to program the query?
		Every directory operation might end up quite verbose, and nearly the same, but not the same enough to make reuse easy.
	Only provide the macro api, and force developers into the paradigm you've created, and no doubt miss some options/facilities?
	Provide both a macro and micro api to allow for ease _and_ flexibility?
	Figure out if there's a way to turn the macro api query into a dsl so that complex queries can be done, but the whole complexity of language isn't exposed?

The last - DSL - is the closest to what I think the ideal would be.
But providing both macro and micro api would be next best.

DSL
---
So the DSL - what could it be like?
It might end up being something like basic SQL in this particular instance:
	Candidates to select from
	a set of predicates that must be true of the selections
	specifics about the selections to return

One of the potential benefits of a DSL - and especially silver-data based dsl - is te potential for easy composability, which is one thing I always find frustrating about code-based approaches.
It's nearly the same thing, but I find composing in code based scenarios forces you to know and utilise the features of the language - writing things in functions, parameters and return types just right etc.
I don't know for sure yet, but i feel like composing in data might be more straightforward.





The real problems about file systems
------------------------------------
Every can and will fail.
I think that's what Rust's api is conveying.






