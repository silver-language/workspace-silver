Parsing and Grammar
===================

The parsing structure for silver data.

Warning - very tentative - lexing structure and grammar.
Need to be clear what's lexing and what's parsing.
There's lots here I'm not sure about.

Lexing/parsing
--------------

### Document

	(line)*

### Line

	(empty-line) | (indent)(statement)

### Indent

	(\t*)

### Statement

	| (name): (entityExpression)
	| (:?)(entityExpression)
	| (name):
	| :





### Entity Expression

	| (type expression)
	| (value expression)
	| (type expression) (value expression)


Grammar
-------

### Assignment

	(name) : (entity)

### Entity

	| (type)
	| (simplevalue)
	| (blockValue)

### Simple Value

	(type)(value)

### Block value

	(entity)*





