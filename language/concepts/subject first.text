
Subject first
===================
Or subject-verb-object, or subject-object-verb

https://en.wikipedia.org/wiki/Subject%E2%80%93verb%E2%80%93object
https://en.wikipedia.org/wiki/Reification_(computer_science)
https://en.wikipedia.org/wiki/Pure_function


This brings together a bunch of ideas such as reification, pure functions, oo, scope ...


Statements
----------

So the idea here is that I want silver to be able to say things like:


	myarray apply
		...


	myvar match
		...


	mycollection pipe
		...


Or things like that.
The thing to note that I'm going for is that the variable name is first and the action or method is second.
In that way it's a bit like an oo class method, and you could imagine writing these with dot notation:

	myarray.apply(operation: foo
		...


	myvar.match(expression: foo
		...


	mycollection.pipe(sequence: foo
		...

OO and function purity
----------------------
But the problem with this bit of oo (that I'm trying to work around) is that the functions written like this, and barring any under the hood magic at this point, are not pure.
In addition to any declared arguments methods also take the implied argument 'this' (or lang equiv) for the class or instance.

So in a way all oo class methods take an extra argument of the instance:

in the method signature:

	myMethod
	(
		parameter1: valueType
		parameter2: valueType		// declared parameters
		..
		this: object				// the instance 'this' scope
	)

and in a method call

	foo.myMethod
	(
		parameter1: value1
		parameter2: value2
		...
		this: theInstance

	)


Now tbh i don't really know how most oo languages do their thing, maybe this is actually how the magic is done.
But to fulfill pure function point 1 (only operate on arguments) this becomes a necessity.

So then we're in the situation where you have something like

	verb(subject, ...object...)

In the oo case, the object or instance is the subject, and any other parameters become the (linguistic) object.
And that too is something i'd like to provide an alternative for.
Partly becuase I find 'everything is a function' code hard to read, even though I can see how it arises.

So I'm wondering if there might be some sort of way to auto-demangle a function fulfilling a certain contract into a nicer piece of syntax.
(Indeed this might be only way at the start to provide basic keywords.)

So you have a function

	verb(subject: object, ... other arguments ...)

and if it has a subject parameter in the right sense, or defines the right properties, then you can demangle it to:

	subject verb
		...other parameters...

yielding a far cleaner and more readable syntax.



So some sketchy examples
------------------------

Addition function:

	plus(subject, object)

becomes

	subject plus
		object
or

	subject plus { object }



A match conditional statement

	match(subject, {{matchExpr:method}{matchExpr:method}...})

becomes

	subject match
		expr: method
		expr: method

There might need to be some additional indicators for a more complex expression like match though, to delineate different parts of the object like options and maybe a payload.
A simpler example might be 'equal':

	equal(subject,object,payload)

	subject equal
		object
		payload







Counter Examples
----------------

Places where subject first doesn't make much sense, or would be a bit of stretch.


Multiple combine or add:

	Say you wanted to create a collection from some elements, which for whatever reason aren't yet combined.
	This could be an overload of an 'add' function for example.
	The binary case is obvious:

		a add b

	But for combining lots of things it's a bit uglier...

		a add b add c add d

	or

		a add {a,b,c,d}

	Both of these arbitrarily favour one of the elements, which isn't ideal.
	(though, it could be used to some advantage for things like precedence)
	So you might just to give up on subject-first and do:

		add {a,b,c,d}

	A couple of ways to put the subject back at the start - perform it as an assignment:

		newCollection: add {a,b,c,d}

	Allow the subject term to be a constructed collection:

		{a,b,c,d} add

	But both of these would need to be cleared up about what the actual parameters are - are we adding the arguments as groups of items, or as a group of items.







