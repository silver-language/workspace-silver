

Keyword Order
=============

Simple question:

	keyword name

	or

	name keyword

	??


Eg say i want to loop over a collection (i don't even know yet what the syntax for this might be...)
Would it better to say

	loop myCollection
		...
		print(current)
		...

or

	myCollection loop
		...
		print(current)
		...


Not sure yet, each is good in it's own way.
Generally I'm a fan of big-endian, which in the context of silver means putting the most important thing first.
Hence things like

	foo:
		type: function
		...
	end foo

Now i haven't really decided on the 'end' thing yet, it could equally be these also:

	foo:
		type: function
		...
	foo end

	...

	foo:
		type: function
		...
	end

	...

	foo:
		type: function
		...
	foo



The point off all of these is that the *name* of the function (or thing, whatever it is) is the most important, and goes first.
That is the sense that it is big-endian.

So then does that mean we *always* put the name first?
In the case of the block delimiter I'm actually slightly inclined to the 'end foo' syntax because it makes it clear that the second foo isn't another item in the same scope of the parent block, but that might be surmised by the context.
Take this totally made up class-like construct for example:

	widget:
		type: class
		name: 	{ type: string }
		id:		{ type: integer }

		getName:
			type: function
			result: instance.name
		end

	end

Here, with surrounding context in place the inner 'end' can be seen at the same block level as the class's private members.
(There are other constructs and situations where having an explicit end would be helpful)
Doesn't look too confusing like that, but it's a pretty small bit of code.
The idea was though to be able to name the block that's closing, similar to xml, so that in long code runs it's clear.
So we have these choices, keyword first:

	widget:
		type: class

		name: 	{ type: string }
		id:		{ type: integer }

		getName:
			type: function
			result: instance.name
		end getName

	end widget


... or name first:


	widget:
		type: class

		name: 	{ type: string }
		id:		{ type: integer }

		getName:
			type: function
			result: instance.name
		getName end

	widget end


Seeing them in practice I'm now flipping and leaning more towards name-first.
To me, it looks more declarative, whereas the keyword first looks more imperative.


Loop end
--------

I should try some other constructs and see what they might look like.
How about the loop construct we started with?


	myCollection loop
		...
		print(current)
		...

That's okay on its own, but again it's short.
How do we explicitly close the loop?
Well first, the loop block is currently anonymous so we can't use a block identifier.
So as written we could just do an anonymous end, or maybe introduce a construct end:

	myCollection loop
		...
		print(current)
		...
	end

...

	myCollection loop
		...
		print(current)
		...
	loop end

... or even:

	myCollection loop
		...
		print(current)
		...
	myCollection loop end


But that looks a bit heavyweight. Depends on what automatic identifiers i generate.
With a block identifier it would look like:

	myLoop: myCollection loop
		...
		print(current)
		...
	myLoop end


Haha but does this raise an ambiguity about blocks... say i try to rewrite it like this:


	myLoop:
		myCollection loop
			...
			print(current)
			...
	myLoop end

These appear to have subtly different meanings so far, unless I can clear it up.
This might actually go back to block syntax itself, eg are these the same or different:

	foo: bar

...

	foo:
		bar





