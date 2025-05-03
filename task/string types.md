String types
============

Looking at lexing strategies and would like to take a little detour into string types.


```yaml
type: task
status: done-ish, still hacking
blocks: lexing
priority: high-ish
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
	myHomepage			: String-url "http://www.geocities.com/hollywood/123/my%20homepage.html"
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
How the strings are joined is a question, but a newline would probably do for starters.

Another option (which I've done in example code) is Array of String, which gives the array back to be joined as pleased.


Strings for Names
-----------------

Most of the above pertains to string *values* - which could hold just about anything.

When it comes to string names for values and types things will get more restrictive.

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
Contrived example (you probably wouldn't actually do this):
```pseudocode
	loop x
		loop y
			'pixel-{x}-{y}' : 0
		loop end
	loop end
```

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
	myFoo		: megaData.map("mobiusStrip").crease("downTheMiddle").fold("up").pocket("done")
	fooProcess	: "megaData.map("mobiusStrip").crease("downTheMiddle").fold("up").pocket("done")"
```
Brackets take precedence in the first, quotes in the second.

It will probably be necessary to talk about something like context starts and ends, but not for now.
For silver data the context end always be the line end.



Backticks and Quote shuffling
-----------------------------

Thus far I've been pretty sparing with use of quote characters (if all goes well), so would there be any benefit from shuffling them around a bit to optimise their use?

For example, what if ordinary strings used backticks instead of double quotes, eg to clean up the scare quote example:

	scareQuotes : String `The "fresh" bread was all dried up`

Backticks have almost no use in ordinary prose, so you could use singles and doubles freely:

	someProse : String `"The fresh bread is all dried up", said O'Leary to Minogue.`

Admittedly regular prose like that doesn't appear in ordinary programs much.
But similar sorts of things definitely would appear in data, markup, config etc.

### Review Backticks

https://en.wikipedia.org/wiki/Backtick

Usage of backticks:
* JavaScript since es6 - template strings, literals
* String literals of various kinds: Go (raw), F#, MySQL, R, Scala
* Command substitution - Perl, PHP, Ruby, Lisp macros, Julia, shell (deprecated)
* Alternative escape character in PowerShell
* Markdown for code sections and blocks
* No meaning as far as I can tell: C#, Python, Rust

Java seems to have gotten into the weeds a bit with their proposals - ended up with Text Blocks instead (afaict).

Suffice to say programming languages are really the only mainstream users of backticks.

### Need to escape?

I've done some code-block experiments here: [experiment - document format](../../wiki/silver-data/example/experiment%20-%20document%20format.md)

The takeaway is basic strings should be literal, and it would be *exceedingly* nice to be able recognise and handle String-multiline in the lexer/parser.

For single line strings or more complicated lines might need to establish some rules.
Method chaining examples from above and some mess:
```
myFoo				: megaData.map(`mobiusStrip`).crease(`downTheMiddle`).fold(`up`).pocket(`done`)
fooProcess			: `megaData.map(`mobiusStrip`).crease(`downTheMiddle`).fold(`up`).pocket(`done`)`
complicatedString	: String `` here's a bunch of backticks `````` and some `quasi-markdown` ```
```

Probably the easy solution is to just take everything between the first and last backticks within the established context.
For silver-data everything is one-idea-per-line (one statement or value), so the context always ends at the lineend. I don't think I have any need for brackets in silver-data, but will have to keep an eye on that one.
For the `myFoo` example you could do something similar, but take everything up to the last backtick before the context end, the close paren in this case.

### Too easy?

This feels *too* easy, I must be missing something.
Why hasn't anyone used this solution before?
Better write out some tests and find some counterexamples.

Probably being able to escape the context boundaries - parentheses, brackets etc will become necessary.
Say for instance you want brackets and backticks in a regex with chained methods:
```
	matches	: Boolean myString.find(``(\w+)``).print()
	band 	: Boolean myString.findOne(``bandname`:Sun O)))`).toUppercase()
```
(I probably wouldn't write either like that, but it's a style.)
The meaning is clear-ish, but it's a little non-obvious how to parse it.
This is undoubtedly a solved problem, but it's beyond me for now, so I'm going to go with a simpler solution with unambiguous context boundaries.
```
	regex1	: String ``(\w+)``
	matches	: Boolean myString.find(regex1).print()
	regex2	: String ``bandname`:Sun O)))`
	band 	: Boolean myString.findOne(regex2).toUppercase()
```
This is how I would write these - more readable to me, and easier to parse.
And no need (yet) to escape anything.


### Single and double quotes

Does that leave anything for single and double quotes to do? Dunno...
Single quotes could still be used for value names as I've speculated, but no need to rush that one.
Double quotes are still free at this point.
They prehaps could be used for strings with escape sequences, which would be funny because I would have arrived at the same place as lots of other languages, but sort of by going in reverse.
I'd rather leave them unclaimed for now and further investigate the string-alias-typing idea.


Summary Again
-------------
I'd better cut this off pretty soon, or split or move on.

* The basic string type is a raw literal
* The basic string type is delimited with backticks
* The outermost pair of backticks in the context are the deilimiters, everything inside is the string proper
* Context ends at the end of the line
* Type aliases can use different constructors, as long they return the main type
* String interpolation strongly recommended. Concatenation will not be implemented initially.
* Plain (undelimited) value and type names have fairly strict naming rules
* More complicated value names can be be achieved by quoting with single quotes
* Be able to recognise and handle multiline raw strings in the lexer/parser.


### Further notes/questions
* Is there *any* need or use for parentheses in silver-data?
* Is there *any* need or use for braces in silver-data?

https://en.wikipedia.org/wiki/Delimiter#Delimiter_collision