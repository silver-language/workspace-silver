a code block
------------


	sadf
	sdf
	sadf
	sdaf


named code block
----------------


	'name'
		sadf
		sdf
		sadf
		sdaf



named code block with metadata
------------------------------


	'blah'					// 'name' is variable
		metadata:			// 'metadata' is literal
			asdfsadf
			sdfasdf
			asfdsdaf
		code:				// 'code' is literal
			sadf
			sdf
			sadf
			sdaf


separate metadata blocks
------------------------


	name:					// 'name' is variable
		paramters:			// 'paramters' is literal
			asdfsadf
			sdfasdf
			asfdsdaf

		code:				// 'code' is literal
			sadf
			sdf
			sadf
			sdaf



class
-------------------------

	FooClass
		type: class
		extend:
		implement:


Function
-------------------------

	doFoo
		type: function
		return: foo
		parameter
			blah	string
			foo		number




Function Parameters
-------------------

	parameter
		name
		type		// compile time check
		required
		default
		valid 		// runtime; this could actually be a function that discriminates further than type, if no suitable subtype exists


	structure
		parameter




Structure
---------
This is sort of the most important bit.
A structure, be it an array, struct, object, function, parameter etc, needs to be able define its data and metadata.

There's also the problem of defining the  difference between the different kinds of subkeys.
A structure can have arbitratry subkeys, but depending on the type of the structure, the subkeys will be interpreted differently.

	structureName
		value1			// no or implied/generated key
		value2			// no or implied/generated key
		simpleKey:	value
		simpleKey2: value


	structureWithMetadata/properties
		metadata/properties
			type
			valid
			key
			range
		data
			value1
			value2
			key1	value


structureWithInlineMetadata
	value:

Another option might be:

	thing
		(
			metadata
			...
		)
		data
		...

But that messes up the indenting a bit


Array / anonymous collection
----------------------------
For things with no explicit keying (auto/implied etc) a few patterns arise
Use an anonymous or placeholder key, eg, with a few variants:

	* thing
	* thing
		metadata
		data
	*
		thing
			metadata
			data

But none of those are really /good/.
Regular code itself is an anonymous sequence, and code should look like


	code
		asdfasdf
		asdfasdf
		asdfasdf


So anything that doesn't have an identifier should just be an anonymous sequence entry

Which means that keyed/named structures need to be like this:

	code
		name
			stuff
			stuff
			stuff
		name
			stuff
			stuff
			stuff

And if you include metadata, it gets a ~bit~ weird:

	code
		name
			metadata
				stuff
				stuff
				stuff
			data
				stuff
				stuff
				stuff
		name
			metadata
				stuff
				stuff
				stuff
			data
				stuff
				stuff
				stuff

A concise metadata/typing syntax would help here.

But....	then how do you have an array of *structured* items?

Anonymous key, would work, doesn't look very good though

	array
		*
			stuff
			stuff
			stuff
		*
			stuff
			stuff
			stuff

Space delimited (don't really want to do this)

	array
		item stuff
		item stuff
		item stuff

		item2 stuff
		item2 stuff
		item2 stuff

		item 3 stuff
		item 3 stuff
		item 3 stuff

I like the idea of horizontal structure, but strict vertical structure, not so much.
The delimiter effectively becomes two consecutive line ends.
This looks okay, though has negative implications unless the array can be made explicit...
Eg

	data
		verb
		verb
		verb

		verb
		verb
		verb

Is that an array of six elements with some formatting, or two structured elements?
If you typed it, something like:

	data:array
		verb
		verb
		verb

		verb
		verb
		verb

It would be okay.


Structure/array take 2
======================



	qwer
	asdf
	zxcv

That's an array

	asdf
		asdf
		asdf
		asdf

That's a named subarray?

	asdf
		asdf zxcv
		asdf zxcv
		asdf zxcv
	asdf
		asdf zxcv
		asdf zxcv
		asdf zxcv
	asdf
		asdf zxcv
		asdf zxcv
		asdf zxcv

Maybe...  that could be array of arrays, though the keys mean nothing














