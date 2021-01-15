Metadata
--------

This is one of the core tricky things.

I want to be able to declare metadata in some cases, and not sure the best way to do it.

There's also the philosophical issue of what's metadata, and what's simply 'data'.
In a really basic sense everything is just data, but there are times when it's useful to organise data into categories or heirarchies, things of relevence to different concerns.
So for a simple example data might be things the user or programmer cares about - *their* data, whereas metadata might be the things the compiler or program cares about.
But the distinction is a little bit arbitrary, and maybe a bit binary.
What about quasidata, hyperdata, uberdata, shadowdata, nanodata and omnidata?
It's turtles all the way down you know...
So maybe a way of categorising or tagging might be better.


Some examples
-------------

A simple function 'foo':

	foo
		type: function
		parameter:
			i:
				type: integer
				description: this is i
			j:
				type: boolean

		result: i + j
	end foo


In the case of a traditional old-school programming language function, the fist stanza might be considered the 'metadata', and the function body the 'data'.
Still a bit arbitrary though.



Match
-----
A second and more pertinent example might be my mythic 'match' function that I'm trying to realise (and demangle).

At a first brush the traditional function signature might like this:

	match(
		subject	: { type: object } 		// thing to be tested for matches
		match	: { type: object { matchExpression: function } }	// match expressions and their code
		option	: { type: object }
	)

I've probably cocked up the match type expression, but you get the idea.
Demangled I want it to look like:

	subject match
		matchExpr1 : function1
		matchExpr2 : function2

		??? option ???

But where then do the options go? You could of course go the more verbose route:

	subject match
		match:
			matchExpr1 : function1
			matchExpr2 : function2

		option:
			...
			...
			...

But for such a core method I'd rather not end up with clutter like that.
So if a demangleable (new word yay) function has a subject and object, what about a residual?
The part of the function that isn't one of those two things?
And some way of specifying that - that is the tricky bit.
Here's some random syntax explosions:


	subject match
		( options... )
		matchExpr1 : function1
		matchExpr2 : function2

	subject match
		{ options... }
		matchExpr1 : function1
		matchExpr2 : function2

	subject match
		[ options... ]
		matchExpr1 : function1
		matchExpr2 : function2

	subject match
		< options... >
		matchExpr1 : function1
		matchExpr2 : function2

Honestly of all of those, the brace syntax looks to be the least bad and potentially most obvious.
You could even stick it at the bottom, and the meaning wouldn't be all that different:

	subject match
		matchExpr1 : function1
		matchExpr2 : function2

		{ options... }

But, it would be weird in places where the object was an object literal.
So lets try plus:

	plus(subject, object, option)

	thing plus
		{
			a:1
			b:2
		}

		{
			overwrite:false
		}

There needs to be a sensible set of rules or guidelines around this.
