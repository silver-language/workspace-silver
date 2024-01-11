Basic constructs
================

Even though it will be a while before i get to any of this stuff, i want to start sketching things out and trying ideas for what might work.

The basic minimum constructs i need are:
	assignment
	function declaration
	conditional




assignment
----------

	name: value

	name:
		value

	name:
		value
		value
		value
		value

	name:
		value
		name:	value
		value
		name:
			value
		value
		name:
			value
			value
			value





function declaration
--------------------

	name:
		type: function


function call
-------------
All arguments to functions are named.


	functionName(a:b; c:d; )



match (conditional)
-------------------
Want to start with just one conditional, a match expression.
This needs workshopping...


	match (thing)
		expression		block
		expression		{ block }
		(expression)	block
		expression
			block
		expression
		{
			block
		}


Match is something I'd love to be able to condense down into a single expression, but not sure if i'll be able to.
For instance it would be nice to be able to have one syntax for
	single match
	multi-match
	not match
	match within time (ohh cool)
	match at least n,
	match fuzzy (nearest to),
	etc.
All sorts of fun ideas fall into this category.
They could obviously all be done with separate methods and would obviously all be implemented under the hood as individual methods, but it would be nice have a way to use a single syntax and flip the logic using options or configuration.
Which comes back to the ontological question of 'metadata'.
This needs work.



collection operations
---------------------

These are for things like looping, map, reduce
I wonder if some terminology could be found that includes other types of collections/structures such as lists, trees, graphs, matrices etc.

	loop myCollection
		print(current)



apply
foreach



