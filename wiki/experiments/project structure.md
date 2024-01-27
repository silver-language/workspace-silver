Project Structure
=================

Here I'm going to throw around some ideas about how silver as a project is structured overall.

* silver-data
* silver language
* silver-core (???)
* other silver modules / libraries / plugins


silver-data and silver-language
-------------------------------

My intial idea was to only have these levels, silver-language building on top of silver-data, but I need to go into more detail here.

Both of them will end up consisting of various kinds of modules, some central, some secondary.

For instance the absolute minimum needed to do silver data would be (I think):

* strings for names and values
* trees to put names and values into

But there are a few more parts that are probably needed:

* Some sort of ordinal or implicit naming system for maintaining the order of nodes in the tree - eg integers
* A base system for allowed names, and variants - a subset of string
* A basic type system that can expanded upon
* The ability to reference other nodes, locally or externally


There are a few questions that could arise from this:
* Will these be the same for sd and sl?
* Can the type system or ordinal system be made optional for interaction with other languages?
* What parts would be necessary for writing a silver-data parser for another language?

And the more general questions:
* Is a silver-core project needed, and if so where does it sit in relation to sd and sl?
* How do modules work in each project?
