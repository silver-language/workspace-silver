
Name Type Value
===============

So here's the basic assignment:

	name : value

Where for most of the thinking so far value has been a string to keep it straightforward.

Now I want to add ways to denote types.
I think (and I'm pretty sure this is correct, will try to check) that -types are values-.
That would mean types go the right of the colon, like this:


	name: type value

and that a simple assignment could represent either a type or a value,

	name: value OR type

	eg

	mything : 'blah'
	mything : string

	and probably both, a-la

	mything : string 'blah'

That's okay so far, we can create literals and schemas.



Querying variables - first simple go
------------------------------------

So to use the var, the default return is the value

print mything
	blah

But what if we want the type?
The most obvious thing to do would be to use variable properties, something like this:

	print mything
		blah

	print mything.value
		blah

	print mything.type
		string

We probably also want to be able to query the name, eg if iterating:

	print mything.name
		mything


That's all simple enough, what about arrays/structs/collections?
(i'll type the array implicitly for this to make it clear)

	myShirt: array
		colour: string 'yellow'
		size:	string 'medium'

Queries could be (ommiting metadata):

	print myShirt
		{ colour: 'yellow'; size: 'medium'; }

	print myshirt.type
		array

	print myShirt.colour
		yellow

	print myShirt.colour.type
		string

	etc


Reserving very common words
---------------------------

This scheme would imply reserving some very common and useful words, and would force the coder to munge 'name', 'type' and 'value' into longer things like:

	personName
	productType
	itemValue

This might add clarity, but could be overbearing sometimes.
A neat metadata syntax might be nice, eg something like one of these:

	myShirt!type 		hints at a meta-dot; hard to read imo
	myShirt@type		attribute? also hard to read
	myShirt^type		not too bad, fairly easy to read
	myShirt~type		not too bad
	myShirt_type		don't like; half the world uses them in varnames
	myshirt.meta.type	the original idea I had, not too bad, reserves 'meta', could get wordy

Of those, the best are probably tilde, caret or 'meta'.
I'd probably start with 'meta', because i want the base language to be very readable.


Querying using metadata syntax
------------------------------

Basic values don't change:

	print myShirt
		{ colour: 'yellow'; size: 'medium'; }


	print myShirt.colour
		yellow

Querying metadata changes, examples:

	print myShirt.meta.type
		array

	print myShirt.colour.meta.type
		string

Or with a shortened syntax:

	print myShirt~type
		array

	print myShirt.colour^type
		string

In use both look a bit ugly tbh, and not really obvious.
Anything simpler?
Another idea ..

	print myShirt..type
		array

	print myShirt.colour..type
		string

That's actually not too bad.
How a printFull probably would work something like this:

	printFull myShirt

		myShirt:
			..name: myShirt
			..type: array
			colour:
				..name: 'colour'
				..type: 'string'
				'yellow'
			size:
				..name: 'size'
				..type: 'string'
				'medium'

But that's kind of awkward, I'm not sure the best layout yet.
Will have to think about it.
It might be useful to inlude a 'value' key in the metadata to make it clearer, but that would have to be done carefully to manage/avoid circular references.


Outcomes
========

All values have at minimum three properties:
	name, type, value

Though name may be undefined/automatically generated.

Reserved keywords:
	name, value, type
	OR
	meta
	OR
	a meta operator such as ..


