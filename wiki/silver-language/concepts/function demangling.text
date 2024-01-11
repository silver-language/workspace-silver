
Function demangling
===================

This is something i've started to think about in
	subject first
	metadata

But it's a big enough topic to be treated separately.

The idea is that given the right conditions (yet to be determined) functions can be turned into expressions or operators.
Some simple examples...

plus:

	plus(left, right)

	becomes:

	left plus right


if:

	if(condition, action)

	beomes:

	if condition
		action




match:
	match(subject,[{expression,payload}])

	becomes:

	subject match
		expression1: payload1
		expression2: payload2
		...




So what you'd need is way to tag and annotate a function so that it can be turned into a more natural looking construct like a control flow expression or an operator.

You'd need a way of defining a grammar that you wanted, something like

	plus:
		type: function
		parameter:
			left:
				type: integer
			right:
				type: integer

		grammar: left 'plus' right


But there could be a hundred ways to do it - finding the right one...

F




ref
---
https://programming.guide/statements-vs-expressions.html
https://therenegadecoder.com/code/the-difference-between-statements-and-expressions/
https://en.wikipedia.org/wiki/Operator_(computer_programming)
