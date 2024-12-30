Colon Formatting
================

*Are rules about colon formatting needed?*

```yaml
type: decision task
category: syntax
status: in progress
blocks: lexer/parser
priority: low
open: 2024-12-30
```

Formatting options
------------------



So far I've been lasseiz faire about colon formatting, as it's not really high priority.

So these would all have been fine:

Simple values:
```
a:1
b: 2
c : 3
```

Blocks:
```
myblock:Block
	d:4
	ee: 5
	fff : 6
	gggg	: 7
```

Most of this can be deferred to a formatter, for instance in the block case I prefer this as it lines up the colons:
```
myblock: Block
	d    : 4
	ee   : 5
	fff  : 6
	gggg : 7
```

The only really mandatory decision for lexing/parsing is whether or not I should enforce any space around the colon:
```
a:1			// syntax error?
b: 2		// require space after the colon
c :4		// require space before the colon
d : 3		// require space on both sides of the colon
```

Initially I'm inclined not to take a stance on these in the lexer/parser, and just leave these these as formatting issues, though in practically all cases I prefer space after (b).
Sapce before only (c) looks pretty weird to me.
Space around (d) nost of the time.
The only time I'd tend to do (b) is for block starts.

```
myArray1: Array			// like this
	foo : bar

myArray2 : Array		// not this
	foo : bar
```

But it's no biggie.
Back to the space after, I can't think of any case where I'd actually prefer it to be absent...
Should I make that mandatory?


