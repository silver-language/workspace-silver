purity
======


I'd to distinguish between functions and procedures, but not yet sure what the best way to do that is.



The thing i have in mind is that I want a function to be 'pure',

	https://youtu.be/O2lZkr-aAqk?list=PLbgaMIhjbmEnaH_LTkxLI7FMa2HsnawM_&t=243
	A pure function is memoizable



No side effects, only operates on parameters.

If you want side effects, or scope, you want a procedure (or subroutine).


I'm not sure if that is better as a base rule of the language:

	factorial
		type: function			// where 'pure' is implied

	print
		type: procedure			// where the rules are relaxed


Or as function metadata:

	factorial
		type: function
		pure: true				// pure is a particular property of specific functions

	print
		type: function
		pure: false				// where the rules are relaxed




The former is terser, and would be nicer to the reader, but the second is more flexible, and allows
for more flexibly denoting different kinds of function properties.


The ultimate i think would be being able to define a nice set of properties of things like functions and procedures
--in the language itself-- like the second, then use the first thereafter.
This could then be the default, but allows for changing the behaviour for advanced requirements.

Each folder could have an optional '.silver' directory where behaviour could be overridden/changed.
