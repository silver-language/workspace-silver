Names and Naming
----------------


```yaml
type: design task
category: lexing/parsing
status:  ongoing
priority: medium
```

Need to decide on some explcit naming rules, for now at least.


So far it's been this:
	valueName: value expression
	valueTypeCombined : type expression value expression
	TypeName: type expression

So far it's been values start with a lower case letter and types with an uppercase letter.

The question is what other kinds of names could be allowed, and what would they look like, and can they be added incrementally.
For example:
	* quoted names
	* names with modifiers to indicate kind
	* dynamic names

These would be a bit fancy, and not needed initially, except maybe quoted names.




Quoted names
------------

For bare names i probably want to stick to something basic like the /w regex chars.
That would be names-basic.

But there are times when allowing other characters into names can be handy which would require something like quotes.

	"a slightly complicated name" : String "foo"
	"0-590-76484-5" : Book ...


You wouldn't do the second in practise, it's just an example.





Names with modifiers
--------------------

This is a thought I have sometimes, don't know if it's good or necessary.
I guess it's a bit like hungarian notation, something like:

	+typename : (type expression)

Where some prefix or modifier indicates that it's a type.
In general I'm not a fan of these kinds of schemes, but it floats through my head from time to time, as I wonder if it would be easier to read than initial capitals.

In a character and syntax-lite world this would be bad, as it uses up a valuable char and could get ugly.
With unicode though you could do just about anything, as long as your font supports it.

	𝑻typename : (type expression)
	𝚃typename : (type expression)



Dynamic Names / name expressions
--------------------------------

Don't know how this could work, haven't really thought about it yet, probably something like this:

	"product"+id1: Product input1


