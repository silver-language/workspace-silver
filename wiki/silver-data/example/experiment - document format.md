Experiment: Document format
===========================

```yaml
type: experiment
category: silver-data
status: mostly done, can be tidied up and added to wiki
priority: low
```


This stems from a shower thought - what might a simple document format look like in silver?
For example something that could work as an alternative to markdown or basic html.

Markdown is nice and lightweight, but it's not standardised, and doesn't have any obvious structure.
Structure is easy to create in html, but it's more verbose.

What I'd like is something that's a little more structured and standardised than markdown, but lighter than html.

Some initial features that would be wanted:
* headings
* sections
* paragraphs
* links
* lists
* some other block types like code, quote, image etc

That would do for starters.
For the moment I'll leave out lightweight markup like bold, italics, strikethroughs etc.


First thoughts
--------------

I suppose most or all would becomes types, so if we stick with

	name: Type value

Then you might get things like these:

	myDoc: Document
		myheading: H1 This is the heading of the document

		p1: Paragraph
			lorum ipsum
			dolor sit amet

		help: Link http://localhost/help

		items: UnorderedList
			item 1
			item 2
			item 3

		instructions: OrderedList
			do this
			then this
			finally this

		script: Code
			10 print "Hello world"
			20 goto 10
	myDoc end

Well that's the basic idea, and seems like it would accomodate a certain amount structure.
The names become like ids, which could be useful for anchors and such, but could also be ommitted as anonymous nodes:

	myDoc: Document
		Title 'This is the heading of the document'

		Paragraph
			lorum ipsum
			dolor sit amet

		Link http://localhost/help

		UnorderedList
			item 1
			item 2
			item 3

		OrderedList
			do this
			then this
			finally this

		Code
			10 print "Hello world"
			20 goto 10
	myDoc end

Though this shows how a bit of confusion can turn up about what's the type, and what's the value - in this case the H1.
How do we know that the H1 isn't part of the value?
There would have to be ways to clear it up, otherwise we're in an ambiguous state.
Normally initial caps indicate a type, so the parser would try to match it with a type; if it finds a match the type will be consumed.
So need a way to have a piece of text that happens to start with a type.
Probably do this most of the time:

	'H1 is how you write a first level heading'


With separate types
-------------------
This is just a quick bash, not too serious:

Types first:

	Document: Array of Element

	Element: choice of
		Title
		Code
		Quote
		Paragraph Link
		UnorderedList
		OrderedList

	Title: String
	Code: Array of String
	Quote: Array of String
	Paragraph Array of String
	Link: String
	OrderedList: Array of String
	UnorderedList: Array of String

At this point a fairly general document format might be a little ambitious becuase of it's open ended nature.
A slightly simpler example might be something like these task documents themselves.



Using Ideas from String Types
-----------------------------
From: [string types](../../../task/doing/string%20types.md)

```
myDoc: Document
	heading: H1 `This is the heading of the document`

	introduction: Paragraph
		`lorum ipsum`
		`dolor sit amet`

	H2 `Requirements`
	UnorderedList
		Paragraph
			`item 1`
			``
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

Documents with Code blocks containing backticks
-----------------------------------------------

Can code blocks from other langauges that make use of backticks work?

Golang
```
example-go: Document
	title: H1 `Go Example`

	code-go: Code
		const (
			IndentCharacter  = "\t"
			regexSplitIndent = `^(` + IndentCharacter + `*)(.*)`
		)
		var regexpSplitIndent = regexp.MustCompile(regexSplitIndent)

		func main() {

			message := `This is a
		Multi-line Text String
		Because it uses the raw-string back ticks
		instead of quotes.
		`
			fmt.Printf("%s", message)
		}

	code-go end

example-go end
```


JavaScript
```
example-javascript: Document
	title: H1 `JavaScript Example`

	code-javascript: Code
		console.log(`string text line 1
		string text line 2`);
	code-javascript end

example-javascript end
```


Markdown (this could get weird):
```
example-markdown: Document
	title: H1 `Markdown Example`

	code-md: Code
		Title
		-----
		This is some *simple* **Markdown** with some `backticks`
		```
			This is a fenced code block
		```
	code-md end

myDoc end

```

In each of these examples it's clear the `Code` type - whatever that is - is doing the heavy lifting.

Inside a `Code` block indentation rules (beyond it's own) and lexing/parsing would have to be suspended.
So if `code-foo: Code` and `code-foo end` are at indent x, everything inside is at indent x+1, and beyond that *everything* is a string literal.

So `Code` is probably an alias for `String-multiline`.
This also suggests string literals are the base form, which I think i want to decide upon.

It would be handy to have special rules in the lexer to recognize and do this to speed up processing of these blocks.


