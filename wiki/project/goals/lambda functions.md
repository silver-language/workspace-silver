References:
===========

Anonymity (bad):
	https://youtu.be/OLH3L285EiY?t=446



https://www.quora.com/What-are-the-benefits-of-lambda-functions

	What are the benefits of lambda functions?
	12 Answers

	Alex Seewald
	Alex Seewald
	Answered Jun 13, 2017 · Author has 519 answers and 557.7k answer views

		Wouter’s answer to this question contains the most important thing to know: that lambda functions allow you to abstract and hold onto an expression involving bound and free variables. There are many valuable consequences of this, most being obvious, so I’ll mention a weird one. Having lambda functions allows you to write programs in Continuation Passing Style (CPS). CPS is a difficult concept to wrap your head around, and you could easily go your whole life without knowing about it, but there is a valuable consequence.

		Think about what an interpreter would have to do with a typical style of recursive binary tree search: the existence of two recursive steps in the middle of a function makes you have to recursively keep track of control and the states of all the variables throughout the whole history of where control has been (so control can return correctly after a particular recursive step has terminated). Reformulating recursion with tail-calls (single recursion at the end of a function) is the solution to the efficiency problem (because your function can be equivalent to a loop instead of a growing stack), and CPS is a way of automatically getting a tail-call formulation when doing complicated stuff with control.

		If you have an interest in understanding why that is true, you should probably read an introduction to continuations. The only approachable and sufficient explanation of CPS which I could find when learning about them myself is chapter 6 in Essentials of Programming Languages.
		1.2k views


	Wouter van Oortmerssen
	Wouter van Oortmerssen, Programmer
	Answered Oct 25, 2012 · Author has 52 answers and 132.5k answer views

		The power of lambdas doesn't come from the fact that they're anonymous (that's a mere convenience), but because they tend to allow free variables (in almost any language that supports them). That gives the functions that take lambdas as an argument (higher order functions) the power to function as a user defined control structure, e.g.

			a = ...
			map(lambda(x): x + a, list)



		here, a "a" is a free variable, i.e. a variable not defined inside the lambda, but in a surrounding scope. Note that without such variables, a function like map() would lose all its power, because it would mean you can only perform static transformations on lists, as opposed to transformations that depend on the data you're currently working on.

		More abstractly, free variables allow you to abstract the middle of the call graph. Normal functions allow you to abstract only the leaves of the call graph. Think about it, when you create functions, you do so because you find repeating patterns in your code, and you don't want to write it twice (copy & paste). Only being able to abstract the leaves is seriously limiting, it means you can't create functions where the leaf is the unique part and the part above it the repeating pattern.

		Yet another way to see it is that lambdas allow you to abstract out arguments where the execution frequency is 0..N. A normal function argument has an execution frequency of exactly 1, since it is always evaluated once. If how many times an argument is evaluated has to be decided by the function it is passed to (which is often the case if that argument is used inside a loop or something), then in a language without lambdas, it cannot be passed as an argument, which means you have to copy paste that loop (or use macros :)

		You can emulate the effect of lambdas in languages that don't have them with objects that have a special method, and sticking free variables in that object, but the resulting code is often orders of magnitude larger than the lambda equivalent, so doesn't get used as often.

		A language without lambdas (& free variables) is an incomplete language.
		8.1k views · View 20 Upvoters
