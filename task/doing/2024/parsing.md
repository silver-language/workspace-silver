
Parsing
=======


https://www.perl.com/pub/2012/10/an-overview-of-lexing-and-parsing.html/
https://www.reddit.com/r/ProgrammingLanguages/comments/gdt3xd/why_lexing_and_parsing_should_be_separate/
https://github.com/oilshell/oil/wiki/Why-Lexing-and-Parsing-Should-Be-Separate
https://stackoverflow.com/questions/2842809/lexers-vs-parsers

https://en.wikipedia.org/wiki/Context-free_grammar



While there are still a few design decisions left to iron out, here's the start of some parsing ideas.



Algorithm sketch
----------------
One big loop over file lines:


start

	contextIndent = 0


	filemap:
	{
		line...
		{
			number			// line number in file
			text			// raw text of line
			indent			// tab count
			data			// text minus indent
			block			// pointer to datastructure
		}
	}


	datastruct:		// where we're constructing the datamap
	{
		...$blockname...
		{
			(block | value

			)
		}

	}


	for line
	{
		if not empty
		{
			lineIndent = consume tabs before text
			text = text after indent

			match (lineIndent - contextIndent)
			0:
				comment: same level as the context, continue adding to it
			1:
				comment: we're in one from the context, a new scope is starting
			>1:
				comment: this is an error, cannot do
			-1:
				comment: close the current context and returning to the parent
			-x:
				comment: close the current context and return x levels above

		}
	}
end



File datastructure
-------------------

file map structures

	package

		directory

			filename
				line
					indent
					assignment -> instruction or block
				line
				line



Data datastructure
------------------

During processing - this might become the 'private' datastructure:

	block
		source -> file.line.char
		assignment
			sequence number
				source -> file.line.char



After processing the 'public' datastructure:

	block
		assignment
		...



Langauge datastructure
----------------------

	block
		source -> file.line.char
		assignment
			sequence number
				source -> file.line.char





Return after a while
--------------------

AST nodes

	file:
		line*

	line:
		blank line
		| indent* statement

	statement:
		assignment | expression | block end

	assignment
		name : expression

	expression
		typedValue | type | value

	typedValue
		type value

	type
		capitalised string | type expression

	value
		string beginning with lowercase or number

	type expression
		unknown just yet

I need to clarify statements and expressions.
In silver bare expressions are assignments of sorts, but need to clear this up.




My first naive thought is to split it all down by regex, but this will create half tree/half lexed symbols.
The lines will be lexed into symbols, but blocks not gouped into trees.
Needs to refine.

This might be useful for building a line/character map though.

I could be used as a first pass maybe?

A second pass for grouping the blocks?

Things I think I want:
	Every node/piece to have information about where in the source file it is - line,column - 1 based
	Perhaps a unique identifier per node (could be optional?)





Lexing and/or parsing
---------------------

I really think I need to take a step back here for a bit.
There's *loads* out there on lexing and parsing and I'm not sure I've really gotten much of it.

https://github.com/oils-for-unix/oils/wiki/Why-Lexing-and-Parsing-Should-Be-Separate

* the lexer should only produce a stream of symbols, ie something like an array
* Lexing should be easy and fast
* Parsing is likely to be slow and complicated
* lexing should stay the same while parsing can change


https://stackoverflow.com/questions/2842809/lexers-vs-parsers

* Symbols for the lexer: ASCII characters.
* Symbols for the parser: the particular tokens, which are terminal symbols of their grammar.


https://rustc-dev-guide.rust-lang.org/the-parser.html
* lexing produces streams of tokens
* parsing turns the tokens into an AST


https://cs.stackexchange.com/questions/39898/why-separate-lexing-and-parsing


https://softwareengineering.stackexchange.com/questions/128888/are-separate-parsing-and-lexing-passes-good-practice-with-parser-combinators

https://cs.stackexchange.com/questions/28858/expressive-power-of-lexer-parser


Silver-data Lexing and Parsing
------------------------------

The main thing I've been doing differently so far is to output a symbol tree instead of a symbol stream.
I think this is mainly because breaking down silver-data is relatively straightforward.
I think this will probably still be okay, as long as I don't attempt any logical/syntactical analysis in the initial phase.

So I'll set myself some guidelines:
* No proper logic in the lexer, eg it should be done mostly with regex
* Save things like syntax errors for the parser


Also I think I've gotten my naming wrong - I think the parser outputs the AST, and the lexer outputs symbols/tokens -


