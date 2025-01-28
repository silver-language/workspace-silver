Lexing Strategies
=================

Need to sort out different ways to do line-lexing and come up with set of algorithms.

```yaml
type: task
status: in progress
blocks: lexing
priority: high
```

I currently have a basic lexing strategy, dumb lexing, that assumes a simple well-formed line.
However it's not very adaptable to things like quoted names and values that I'll need soon.
I'd started this discussion in a task in silver-data-go but I want to ramble a bit more so will restart in here.

Preamble
--------

Prior to the dumb-lexer I'd started a somewhat too complicated setup with structures and regex for breaking down the parts of the grammar.
It was premature and overcooked, so I chucked most of it out to focus on getting *something* working, yielding the dumb lexer.
As stated, it's not very flexible so I want more options.

Silver data is super simple so this *shouldn't* be hard, at least you'd think.


Things getting in the way
-------------------------
Some things I've wanted, but shouldn't be blocking progress at this stage.

### Configurable characters
I'd have liked to be able to make things like indents, name separators, quotes and other other delimiters, all configrable.
So for example you could have a file or a folder or project with different values for those.
That would be interesting, but it's totally a red herring for now.
I shouldn't let considerations for this block progress - it's extremely low priority.

### Configurable lexing features

I've wanted to be able to put some lexing features behind feature flags, for example

* simple names / quoted names / dynamic names
* simple types / delimited types / dynamic types
* simple values / quoted values / dynamic values

By feature flagging these I could switch them to see what effects they have, etc.

But... it's going to massively complicate things right now.
It'd better to have a minimum set going than get stuck trying to accomodate all the cases.
And it would also require a way to codify the flags, which I don't have, so it too is mostly a red herring for now.

The minimum I think I need for now is:
* simple names
* simple types
* quoted values
And *maybe* quoted names.

I do want to return to this though. I could just set them as internal flags for now.


Lexing Strategies
-----------------

Onto the main show. This all pertains to line-lexing strategies.

Categories:
* Broad regexes - the dumb lexer, okay for simple well-formed lines, not very flexible
* Sequential tokens - traditional lexing strategy
* Initial character - useful in some cases to cut down line type possibilities
* Final character - similar to above, only useful in a handful of cases
* Final word - may be able to identify block-ends; could be misleading; not likely useful

The hope is that by combining a few of these I might come up with something better and more flexible than what I have currently.



