Types
=====

Type Syntax
-----------

### Capitalisation

All types begin with a capital letter:

```js
	name: String `Alice`
	year: Integer 2005

	grandTour: Array
		`Giro d'Italia`
		`Tour de France`
		`Vuelta a España`
```

### Position

Types go to the right of the colon, before the value:

```js
name: String `Alice`
```

These are INCORRECT:
```js
name String: `Alice`	// INCORRECT
String name: `Alice`	// INCORRECT
```


Type definitions
----------------

Types can be built out other types:

```js
Product: Array
	name: String
	price: Decimal
Product End

myProduct: Product
	name: `bread`
	price: 4.99
myProduct end
```


Core Types
----------
There are two core types, String and Array.
All other types are derived from these.