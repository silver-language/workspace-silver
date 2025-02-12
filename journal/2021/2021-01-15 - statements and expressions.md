
Statements and Expressions
==========================

Unresolved unease here....

An expression evaluates to ~something~

A statement does ~something~


Traditionally in maths we'd group expressions with parentheses.
But values can be created with braces for objects.

There might be some implicit but well trodden ambiguity here...


https://doc.rust-lang.org/book/ch03-03-how-functions-work.html#function-bodies-contain-statements-and-expressions



Blocks as structures, statements and expressions
------------------------------------------------

Another problem I've just thought of - when is a block a structure and when is evaluated like an expression.
Quick example from the collection combiner i was thinking about over in subject-first:

	newCollection: add {a,b,c,d}

But I noticed it lacked a type annotation, so say you write it like this:

	newCollection:
		type: array{foo}
		add {a,b,c,d}

Does newCollction become a struct or the result of the add operation???
The presence of the add seems to change the form of the expression.

Well for starters there's two obvious ways to interpret it - data or language.
	As data, it's a plain struct with names and values.
	As language (eval'd) it's probably going to be the result of the operation.

Also, maybe the type annotation is in the wrong spot? Should it actually be part of the add operation?
Could be either or both i guess, but probably needs to be at least one.

So for the moment:
	as data, all blocks are structures
	as language, some items modify or transform the resulting structure


One possible way to make this more explicit might be to use my hypothesised 'result' keyword.
I don't think I've written anything much about it yet, but it was my idea for making a return statement more declarative.
So for the above example:

	newCollection:
		type: array{foo}
		result: add {a,b,c,d}

Which isn't too bad I guess.


Would that be weird in the context of a function?

	reciprocal:
		type: function
		parameter:
			x: { type: integer}

		result: 1/x

So I'm thinking there are two ways to read this - a function statement and a function expression.
This needs to be cleared up.


