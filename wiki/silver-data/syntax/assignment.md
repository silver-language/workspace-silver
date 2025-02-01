Assignment
==========

Assignment is done with a colon, not an equals sign.

https://en.wikipedia.org/wiki/Equals_sign#Usage_in_mathematics_and_computer_programming






Single value assignment
-----------------------

Here's the basic assignment of a simple value:

	variableName : value

Declare a variable to be of a particular type without assigning anything to it - the type is capitalised:

	variableName: Type

User-made or aliased types must be capitalised:

	TypeName: Type

A combined type-value assignment is like this:

	variableName: Type value

Examples:

	myString : 'hello world'

	person1 : String
	person1 : 'Alice'

	person2 : String 'Bob'





Block assignment
----------------

Block assignment is as follows:

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2


Without a name only the type is specified:

	BlockType
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

	BlockType
		item1: type1 value1
		item2: type2 value2
	end



Refs
----
https://developers.slashdot.org/story/23/08/07/0136228/should-a-variables-type-come-after-its-name

https://go.dev/doc/faq#declarations_backwards

https://benhoyt.com/writings/name-before-type/

https://go.dev/blog/declaration-syntax
