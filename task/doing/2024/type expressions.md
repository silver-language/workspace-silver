Type expressions
================

Where needed
What needed (kinds)
mvp



### Is a special syntax needed for types?

Everything so far has just been:

	name: value
	name: type
	name: type value

without any special way of distinguishing the type from the value, just presuming it can be resolved in parsing.

Would it be advantageous to denote the type in some way such as:

	name: Type value			// capitalisation
	name: <type> value			// eg type expression

https://stackoverflow.com/questions/37358364/rules-for-the-use-of-angle-brackets-in-typescript