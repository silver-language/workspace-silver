Syntax errors
=============




Sub-structured simple values
----------------------------

In arrays types can be used as placeholders for the members:

	classroom:
		student
			name: Alice
		student
			name: Bob
		student:
			name: Charlie


If 'student' is not defined elsewhere as a type, it becomes a simple value, in this case a string.
A string has no sub-members (other than metadata) so this is a syntax error.
