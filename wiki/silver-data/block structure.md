

Block structure
===============



The presence of colons
----------------------


Are these 2 examples the same or different:


1.

	product1:
		id: 1234

		tag:								...has a colon
			new
			great
			fantastic

		price: $9.99


2.
	product1:
		id: 1234

		tag									...does NOT have a colon
			new
			great
			fantastic

		price: $9.99




The only difference being in the 'tag' blocks, one has a colon, one does not.

Normally something without a colon denotes a value, as in the tags ('new' etc) themselves.
But can a block be anonymous, and if so how would you denote it, and how would you interpret the first example?

The idea of anonymous blocks isn't bad, after all you'd need to be able to create colelctions of anonymous (auto-indexed) objects - doing so in brace syntax makes this clear and simple:

	product-collection:
		{
			name:	product1
			id:		1234
		}
		{
			name:	product2
			id:		2345
		}

Note the extra indent level would have to be there if the parent collection didn't use braces.
Doing the same construct without braces.... what could you do?


	product-collection:

		name:	product1
		id:		1234


		name:	product2
		id:		2345


That's not going to work out well for anyone... obviously I'm on-board with horizontal whitespace being semantic, but vertical... that's a bridge too far.
Double indenting?

	product-collection:

			name:	product1
			id:		1234

			name:	product2
			id:		2345

Nah i'd prefer to avoid that, don't like it.
What else could you do?
Couple of ideas - specifically anonymous block starts/ends

	product-collection:
		block
			name:	product1
			id:		1234

		block
			name:	product2
			id:		2345

In that construction the 'block' name is a keyword used to denote a block start, but without creating a name.
If you stipulated that block was ~not~ followed by a colon, that would actually make a fair bit sense, as the 'block' becomes the value.
That would also open up the door for other kinds of things that there were defined types for (just running with the idea for sec here...)

	strategy-set:

		function
			parameter: { name:x; type:integer }
			... implementation 1 ...

		function
			parameter: { name:x; type:integer }
			... implementation 2 ...

That way you could define a group of anonymous functions for trying against each other.
Going back to the previous example, if you'd defined the product type elsewhere you could do this:

	product-collection:
		product
			name:	product1
			id:		1234

		product
			name:	product2
			id:		2345

Which really isn't too bad at all to be honest.

And to be clear, this is roughly equivalent to:

	product-collection:
		{
			type:	product
			name:	product1
			id:		1234
		}
		{
			type:	product
			name:	product2
			id:		2345
		}

Though those two could still be interpreted differently depending on circumstances.
Ie, if the type property was properly mapped to the type system, then they would be the same.
If the type-mapping was disabled for whatever reason, the type property would just be another string.
For argument's sake the former might be the case in silver-language, but the latter in silver-data.
So it would be context dependent.


Does this shed any new light on the single member block (composability and multiplicity) discussion iwas having in everything-is-acollection?
