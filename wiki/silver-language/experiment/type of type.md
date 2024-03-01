Type of type
============

I was thinking about this last night, thought I might have hit an inconsistency with generics, need to explore.


Suppose a function that takes a generic type as an argument:


	logger: function
		parameter:
			thingToLog:	type
		result: thing

		[log the thing]

	logger end

Hmmm no i dont think that was it. And that function can't work like that. Well it could, but it would be clunky.

There was a circumstance I thought I thought of where you needed a declaration in the form:

	myType : typeOfMyType actualTypeofMyType

But I can't remember right now.
If this is needed or implied anywhere I'll have to deal with it.
I think it had to do with generics - maybe that's why I was considering generic functions, as the parameters will form something like this, albeit in two parts.
A type paramter in a generic function will form a supertype that the argument type must conform to.
