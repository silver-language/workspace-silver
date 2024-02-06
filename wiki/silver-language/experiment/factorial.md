

factorial
=========


First go:
---------


	factorial
		metadata
			type: function
			parameter
				x
					type: integer
			result
				type: integer
		data
			value x
				1
					result: 1
				default
					result: factorial(x-1)



Well that's a bit ugly.
What else can we do....


	factorial
		type: function
		parameter
			x
				type: integer
		result
			type: integer

		value x
			1
				result: 1
			default
				result: factorial(x-1)



What if we, just for now, make the key colon mandatory:

	factorial:
		type: function
		parameter:
			x:
				type: integer
		result:
			type: integer

		value x:
			1:
				result: 1
			default:
				result: factorial(x-1)


That's a little better.


What if result was actual body???

	factorial:
		type: function
		parameter:
			x:
				type: integer
		result:
			type: integer
			value x:
				1:
					result: 1
				default:
					result: factorial(x-1)






Return after a while
--------------------
Have another go...


	factorial: function
		parameter: integer number
		result: integer number * factorial(number: number-1)


I'm still not really sure how I want the body/result to work.
I don't think I can use the result delaration as result could be either a type or value...
That also ignores the zero case. I'll try an experimental match syntax:


	factorial: function
		parameter: integer number
		result: integer match (number = 0)
			true	: 1
			false	: factorial(number: parameter.number-1)
	end factorial


That looks like it will work in this case, though the function body still needs work.
Also, and this might be a technicality, but factorial might not be strictly pure like this?
Does a reference to itself need to be passed in or is that getting too pedantic?
Not sure, might be able to include self in scope.



If I incorporate latest thoughts on return type:

	factorial: function
		parameter: integer number		// domain
		type: integer					// codomain
		result: match (number = 0)		// image/range
			true	: 1
			false	: factorial(number: parameter.number-1)
	end factorial