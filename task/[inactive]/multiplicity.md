
Multiplicity
============

```yaml
type: task
category: language design
status: partial progress, ongoing
priority: normal
```

In arrays
---------

Syntax for multiplicity

	player: type
		name: string
		position: number

	myTeam: footyTeam [1...12] of player

	team.player.1:
		name: 'Ken'
		position: 7

	team..type = [1...12] of player
	team..type = array[1...12] of player
	team[1]..type = player
	team.1..type = player
	team..index.type = integer
	team..index.first = 1
	team..index.last = 12
	team..index.before = 0		// or maybe undefined, depending on circumstances
	team..index.after = 13		// or maybe undefined, depending on circumstances
	team.1 =
		name: 'Ken'
		position: 7


Just a few other ideas i had about array syntax

	winners: [gold,silver,bronze] of competitor			// an array with just those three keys

	non-winners: [4...] of competitor					// positions 4 onwards

	competitors: [0...]									// traditional zero-based array
	competitors: [1...]									// 1 based array

	excelRow:	[aa...]	of cell							// auto incrementing alpha starting at aa
	postion: [integer]
	struct: [alphanumeric] of any								// kind of equivalent to a standard associative array



So in general
-------------

One liner (combined type and assignment):

	arrayName: arrayType [array keys] of memberType

Separate type and declaration

	myArrayType: array [array keys] of memberType

	myArray: myArrayType
		appropriateKey: appropriateMemberVal
		...



Slow down for a sec - we need a standard syntax
-----------------------------------------------
I've accidentally gone ahead a defined a neat compact syntax for multiplicity/array keys without an ordinary array-style syntax

myArray: array
	1: 'hello'
	2: 'world'


What is the the metadata key for the member names of the array?

	names?
	valueNames?
	keynames?
	keys?











