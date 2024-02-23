Brace syntax
============

This is not mandatory at this point, but something I want.


Essentially an equivalent syntax using braces and semicolons, and that lossless transforms can be done be done between the two.

Mixing of the syntaxes will probably only be allowed in the case of embedding the brace syntax within the indented syntax, and prefereably only at the lowest levels.


Syntax
------

	name: type value;


A block

	blockName: blockType
		item1: type1 value1
		item2: type2 value2

Equivalent brace syntax:

	blockName: blockType
	{
		item1: type1 value1;
		item2: type2 value2;
	};


or on one line:

	blockName: blockType { item1: type1 value1; item2: type2 value2; };


NB: not sure yet whether I need the terminating semicolon after the last brace - it might be redundant.