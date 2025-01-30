String types
============

Looking at lexing strategies and would like to take a little detour into string types.


```yaml
type: task
status: mostly done (for now)
blocks: lexing
priority: high
```


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
	name 				: String "Alice"
	tabDelimted			: String-escaped "1.1\t2.2\t3.3\t4.4"
	myRegex 			: String-raw "Year: \d\d\d\d"
	blockText			: String-multiline
		Lorem ispum
		Dolor sit amet
	greetingTemplate	: String-interpolated "Greetings ${user}, today is ${date}."
```

At a glance they are fairly understandable, but probably misleading from a typing perspective.
They should all produce the same end result, ie should all be of the same String type.

You could perhaps force it to work by making them all type synonyms/aliases, but use different constructors for each.
I have no idea if that's a good idea or not, I suspect it might set a bad precedent.
I'll think about it.

In essence this would be an alternative to using particular kinds of quotes to indicate string types/constructors.
Pros:
* Frees up different quotes for other purposes (what though?)
* Makes the processsing features you want explicit
Cons:
* Too many combinations to have literal typenames for all of them

For maybe a few simple cases this might be okay, but probably better to use proper string constructor functions when it gets more complicated.


### String concatenation

I could have added something like this to the examples above:

```
	helloString			: String-concatenated "Hello" + name
```
But I reckon concatenation is a whole different beast, and more complicated, than any of the initial examples:
* It presumes a plus operator
* It presumes an infix style of construction
* It presumes variables (in this example)

With the exception of the multiline string (which is kind of a special case), all of the others could have their string types changed, and they'd *still* produce a string (just maybe not the one you wanted).
They really are synonyms for string.


### Escaping double-quotes and quote grouping

There might be exceptions to string synonym substutability in some edge cases.
An example could be an escaped string with backslash-escaped douple quotes in it:

	scareQuotes : String-escaped "The \"fresh\" bread was all dried up"

Changing that to String-raw necessitates taking a position on quote grouping:
* Disallow double quotes within double quotes - use a different encoding.
* Strings last from the first to the final double quote - anything inside is string content

The second would be easier to parse, but probably rule out string concatenation. That may not be a bad thing....

https://duckduckgo.com/?q=string%20concatenation%20interpolation


Interpolation over concatentaion
--------------------------------

I think I might favour interpolation over concatenation as a general stance.
* More modern, readable & maintainable
* Simpler string parsing
* Simplifies quote grouping, and therefore allows string type aliasing more comfortably
* More flexible - you can use whatever template style you like if you have a processor for it
* Far less presumptuous, as stated above.


Multiline Strings
-----------------

In silver having a special type for multiline strings would be valuable to have proper indentation, and make it clear the indentation is ignored.
How the strings are joined is a question, but a newline would probably suffice for starters.

Another option (which I've done in example code) is Array of String, which gives the array back to be joined as pleased.


Strings for Names
-----------------

Most of the above pertains to string *values* - which could hold just about anything.

When it comes to string names for values and type things will get more restrictive.

Initially value and type names will be holding to very simple strings that don't need quotes.

Eventually I'd like value names to be more permissive by allowing quotes and other constructions, but will hold off on that for now.

Simple (unquoted) value names:

* **Cannot** start with a capital letter
* Regex: [0-9a-z_-][0-9a-zA-Z_-]*

Type names will be even more restrictive - something like:
* **Must** start with a capital letter
* Regex: [A-Z][0-9a-zA-Z_-]*
* The only other way to construct a type name might be with angle brackets, but that's further down the line.


Use different quotes for names
------------------------------
If we went down the string-type-alias route (which I'm still mulling over) then, as mentioned, it would free up some quotes for other purposes.

For instance you could have different quotes (or delimiters) for names, types and values.
For now I'd rather not think about really crazy type names (notwithstanding the utility of delimiters), but using different quotes for names is an idea.

Eg

	simpleName		: SimpleType simpleValue
	'fancy name'	: <Fancy Type> "fancy value"

* Might look more complicated in some cases?
* Probably make parsing easier...
* Might make name construction clearer, for instance only specific escaping/interpolation rules allowed.

Names will always be a subset of String.


### String interpolation in names
Eg:
```pseudocode
	loop x
		loop y
			'pixel-{x}-{y}' : 0
		loop end
	loop end
```

Not that you'd do it like that.



Tentative Summary
-----------------

* Allow for type aliases to use different constructors, as long they return the main type
* Prefer string interpolation over concatenation (if concatenation is allowed at all)
* Strings are delimited by the outermost set of quotes, everything inside is the string proper
* Plain (undelimited) value and type names have fairly strict naming rules
* More complicated value names can be be achieved by quoting with single quotes


### Precedence

This would probably all be mostly okay for something like silver data, but when the grammar gets more complicated you'd need a precedence rules of some sort.

Eg, method chaining:
```
	myFoo		: megaData.map("mobiusStrip").crease("downTheMiddle").fold("up).pocket("done")
	fooProcess	: "megaData.map("mobiusStrip").crease("downTheMiddle").fold("up).pocket("done")"
```
Brackets take precedence in the first, quotes in the second.


Backticks and Quote shuffling
-----------------------------

Thus far I've been pretty sparing with use of quote characters (if all goes well), so would there be any benefit from shuffling them around a bit to optimise their use?

For example, what if ordinary strings used backticks instead of double quotes, eg to clean up the scare quote example:

	scareQuotes : String `The "fresh" bread was all dried up`

Backticks have almost no use in ordinary prose, so you could use singles and doubles freely:

	someProse : String `"The fresh bread is all dried up", said O'Leary to Minogue.`

It'd certainly be unusual - I don't think I've ever seen something like that before.
Markdown `wouldn't` like it much though.

Admittedly regular prose like that doesn't appear much in most programs.
However it does in data.

There's an experiment where I've tried to use silver-data for a document format a bit like HTML:

[experiment - document format](../../wiki/silver-data/example/experiment%20-%20document%20format.md)

Rewritten a bit, with some current ideas:

```
	myDoc: Document
		heading: H1 `This is the heading of the document`

		introduction: Paragraph
			`lorum ipsum`
			`dolor sit amet`

		H2 `Requirements`
		UnorderedList:
			`item 1`
			`item 2`
			`item 3`

		H2 `Instructions`
		OrderedList
			`do this`
			`then this`
			`finally this`

		script: Code
			`10 print "Hello world"`
			`20 goto 10`

		references: UnorderedList
			Link `http://localhost/help`
myDoc end
```





