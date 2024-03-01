Function types
==============

I've been wondering about this lately, so want to have a little tinker.
This is related to type-of-type, but a bit more specific.


Take my current idea of what a function would look like:

	addOne: Function
		type: Integer
		parameter:
			x: Integer
		result: x + 1
	addone end


(Also, at the moment I'm toying with the idea of capitalising types - will see how it goes)


The function type here is a name for compound type that looks something like


Function: Type
	type: Type
	parameter: Array of Parameter
	result: Any

(I'm not yet sure how to define Parameter)
