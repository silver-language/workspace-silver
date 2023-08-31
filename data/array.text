


An array is the most basic structure, it looks like this:


	myArray:
		foo
		bar
		4356
		'blah blah blah'
		etc


Where any of the items may be literal or references as context dictates.
None of the child items have explicit keys, but are given implicit or 'natural' keys, so you can rewrite the above with the same meaning as:

	myArray:
		1 : foo
		2 : bar
		3 : 4356
		4 : 'blah blah blah'
		5 : etc


So how are the indexes/keys generated?

Generator functions can be provided that, but the default will simply start at one and add one to the previous value, and you can seed the generator by doing this:

	myArray:
		1: foo
		bar
		4356
		'blah blah blah'
		etc




Arrays of structures
--------------------

How do i have anonymously/automatically named structures?
Do i have to revert back to brace syntax for that?

people:
	1:
		name: ...
		address: ...
		phone: ...

	2:
		...

people
	{
		name: ...;
		address: ...;
		phone: ...;
	}
	{
		...
	}

Ahh - see 'block structure' - i have disscussed this problem a bit.
The solution I ended up at was to use semi-anonymous value markers something like this:

people:
	person
		name: ...
		address: ...
		phone: ...

	person
		name: ...
		address: ...
		phone: ...


In this case person without colon after it denotes a value, not a name.
This deserves some more discussion, as it impacts on good and bad syntax and schema/typing.


