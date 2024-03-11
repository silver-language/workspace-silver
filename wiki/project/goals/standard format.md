Standard format
===============

I'm extremely impressed by, and jealous of, Go's gofmt. 
It completely eliminates a whole host of debates so people can just get on with it.
It's a genius move.


I'll be honest I had originally wanted some options in the way the language could be written, eg the brace syntax and optional block ends.
Not sure if that's the same thing though - options on what you write isn't the same as how it's presented.

So it could be taken to different levels, possibly:

1. Have different ways to write the code, but only one way to format it
2. Have only one way to actually write it in the first place, and only one way to format it.

I think the second might be a bit hardline, but i'll entertain both for a bit just to see what falls out.


Only one format
---------------

That might mean:

* enforcing indent whitespace
* enforcing specific padding around colons, brackets, other puntuation etc

* allowing brace syntax, but enforcing the way it looks

On the last one, it might be something like inlining the innermost blocks, but Allman style everywhere else. 


Only one way to write the code
------------------------------

That might mean:

* no brace syntax, or a strict set of rules about how to write it
* a strict set of rules on when and what block ends are needed
* maybe a strict placeholder for generic/anonymous types

probably some other stuff


Other options?
--------------

I think there might be a nice cozy spot somewhere between those two.

* definitely the whitespace enforcements
* some rules around block ends, such not needed on innermost blocks, end-only required the next layer out, and full block ends on all subsequent outer layers

One possibility for brace syntax might be to disallow mixing, ie have a file *only* be one or the other.

That's probably sensible for other reasons too - can have separate parsers, extensions.

I'll sit on it for now.
