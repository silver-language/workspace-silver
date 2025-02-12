Document Format 2
=================


Ref:
* [journal - document format](./2024/2024-03-29%20-%20document%20format.md)
* [silver data - example - document format](../wiki/silver-data/example/document%20format.md)



Using Ideas from String Types
-----------------------------
From: [string types](../task/doing/string%20types.md)

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

