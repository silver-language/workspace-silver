References
==========

I need a way to include references to other structures/values.
A simple examples is an array that has meta-references to certain members, eg



	myArray:
		..
			name: myArrray
			type: array
			length: 4
			key:
				first: 1
				last: undefined
			first: ->1
			last: ->4
			before: ???
			after: ???
		1
		2
		3
		4



The last four metadata keys are references to places in the array

	first: ->1
	last: ->4
	before: ???
	after: ???

Also the array type will be defined elsewhere, so that will have to be a reference also.

How do we do this?
Do we need any special syntax?
Do we need to consider privacy/visibility/mutability for this?
