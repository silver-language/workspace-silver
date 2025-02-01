Values
======
What constitutes a value?
When is a value actual vs symbolic?



This is a kind of follow on from a couple of different lines of discussion.

	Arrays of anonymous structures
	schemas/types

Let start with the basics:

	name1: true			// a boolean
	name2: 42			// a number
	name3: 'foobar'		// a string

Those are all pretty straightforward.
What if i do this:

	name4: xyz

No-one knows yet what xyz is. It might be a variable, it might be a string.
Without further information or context it's hard to say.

Let's pack these into a structure/array:


	myobj:
		name1: true			// a boolean
		name2: 42			// a number
		name3: 'foobar'		// a string
		name4: xyz			// ???

Same rules apply, we don't know what xyz is, but each member of the structure at least has a name.

Let's remove the names - this makes things harder to interpret:

	myobj:
		true			// a boolean
		42				// a number
		'foobar'		// a string
		xyz				// ???

At this point things start to get a bit hazy.
Are we sure about the first three? It will come down to the parser after all...
And without a schema of some sort it's a pretty rough guess.
We can say pretty confidently that the object has 4 anonymous values though.

So without any other type information we could call everything a string or use a few basic rules for primitive types and that would be about as far as we could go with that sensibly.

But the point here is that without a colon ("name:"), it's a value.
Or maybe even an expression.












Example of array of anonymous structures:


	collection:
		item
			name:	'a'
		item
			name: 	'b'
		item
			name:	'c'

In this case each 'item' represents a value of some sort.
Without any more context, it's hard to say what.
