
Silver Data
===========

This is the current summary of the syntax and rules.


Assignment
----------

Named values must have a colon after the name and before the value:

```yaml
	year: 2001
```


Blocks
------

Blocks are denoted by indentation:

```yaml
product1:
	name:	`cat food`
	price:	$9.99

person:
	name: `Jane Smith`
	age: 34
```

Blocks can optionally be terminated with `end`, or `blockname end`:

```yaml
product1:
	name:	`cat food`
	price:	$9.99
end


product1:
	name:	`cat food`
	price:	$9.99
product1 end
```






Metadata
--------

Metadata fields are read with two dots:

```yaml
	thisYear..value = 2024
	thisYear..Type	= Integer
	thisYear..name	= thisYear
```

Metadata is an array, so this would be equivalent
```yaml
	thisYear
		..
			value : 2024
			Type
			name
```


Anonymous values
----------------

Items without names or keys are anonymous values and automatically given names/indexes:

```yaml
	stooges: Person
		`Larry`						[1]
		`Curly`						[2]
		`Mo`						[3]
```

Anonymous blocks can use types as placeholders:

```yaml
	class:
		Student
			name: `Alice`
		Student
			name: `Bob`
		Student
			name: `Charlie`
```

### Placeholder for typed anonymous blocks (experimental)

In cases where the type of the child items is known a single colon can be used as a placeholder.

```yaml
class: Array of Student
	:
		name: `Alice`
	:
		name: `Bob`
	:
		name: `Charlie`
```
