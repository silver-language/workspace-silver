Function
========


simple function
---------------

	functionName : function
		parameter: paramType paramName
		result: resultType resultExpresssion
	end functionName



more complicated
----------------

	functionName: function
		parameter:
			param1 : type1
			param2 : type2

		--- do some stuff ---

		result: resultType resultValue
	end functionName

This could work, though it differs greatly from the way most languages put the return type in the signature.


function metadata
-----------------

Should the parameters or the result type be part of the metadata?
For example would something like this make any more sense?


	functionName: function
		..result.type: someType
		..parameter:
			param1 : type1
			param2 : type2

		--- do some stuff ---

		result: resultValue
	end functionName

I think I'd have to do a bunch of concrete examples to see if that's any better or worse.
At least it puts the return type at the top.
I suppose you could do that without the metadata though:


	functionName: function
		result..type: resultType
		parameter:
			param1 : type1
			param2 : type2

		--- do some stuff ---

		result: resultValue
	end functionName


While this does sort of make sense, it kind of obscures what's actually happening:
	* result..type is intially mutable
	* result..type is a supertype of whatever the actual result type is
	* setting the result finalises the value return and type of the function


Type as an ordinary member
--------------------------

Hang on a sec, why shoudn't type just be an ordinary member of the function struct?
I made the metadata struct (amongst other reasons) so that the keywords name, type and value could be used in user defined structures, so why not just use type...


	functionName: function
		parameter:								//	domain
			param1 : type1
			param2 : type2
		type: resultType						// codomain

		--- do some stuff ---

		result: ?resultType? resultValue		// image/range
	end functionName

That makes much more sense.

For that matter any other function modifiers such as visibility, mutability, lifetimes, purity (maybe) could be added in much the same way (if they weren't required in the core of the language).




Type expressions for subtype
----------------------------
This gets a bit harder.

Often a function will accept anything that fulfills the contract of the parameter types, so subtypes,subclasses etc.
Need a way to make this clear, but this falls into the space of type expressions.