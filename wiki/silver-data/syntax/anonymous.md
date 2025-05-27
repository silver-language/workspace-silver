Anonymous values
================

Items without names are anonymous and given automatically generated names/indexes:

```js
stooges: Person
	`Larry`						[1]
	`Curly`						[2]
	`Mo`						[3]
```

Anonymous blocks can use types as placeholders:

```js
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

```js
class: Array of Student
	:
		name: `Alice`
	:
		name: `Bob`
	:
		name: `Charlie`
```
