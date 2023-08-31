
Funtions
========

Trying to figure out how a function declaration could work.



Funtion type definition
-----------------------

	function: type
		parameter: struct
		result: block
		returnType: type

not sure that's right at all, might taker a few goes





Function declaration
--------------------


foo : function
	parameter: type {}
	result: {}
	returnType:


foo : function
	parameter: {}
	result: {}
	returnType:


The return type and parameters are both typed so maybe could do something like this

foo: function
	parameter: array {}
	result: type {}


Slow down
---------

Before i run too far ahead just want to break this down in to easy to understand bits.

	foo..type = function				// foo itself is a function
	foo.parameter..type = array			// its parameters are an array of some sort
	foo.result..type =					// whatever is declared in the function defintion

Let's have a little chat about result.
Some piece of the function defintion defines what gets returned, so this piece of the function could be fairly equally be called any of these:

	value
	result
	return
	output

I'll have to decide on one, my prefs right now are for value or result, probably not output as it tends to have slighlty different meaning in computing circles. I don't like return as it's too imperative.


result: (the type of this is a block or array - how do we define the type of the actual result? )
	sadf
	asdf
	asdf
	asdf

We'd need another way of defining the returnType of the function, so to revisit my earlier attempt

foo: function
	parameter: array
	body: codeBlock	| value		// something like that anyway
	result: type

You'd probably need to either add and explicit result type item to the function array, or define a particular type of codeblock (or somesuch) array that requires defining a resultType, by say requiring a result item.
The latter, if used alone would bury the result type too deeply, so the result field for a function looks better at this point.

Unfortunately this doesn't look like it's super conducive to really terse function defintions, but I'm not too concerned about that just at the moment.

	foo..type		= function
	foo()..type		= function.result..type

For this to work theere also needs to be a way to declare what the result of the function body is.
Lets' try some things. I'll pretend we can use maths


factorial: function
	paramter: { number}





