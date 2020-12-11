

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



