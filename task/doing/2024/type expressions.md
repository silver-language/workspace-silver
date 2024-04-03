Type expressions
================



Where needed
What needed (kinds)
mvp



Is a special syntax needed for types?
-------------------------------------

Everything so far has just been:

	name: value
	name: type
	name: type value

without any special way of distinguishing the type from the value, just presuming it can be resolved in parsing.

Would it be advantageous to denote the type in some way such as:

	name: Type value			// capitalisation
	name: <type> value			// eg type expression

https://stackoverflow.com/questions/37358364/rules-for-the-use-of-angle-brackets-in-typescript



Product and Sum Types (AND / OR types)
--------------------------------------

https://ericnormand.me/podcast/what-are-product-and-sum-types

https://en.wikipedia.org/wiki/Algebraic_data_type



### Product Type, ie AND
https://en.wikipedia.org/wiki/Product_type

aka
	Tuple
	Record
	Struct

This is my basic array.


### Sum Type, ie OR
https://en.wikipedia.org/wiki/Tagged_union

aka
	enum
	discrimnated union

NB note the difference between this and https://en.wikipedia.org/wiki/Enumerated_type

https://langdev.stackexchange.com/questions/2326/what-are-pros-and-cons-of-tagged-vs-untagged-union-types


I think I want the tagged union type?


Sum/Enumerations/Unions - 'OR' types
------------------------------------

https://en.wikipedia.org/wiki/Enumerated_type
https://en.wikipedia.org/wiki/Tagged_union

In typescript prefer discriminated union over enum


Fast F#: Intro to Discriminated Unions
https://www.youtube.com/watch?v=vgMYQ1clE0E
	'or' cases have names separate from the types



	Suit: choice of String
		hearts
		diamonds
		clubs
		spades

	myCard: Card
		suit: Suit 'clubs'

Not sure how to to clearly discriminate literals or types yet

	Document: Array of Element

	Element: choice of Type
		Title
		Link
		Code
		Paragraph
		...

Have to figure out the best way to write this out - 'choice' needs to be a keyword of some kind, so the type system needs some utility keywords.








Utility Types / Type keywords
-----------------------------

	of
	choice

See for example
	https://www.typescriptlang.org/docs/handbook/utility-types.html







