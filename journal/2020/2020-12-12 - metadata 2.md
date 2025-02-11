
Metadata
========

This follows on the from some of the thoughts in ../data/name type value.text
I was just getting started in there, want to flesh out the thought experiment, see where it leads.


In looking for ways to avoid reserving useful words like name, type, value I was toying with adding a metadata substructure to all values.
The syntax i disliked least was either a special 'meta' key, or alternatively two dots, eg


	name.meta.type
	name..type

Wherein the keys 'type' and 'name' would be stored

	product: string 'cornflakes'
	price: number 4.99

Metadata could be accessed like this:

	print product..type
		string

	print product..name
		product

	print price..type
		number


I wasn't sure about arrays - had a couple of different ideas about how it could work, need to throw this around.

	product:	type
		name:	string
		price:	number

	1234: product
		name:	'cornflakes'
		price:	4.99

Which reminds me I really need a way to specify multiplicity...




Complications
-------------

This all looks fine so far, but there will be complications.
For instance some metadata might be user controllable, and some might be controlled by the program.
A simple example is array length, if the array is mutable.

	myArray: array [1...] of number

This is an unbounded array so it can grow dynamically.
The array at a given point might look like:

	myArray:
		..
			name: myArrray
			type: array
		1
		2
		3
		4


But we need to add in the key constraints, and maybe length, so it might look a bit like this:

	myArray:
		..
			name: myArrray
			type: array
			length: 4
			key:
				first: 1
				last: undefined
			value:
				first: ->1
				last: ->4
		1
		2
		3
		4

So already a bunch of questions...
	Can the metadata fields have metadata?
	How do we know what are user defined and what are managed by the program?
	How do we break down multiplicity?
	Plus we're probably going to need pointers/references to implement things like first, last, before, after etc



Can the metadata fields have metadata?
--------------------------------------

The answer to that almost certainly YES.

Take an array like the one above, and the length property.

To read it directly you go

	myArray..length		= 4

But it's a value so these also exist

	myArray..length..name	= length
	myArray..length..type	= cardinal
	myArray..length..value  = 4


or
	myArray..length
		..
			name: length
			type: cardinal
			value: 4

So I think this will probably mean every structure will probably expand down to a basic single-valued metadata array like this.
It could definitely go further though - for instance you could query the properties of the name key:

	myArray..length..name..type	= arrayKey		(or whatever the appropriate key string type is for this array)

Or the cardinal type:

	myArray..length..type..name = cardinal		not really sure yet..

At this point it becomes practically certain that we'll need references of some kind - there's no way these can all be own properties.
For example nearly all types will probably be references to their definitions elsewhere.


