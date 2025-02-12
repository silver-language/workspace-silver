Array
=====

Simple Arrays
-------------


Array with anonymous values (indexes will be generated):

```yaml
	beatle: Array
		`John`
		`Paul`
		`George`
		`Ringo`
```

Array with numeric indexes (conventional array):
```yaml
	lordOfTheRings: Array
		1 : `The Fellowship of the Ring`
		2 : `The Two Towers`
		3 : `The Return of the King`
```

Array with named values (associative array):
```yaml
	dog: Array
		name		: `Scooby Doo`
		bestFriend: : `Shaggy`
		food 		: `scooby snacks`
```


Nested Arrays
-------------

```yaml
	backToTheFuture: Array
		1 : Array
			name	: `Back To The Future`
			year	: 1985
		2 : Array
			name	: `Back to the Future Part II`
			year	: 1989
		2 : Array
			name	: `Back to the Future Part III`
			year	: 1990
	backToTheFuture end
```

All but the innermost arrays **require** end statements.


End Statements
--------------
Array end statements are required on all but the innermost indent levels.


Note that these all mean different things:
```yaml
	foo end		// The array value 'foo' ends here
	Foo End		// The compound Type declaration 'Foo' ends here
	Foo end		// The anonymous array value of type 'Foo' ends here
	foo End		// This has no meaning - syntax error

	end			// Array value ends here, name ommitted - okay but use sparingly
	End			// Compound Type declaration ends here, name ommitted - *strongly* discouraged
```