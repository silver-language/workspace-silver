Factorial
=========


```
	factorial : Function
		type : UnsignedInteger			// codomain
		parameter :						// domain
			number : UnsignedInteger

		result : match (number = 0)		// image/range
			true	: 1
			false	: factorial(number: parameter.number-1)
	factorial end
```
