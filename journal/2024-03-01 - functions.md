Functions
=========

I'd like to initally distinguish between functions and procedures.
Methods in the OO sense would need to be clarified, depending on the how the scope inclusion occurred.


Function Types
--------------

### Functions

https://en.wikipedia.org/wiki/Function_(mathematics)

* Pure - strictly map input to output
* Have no side effects
* Memoizable
* Have no variable hidden state, ie no closures
* Can be anonymous (lambdas)
* Will be idempotent
* Can only call other functions to preserve these properties
* Single-valued outputs


### Procedures

* Everything else
* Can have side effects
* Not usually memoizable
* Could include closures
* Could maybe reference outside scope, eg object methods
* Not necessarily idempotent

Distinguishable from procedures


https://www.youtube.com/watch?v=O2lZkr-aAqk&list=PLbgaMIhjbmEnaH_LTkxLI7FMa2HsnawM_&index=3


### Methods
* Could be pure (functions) if the relevent parts of the object scope were passed in, and no mutation occurred.
* Procedures attached to objects


### Other

Other names for executable units of code:
* routine/subroutine
* closure
* program


Function Properties
-------------------

### Pure

https://en.wikipedia.org/wiki/Pure_function
* Identical output for input
* No side effects

I'd like functions to be pure, and if one of these properties exist but not the other, a different type is used, eg procedure but with additional properties.


### Side-effects
https://en.wikipedia.org/wiki/Function_(computer_programming)#Side_effects


### Idempotence

Can the function be run repeatedly without changing the result

https://en.wikipedia.org/wiki/Idempotence




### Associativity & commutativity


### Set mapping

input type - domain

ouput type - codomain (type) or image (allowed values)

https://en.wikipedia.org/wiki/Bijection,_injection_and_surjection


Injective:

	every input has a unique output
	no collapse in codomain;
	there may be unmapped members in codomain
	codomain > image (can be)

Surjective:

	every output is mapped to an input
	image covers complete codomain;
	image = codomain (manadatory)

Bijective

	(?isomorphic/isomorphism) - both injective and surjective
	reversable
	1:1 complete unique mapping



?invertable

Can any of these be expressed by a type system?


### Single-valued output

This will need clarification, as the notion of 'value' isn't always clear.
For example are vectors single values or composites.



Purity
------

I'd to distinguish between functions and procedures, but not yet sure what the best way to do that is.



The thing i have in mind is that I want a function to be 'pure',

	https://youtu.be/O2lZkr-aAqk?list=PLbgaMIhjbmEnaH_LTkxLI7FMa2HsnawM_&t=243
	A pure function is memoizable



No side effects, only operates on parameters.

If you want side effects, or scope, you want a procedure (or subroutine).


I'm not sure if that is better as a base rule of the language:

	factorial: Function			// where 'pure' is implied

	print: Procedure			// where the rules are relaxed


Or as function metadata:

	factorial: Function
		pure: true				// pure is a particular property of specific functions

	print: Procedure
		pure: false				// where the rules are relaxed


If you allow type literals something like this could be done in the type system:

	Function: Procedure
		pure: true
		...

Which could read something like Function is a procedure that the pure property fixed to true.



The ultimate i think would be being able to define a nice set of properties of things like functions and procedures --in the language itself-- like the second, then use the first thereafter.
This could then be the default, but allows for changing the behaviour for advanced requirements.

Each folder could have an optional '.silver' directory where behaviour could be overridden/changed.




Function/Prcedure type heirarchy
--------------------------------

A type heirarchy for functions and procedures could be speculated.


Procedure

	Function - if pure

	Closure - if hidden state included

	Method - if attached to an object







