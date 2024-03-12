Integral and derivative
=======================

Standard mathematical operations that take functions as input and return functions as results.


Integral - not sure how to specify 'integral with respect to':

	integral: Function
		parameter:
			function : Function
		type: Function

		... do integral ...

		result: integral
	integral end


Derivative:

	derivative: Function
		parameter:
			function: Function
			variable: Number
		type: Function

		... do derivative ...

		result: derivative
	derivative end
