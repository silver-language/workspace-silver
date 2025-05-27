Silver
======

Silver is a data format.

It is also intended to be extended to include programming language features.



Silver Data
-----------

Basic assignment syntax:
```js
	variableName : Type value
```
For example:
```js
	name: String `Alice`
```



Structure assignment:
```js
structureName: StructureType
	item1: Type1 value1
	item2: Type2 value2
```
Example:
```js
product1: Product
	name:	String `cat food`
	price:	Price  4.99
```

Structures might be arrays, blocks, objects etc based on context.




Silver Language
---------------

Silver language is an additional layer on top of the data format.

It allows for creating programming structures in silver data.

Example (very provisional):
```js
factorial: Function
	type: UnsignedInteger
	parameter:
		number: UnsignedInteger

	result: match (number = 0)
		true	: 1
		false	: factorial(number: parameter.number-1)

factorial end
```


