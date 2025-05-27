Syntax errors
=============




Sub-structured simple values
----------------------------

Simple values cannot have members, so for example this would be a syntax error:

```js
	olympics: Integer 1900
		venue: `Paris`
```


### Special case - Multiline Strings

Strings are simple values so this is a syntax error:

```js
	title: String `Star Wars`
		subtitle: `Episode IV – A New Hope`
```

If however there isn't literal on the initial line a valid multiline string is formed:

```js
	title: String
		Star Wars
		Episode IV – A New Hope
```


### Apparent types

In arrays types can be used as placeholders for the members:

```js
	classroom: Array
		Student
			name: `Alice`
		Student
			name: `Bob`
		Student
			name: `Charlie`
```

If 'Student' is not defined elsewhere as a type, it becomes a simple value, in this case a string.
A string has no sub-members (other than metadata) so this is a syntax error.

[tbc: do these become multiline strings?]


### Metadata

[clarify how this relates to the metadata substructure]
