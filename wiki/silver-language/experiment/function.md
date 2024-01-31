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
		result.type: resultType
		parameter:
			param1 : type1
			param2 : type2

		--- do some stuff ---

		result: resultValue
	end functionName