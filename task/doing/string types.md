String types
============

Looking at lexing strategies and would like to take a little detour into string types.



Escaping
--------

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



Different String Types
----------------------

I was wondering if something like these might make sense:

```
	name 			: String "Alice"
	tabDelimted		: String-escaped "1.1\t2.2\t3.3\t4.4"
	myRegex 		: String-raw "Year: \d\d\d\d"
	blockText		: String-multiline
		Lorem ispum
		Dolor sit amet
```

At a glance they are fairly understandable, but probably misleading from a typing perspective.
They should all produce the same end result, ie should all be of the same type.
You could perhaps force it to work by making them all type synonyms/aliases, but use different constructors for each, though I have no idea if that's a good idea or not.
I suspect it might set a bad precedent.
I'll think about it.

