Assignment
==========

Assignment is done with a colon, not an equals sign.

https://en.wikipedia.org/wiki/Equals_sign#Usage_in_mathematics_and_computer_programming


Single value assignment
-----------------------

Assigning a single value looks like this:

	name : type value

Without a value this is becomes a type declaration:

	name : type

Type can be omitted if specified elsewhere:

	name : value


Examples:

	firstName : string Alice
	firstName : string
	firstName : Alice





Block assignment
----------------

Block assignment is as follows:

	blockName: blockType
		item1: type1 value1
		item2: type2 value2


Without a name only the type is specified:

	blockType
		item1: type1 value1
		item2: type2 value2


Block ends
----------

Blocks may be terminated with either of these constructs:

	blockName: blockType
		item1: type1 value1
		item2: type2 value2
	end blockname

	blockName: blockType
		item1: type1 value1
		item2: type2 value2
	end

Nameless blocks can only use the second form:

	blockType
		item1: type1 value1
		item2: type2 value2
	end



Refs
----
https://developers.slashdot.org/story/23/08/07/0136228/should-a-variables-type-come-after-its-name

https://go.dev/doc/faq#declarations_backwards

https://benhoyt.com/writings/name-before-type/


https://go.dev/blog/declaration-syntax
