

Schema and type
===============
Once, I thought this might be easy....


I'd like a way of being able to specify the shape of data.
So given a piece of data:

	I can say whether it conforms to the shape or not
	I can parse it into the required shape successfully
	I can specify multiplicty for items, initially ZOI
	I can accept or reject things optional to the shape
	I can declare a shape without necessarily specifying concrete data types

Not sure about the last. But anyway.

I've copied some of the example documents from rust/silver-data into here.
The one i'm interested in the is the silver-backup one.

How do i specify the schema for it?

So i've had a quick crack at some syntax and nothing is really popping out straight away.

There main problems:
	literal vs placeholder keys
	multiplicity


Literal vs placeholder keys
---------------------------
This is the easier of the two.

If i have a classroom schema it might look like

	person
		'name'		: string
		'address'	: string
		'phone'		: string

	'teacher'		: person 		// singular
	'class':						// multiple
		person






Multiplicity
------------





Experimenting with simplified type systems
------------------------------------------
To simplify the system you could specify that simple subsets of types, eg nearly the simplest one would be arrays and strings.
That way every unary value becomes a string.
There are no references other than names


Data, schema and type
---------------------

Just some ideas that came to me today....

	Data
		all values should resolve to literals or references

		In pure data things like schemas and types could be present, so that's not a problem, but it would be preferable if the schemas and types were defined.
		That's not so much my problem though.
		That's the end programmer's problem.


	Schema
		All values should resolve to literal or primitive types, or other schemas.

		A schema should probably not contain any literals, except maybe for documentation/comments/informational text.

		Actually scratch that, extended runtime validation is often included in schemas, so literals are definitely needed, eg enforcing a value is in a certain range or length or format.


	Types

		Types can only be composed of other types.
		These are things that can be checked at compile time, and do not include runtime checks for values.

		It might be nice though to have a way to declare literals in a special 'meta' way because this will be handy for comments/documentation.

		Also I find myself wondering if an immutable constant, something that can never change, could be included in a type?


	So then
		types are expressions built out of types
		types are checked at compile time

		schema is a specific language for enforcing type and format of data, and is a superset of type

		data can contain literal, schema, and type



Can a type have names?
----------------------

So this is one of those things I'd like to have.
A schema can definitely (and should) have names for fields.
A database schema does just that.

But what about a type?

I think this is normal - I've just had a look at some of my rust code and in places where I've specified a struct as a type those definitely have names.

It would be worth doing some experiments with identical but different named structs (either struct-as-a-whole or members) to see if/when Rust allows or disallows these kind of things.
I'd prefer that different names denote different types.



Can a type have constants?
--------------------------

This was just a random idea I had.
If you can't have variables in types, could you have a constant?
If it could *never* change, in theory a compiler could probably be satisfied that type requirements were met.
In practise i don't know how feasible that would be, as presuambly there's always ways to fiddle with memory locations.
But the idea is kind-of sound.
Could that be used for documentation?
This is making my brain do weird things - this feels like it could start crossing over with schemas.
Maybe i need some examples.

Some regular, conventional types (assuming i can use names):

	foo: boolean

	name: string

	person:
		name: string
		age: integer

These are all things the compiler should be able to confirm. But what if i add some schema style constraints for fun:

	person:
		name: string
		age:
			type: integer
			minimum: 0

First up i've had to decompose the age variable. I'd like to be able to do this so that I can add things like comments to types anyway. The exact syntax i'm not sure about yet, but probably not very different from the above.

But in this case I've added "minimum: 0".
I don't want or expect the compiler to check that (ignoring unsigned ints for the moment), i just want it to be a constant.

So a few thoughts here.
	The names still have to match.
	Both sides still have to match - a bit like a type anyway.
	But in this case the type is a static value.


See this - it might be a thing (in typescript an Python at least):
	https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#literal-types
	https://www.python.org/dev/peps/pep-0586/

So i'm not totally detached from reality here.

In rust this might be doable with something like a single member enum type - should give it a try.














Schema is a superset of type
----------------------------
For now i think that's the main takeaway.

I should start to get cracking on the simplest type/schema for silver data then, which is basically just

	silver-data:
		array or string


