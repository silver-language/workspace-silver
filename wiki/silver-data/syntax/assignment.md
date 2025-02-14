Assignment
==========


Simple Assignment
-----------------

Variable assignment is in the form name-colon-value:

```yaml
	variableName : `value`
```

Type declarations have the form name-colon-Type (type names are capitalised):

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

### Name as block start

```yaml
	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
```

### Type as block start

A type alone can be used as a block start, and the block is anonymous:

```yaml
	BlockType
		item1: Type1 value1
		item2: Type2 value2
```

Optionally in these cases the type may be preceeded by a colon to aid clarity:
```yaml
	:BlockType
		item1: Type1 value1
		item2: Type2 value2
```

### Implied type

When the block type is implied or provided by the context the type may also be ommitted and a single colon used as the block start:
```yaml
	:
		item1: Type1 value1
		item2: Type2 value2
```


Block ends
----------
Block ends are optional on the innermost block.

All deeper blocks must be terminated with either an `end` or `end [blockname]`:

```yaml
	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end blockName
```

### Anonymous blocks

Anonymous blocks can be ended with either `end` or `TypeName end`:

```yaml
	BlockType
		item1: Type1 value1
		item2: Type2 value2
	end

	BlockType
		item1: Type1 value1
		item2: Type2 value2
	BlockType end

	:
		item1: Type1 value1
		item2: Type2 value2
	end
```



Refs
----

https://en.wikipedia.org/wiki/Equals_sign#Usage_in_mathematics_and_computer_programming

https://developers.slashdot.org/story/23/08/07/0136228/should-a-variables-type-come-after-its-name

https://go.dev/doc/faq#declarations_backwards

https://benhoyt.com/writings/name-before-type/

https://go.dev/blog/declaration-syntax
