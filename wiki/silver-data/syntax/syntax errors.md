Syntax errors
=============




Sub-structured simple values
----------------------------

In arrays types can be used as placeholders for the members:

```yaml
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
