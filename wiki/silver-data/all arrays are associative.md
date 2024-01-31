
All arrays are associative
==========================

https://en.wikipedia.org/wiki/Associative_array

In general I'll prefer to use 'name' rather than 'key' but otherwise the principle stands.
I'll tend to use array and collection somewhat interchangeably unless I'm being specific.
In this text I'll be a little more specific.

Traditionally:

	arrays are collections of anonymous values, usually of the same type, that automatically gain an index
	associative arrays are collections of explicitly named items, not necessarily all of the same type


In silver data:

	All arrays are associative, but keys/names are optional.
	If you don't provide one, one or more may be automatically generated.



so the general idea...


	name: value

	name:
		value
		value
		value

	name:
		value
		name2: value

...etc, as outlined elsewhere.

The distinguishing feature


Under the hood
--------------
If you specify names and types that be stored as something more efficent, then we'll do that.
