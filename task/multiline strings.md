Multiline Strings
=================

Allow multi-line strings in Silver Data

```yaml
type: design/decision task
category: lexing/parsing
status:  wrapped up, in review
priority: medium-high
```


Ref:
* [string types](./string%20types.md)
* [experiment - document format](../../wiki/silver-data/example/experiment%20-%20document%20format.md)

Preamble
--------

One of the interesting things to come out of the string types discussion is the desire for dedicated multiline string handling.

The proposal is to handle something like the following purely as strings (which ordinary lexing/parsing would botch):

```yaml
textBlock : String-multiline
	“Beware the Jabberwock, my son!
	The jaws that bite, the claws that catch!
	Beware the Jubjub bird, and shun
	The frumious Bandersnatch!”
textBlock end
```

This could be useful for things like code blocks, markup, comments, ordinary text and prose etc.
The document format experiment has other examples where i've used the type `Code`.


Lexing/Parsing
--------------

For this to work it would be desirable to catch these as early as possible in the lexer so as to not waste cycles attempting to break it into language parts.

Which probably means the lexer would need to have a rudimentary concept of types.
Hmmm.
This might be tricky, but a very basic implementation might be doable.

For example if the lexer finds a String type declaration at indent x, followed by a line with *at least* x+1 indents, then go into multiline string mode for all subsequent lines while indent >= x+1.

You'd probably want to enforce an end-line for these, but it also might be possible to allow for its omission.
Not sure yet.


Recap: String line variants
---------------------------

Allowable string lines (single):

```yaml
	name1 : String						// Ordinary type declaration without value
	name2 : String `a basic string with declared type`
	name3 : `a string without an explicit type, either declared elsewhere, or implied`

	: String `An anonymous string; gets assigned a name`
	: `An anonymous typeless string; gets assigned a name, and type is declared elsewhere or implied`

	String `An anonymous string; gets assigned a name,`
	`An anonymous typeless string; gets assigned a name, and type is declared elsewhere or implied`
```


Anonymous String blocks
-----------------------

A couple of weirder variants - these would have almost no meaning on their own (as single lines), but are definitely be usable as block starts:
```yaml
	: String

	:
```

Some quick examples to explain:
```yaml
theGrandOldDukeOfYork: Array
	: String
		Oh, the grand old Duke of York,
		He had ten thousand men;
		He marched them up to the top of the hill,
		And he marched them down again.
	: String
		When they were up, they were up,
		And when they were down, they were down,
		And when they were only halfway up,
		They were neither up nor down.
theGrandOldDukeOfYork end
```

In this example `theGrandOldDukeOfYork` is declared to be an Array, and two String items will be added (automatically named 0,1 or 1,2 etc) with the items representing each stanza of the song.

Similarly you could do this and maintain explcit typing (typing is actually stronger here):
```yaml
theGrandOldDukeOfYork: Array of String
	:
		Oh, the grand old Duke of York,
		He had ten thousand men;
		He marched them up to the top of the hill,
		And he marched them down again.
	:
		When they were up, they were up,
		And when they were down, they were down,
		And when they were only halfway up,
		They were neither up nor down.
theGrandOldDukeOfYork end
```

This, while desirable, would be *much* harder to catch in the lexer though.

While I'm thinking about it, would there be any way to properly end these blocks? Elsewhere I've mooted the use of the type where nothing else is available - it would look like this:

```yaml
theGrandOldDukeOfYork: Array
	: String
		Oh, the grand old Duke of York,
		He had ten thousand men;
		He marched them up to the top of the hill,
		And he marched them down again.
	String end
	: String
		When they were up, they were up,
		And when they were down, they were down,
		And when they were only halfway up,
		They were neither up nor down.
	String end
theGrandOldDukeOfYork end
```

In this example I don't think that is any clearer, uglier if anything.
But there will be cases where something like this will be required, lambdas for example.

A plain `end` would probably be better:
```yaml
theGrandOldDukeOfYork: Array
	: String
		Oh, the grand old Duke of York,
		He had ten thousand men;
		He marched them up to the top of the hill,
		And he marched them down again.
	end
	: String
		When they were up, they were up,
		And when they were down, they were down,
		And when they were only halfway up,
		They were neither up nor down.
	end
theGrandOldDukeOfYork end
```

It also reminds that these mean different things:
```yaml
	foo end		// The value 'foo' ends here
	Foo End		// The Type declaration 'Foo' ends here
	Foo end		// The anonymous value of type 'Foo' ends here
	foo End		// This has no meaning - syntax error
```
See: [Silver-data - syntax - array](../../wiki/silver-data/syntax/array.md)


Can plain `String` be used for Multiline strings?
-------------------------------------------

So far it's been something like this:

```yaml
	simpleString: String `Hello`

	someProse: String-multiline
		FIRST WITCH
		All hail, Macbeth! Hail to thee, Thane of Glamis!
		SECOND WITCH
		All hail, Macbeth! Hail to thee, Thane of Cawdor!
		THIRD WITCH
		All hail, Macbeth, that shalt be king hereafter!
```

But is it necessary to specify `String-multiline` for these?
Could you make just plain `String` work for multiline strings?

```yaml
	moreProse: String
		SECOND WITCH
		Not so happy, yet much happier.
```

Again it would depend on being able to do a bit of lookahead.
Not sure if easy.
The line `moreProse: String` initially looks like a type declaration, and it would be if the indent continued at the same level.
But in this case the indent increases on the next line, which *might* be enough to suggest a multiline string follows.

The upside, if this could be made to work, is it might also allow for some other string aliases such as String-escaped and String-interpolated - the latter would lead naturally to things like document markup, for example:

```yaml
htmlTemplate: String-interpolated
	<!DOCTYPE html>
	<html>
	<head>
		<title>${docTitle}</title>
	</head>
	<body>
		<h1>${docHeading}</h1>
		<p>${docText}</p>
	</body>
	</html>
htmlTemplate end
```

One major difficulty with all of this is, again, the lexer has to know which Types can trigger multline mode. Beyong basic 'String' that could mean aliases or other string variants, but that gets way too complicated way too fast - there's no way to know all of them before parsing.

(Unless perhaps much further down the line if lexing/parsing of files in folders happened in a strictly ordered sequence it *might* be possible to have the right string types ready for lexing in the right places. Maybe.)

Built-in string types would have to be the initial implementation.


Strings are simple values
-------------------------

It occurs that there might be an apparent ambiguity, but I think it should work.

First some fairly straightforward string assignments, with a multiline:
```yaml
	title: 	String `Haiku No 1`
	author:	String `John Cooper Clarke`
	text: String
		To freeze the moment
		In seventeen syllables
		Is very diffic
```

No problems there, but what about this:

```yaml
	student1: String
		name: String `Alice`
		class: String `Communications`
	student1 end
```

This is intentionally misleading - it looks like an array, but it's actually a multiline string.

It's sort of an example of a [Sub-structured simple value](../../wiki/silver-data/syntax/syntax%20error.md), of which strings are a special case, and *not* a syntax error if multiline strings are available.



Lexing Trigger
--------------

Say we start by just looking for `String`, but this could be a list of acceptable Types.
How does the lexing trigger work?
I'm just going to throw out some ideas and what might work.

### Explcit type

Given you've hit a line of the form `name:	String` with no string literal assigned.

* Pre-read all of the indentation in the document first so the next line can be looked at immediately. Probably a waste, and in the case of multline strings the pre-computed indentation counts could very well be wrong.
* Just read the next line (if there is one) and see what it's indentation count is. If it's greeater than the preceding line then change over to multi-line string mode.

Honestly the second will work fine for explicit cases.

### Implied type

When the type is implied by the context this becomes *much* trickier, and probably not able to be done in the lexer alone.
Using two examples from earlier:

```yaml
theGrandOldDukeOfYork: Array of String
	:
		Oh, the grand old Duke of York,
		He had ten thousand men;
		He marched them up to the top of the hill,
		And he marched them down again.
	:
		When they were up, they were up,
		And when they were down, they were down,
		And when they were only halfway up,
		They were neither up nor down.
theGrandOldDukeOfYork end
```
```yaml
Poem: Array
	title: String
	author: String
	text: String
Poem End

poem1: Poem
	title: 	`Haiku No 1`
	author:	`John Cooper Clarke`
	text:
		To freeze the moment
		In seventeen syllables
		Is very diffic
poem1 end
```

The syntax for the former isn't frozen, but the point stands. In both cases we would have to know what the type of the node in question is to be able to do the lookahead.

One easy way forward would be to make the types explicit again (although redundant) - this could be caught in the lexer:
```yaml
	theGrandOldDukeOfYork: Array of String
		:String
			Oh, the grand old Duke of York,
			He had ten thousand men;
			He marched them up to the top of the hill,
			And he marched them down again.
		:String
			When they were up, they were up,
			And when they were down, they were down,
			And when they were only halfway up,
			They were neither up nor down.
	theGrandOldDukeOfYork end

	poem1: Poem
		title: 	`Haiku No 1`
		author:	`John Cooper Clarke`
		text: String
			To freeze the moment
			In seventeen syllables
			Is very diffic
	poem1 end
```

Other than that you're probably out of luck...
* Could you somehow parse all the types in advance? Probably tricky in a single document, especially if you allowed full freedom of ordering, but *maybe* in an imported set of types.
* Similarly can lexing and parsing be done sort of at the same time where the Lexer gets put on pause until the type can be identified?
* These might be workable if all the documents are well-formed and well-intentioned, but I reckon you could easily end in an infinite loop or deadlock in some cases. Even for some regular constructs it might get interesting if there are mutually dependent types. Not sure.

On top of all that, is it really necessary?
What's the worst the lexer can do in these cases?
For simple documents like silver data, not much ill would come of it; a few names or types might be incorrectly assigned, but these could be cleaned up in the parser fairly easily.
For a more complicated grammar like silver-language things *could* get out of hand.

I'm going to stick all of these in the too-hard basket for now, and just concentrate on explicit types.


Lexing output
-------------

Moving on to lexing output, assuming we've determined that a block is a multiline string, what should the lexer produce that will be comprehensible to the parser?

```yaml
textBlock : String-foobar
	“Beware the Jabberwock, my son!
	The jaws that bite, the claws that catch!
	Beware the Jubjub bird, and shun
	The frumious Bandersnatch!”
textBlock end
```

I have a line schema like this at the moment, though it's open for change:

```go
type Line struct {
	LineNumber    int
	LineText      string
	LineType      string
	Indent        Token
	Name          Token
	NameSeparator Token
	Type          Token
	Value         Token
}
```

* The declaration line would be lexed normally yielding name, separator and type tokens.
* I'm not sure if i've made good use of the LineType field yet, but it could be used to indicate that a multline string follows, given that we've already determined this.
* For the content lines you'd just fill the indentation and value tokens for the specific case, and the name, separator and type tokens would be empty.
* The actual joining and parsing would take place in the lexer.

I think that would work for all the simple cases i care about so far.



Wrap Up
=======

I think I've covered most of the things I need here for now.

To summarize:
* Given the right circumstances the lexer can branch and treat a sequence of lines as a multi-line string
* Initially these will be lines with an explcit String type declared followed by an indented block
* Potentially allow for accepting other in-built string types
* Implied or contextual string types can't be done yet - far too involved
* In the lexing output use the LineType field to indicate the start of multiline string
* String content lines only have indent and value tokens filled
* Joining of multi-line string is left to the parser

