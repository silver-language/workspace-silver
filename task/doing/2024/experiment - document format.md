Experiment: Document format
===========================

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

	Element: Title | Code | Quote | Paragraph | Link | UnorderedList | OrderedList

	Title: String
	Code: Array of String
	Quote: Array of String
	Paragraph Array of String
	Link: String
	OrderedList: Array of String
	UnorderedList: Array of String



With those in place,
