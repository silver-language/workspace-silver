Factorial
=========


```
	factorial : Function
		parameter : Integer number		// domain
		type : Integer					// codomain
		result : match (number = 0)		// image/range
			true	: 1
			false	: factorial(number: parameter.number-1)
	factorial end
```