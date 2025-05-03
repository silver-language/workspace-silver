Silver-Data Grammar
===================

The parsing structure for silver data.

Warning - very tentative - lexing structure and grammar.
Need to be clear what's lexing and what's parsing.
There's lots here I'm not sure about.



Grammar
-------

### Document

	(line)*

### Line
	| (empty-line)
	| (indent)*(statement)

### Indent

	(\t*)

### Statement

	| (assignment)
	| (expression)
	| (block end)


### Assignment

	| (type assignment)
	| (value assignment)

### Type assignment

	(type name) : (type expression)


### Value assignment

	(value name)? : (expression)?


### Expression

	| (type expression)
	| (value expression)
	| (type expression) (value expression)


### Type Expression

	| (type name)
	| (compound type)

### Compound type

	TBD

### Value Expression

	TBD


### Block end

	| (type block end)
	| {value block end}

### Type block end

	(type name) End

### Value block end

	(value name) end


### Type name

	[A-Z]\w+

### Value name

	| (simple value name)
	| (quoted value name)
	| (dynamic value name)

### Simple value name

	[^A-Z]\w+

### Quoted value Name

	"(\w+)"

### Dynamic value name

	TBD

