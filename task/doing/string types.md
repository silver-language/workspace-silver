String types
============

Looking at lexing strategies and would like to take a little detour into string types.



Escaping in Go
--------------

I've mostly been coding Go lately so have that on the brain, but lots of languages do something similar.

### Basic strings

	"This is a basic string."
	"Double-quoted string often allow for escape characters using backslashes"
	"For example to put in a backslash you need to escape it like this: \\"
	"Same for double quotes (\"), newlines (\n) and tabs (\t)"
	"Full list of escapes here: https://www.geeksforgeeks.org/strings-in-golang/"

### Raw strings

	`A raw string`
	`Raw strings
	 can span multiple lines`
	`And escape sequences like \n \t aren't interpreted`
	`Often used for regexes where backslashes are needed`

I think these are both essentially like constructors - different rules apply while building, but once done I think (though I'll check) that they are of the same type.

https://medium.com/@andreiboar/demystifying-golang-strings-05981b84f1a7



Different Kinds of Strings
--------------------------

* raw string 					- exactly as written, no escaping/escapes ignored
* string with escape sequences	- using common backslash notation
* concatenated string			- combined with (eg) a plus
* interpolated string			- (aka template string) string with variables embedded


String Kinds as Types
---------------------

I was wondering if something like these might make sense:

```
	name 			: String "Alice"
	tabDelimted		: String-escaped "1.1\t2.2\t3.3\t4.4"
	myRegex 		: String-raw "Year: \d\d\d\d"
	blockText		: String-multiline
		Lorem ispum
		Dolor sit amet
	helloTemplate	: String-interpolated "Greetings ${user}, today is ${date}."
```

At a glance they are fairly understandable, but probably misleading from a typing perspective.
They should all produce the same end result, ie should all be of the same String type.

You could perhaps force it to work by making them all type synonyms/aliases, but use different constructors for each.
I have no idea if that's a good idea or not, I suspect it might set a bad precedent.
I'll think about it.

Essentially this would be an alternative to using particular kinds of quotes to indicate string types/constructors.
Pros:
* Frees up different quotes for other purposes (what though?)
* Makes the processsing features you want explicit
Cons:
* Too many combinations to have literal typenames for all of them

For maybe a few simple cases this might be okay, but probably better to use proper string constructor functions when it gets more complicated.

In silver having a special type for multiline strings might be valuable to have proper indentation, and make it clear the indentation is ignored.
How the strings are joined is a concern though.


Strings for Names
-----------------

Most of the above pertains to string *values* - which could hold just about anything.

When it comes to value names and type names things will get more restrictive.

Initially value and type names will be holding to very simple strings that don't need quotes.

Eventually I'd like value names to be more permissive by allowing quotes and other constructions, but will hold off on that for now.

Simple (unquoted) value names:

* **Cannot** start with a capital letter
* Regex: [0-9a-z_-][0-9a-zA-Z_-]*

Type names will be more restrictive - something like:
* **Must** start with a capital letter
* Regex: [A-Z][0-9a-zA-Z_-]*
* The only other way to construct a type name might be with angle brackets, but that's further down the line.








