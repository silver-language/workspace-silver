Assignment
==========


Simple Assignment
-----------------

Variable assignment is in the form name-colon-value:

```yaml
	variableName : `value`
```

Type declarations have the form name-colon-Type (types are capitalised):

```yaml
	variableName : String
```

Combined assignment and type declaration is name-colon-Type-value:


```yaml
	variableName : String `value`
```

Examples:
```yaml
	myString : `hello world`

	person1 : String
	person1 : `Alice`

	person2 : String `Bob`
```


Block assignment
----------------

Block assignment is as follows:
```yaml
	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
```

Without a name only the type is specified:

```yaml
	BlockType
		item1: Type1 value1
		item2: Type2 value2
```



Block ends
----------

Blocks may be terminated with either of these constructs:

```yaml
	blockName: blockType
		item1: type1 value1
		item2: type2 value2
	end blockname

	blockName: blockType
		item1: type1 value1
		item2: type2 value2
	end
```

Anonymous blocks can be ended either with a plain `end` or `TypeName end`:

```yaml
	BlockType
		item1: type1 value1
		item2: type2 value2
	end

	BlockType
		item1: type1 value1
		item2: type2 value2
	BlockType end
```




Refs
----

https://en.wikipedia.org/wiki/Equals_sign#Usage_in_mathematics_and_computer_programming

https://developers.slashdot.org/story/23/08/07/0136228/should-a-variables-type-come-after-its-name

https://go.dev/doc/faq#declarations_backwards

https://benhoyt.com/writings/name-before-type/

https://go.dev/blog/declaration-syntax
