
Everything is a collection
==========================

This is an idea that I had half wanted and had influenced some things in my thinking.


But it leads to some ambiguities in the way certain constructs are interpreted, so it's worth spelling it out explicitly and watching for it in other areas to make sure i'm not accidentally mixing the ideas.

I suspect it will be easier in the long run to not go down this route, particularly in Data, however nice it might have been.
There may be other ways to reintroduce some of these idea in the Language section.







'single' member blocks
----------------------
This really needs to be clarified, as it's going to crop up in all sorts of places and be really quite important.

Are these the same or different:


	name: value						...a1


	name:							...a2
		value

I subconscously hinted in the brace syntax that they're different:

	name: value						...b1


	name:							...b2
		{
			value
		}


But in a way I'd always thought they were the same.
This needs unpacking.
It might have something to do with my vague idea of 'everything is a collection' that i've been sort of thinking about, but have no idea if it's pratical, even slightly.

So for now because i don't know the practicalities, lets just play some thought games.

Using the brace (b) forms first because they have a pretty stock traditional interpretation.

b1 means that there is an identifier that identifies the singular value
b2 means that the identifier denotes a structure that has 'value' as one of it's members.
	it's not clear whether here 'value' is itself an identifier, or just a member value.
	the general idea is that anonymous things are values, so it's a value for now

So for instance

	a:
		b
		c
		d

in that case b, c and d are values, and the equivalents in brace syntax are

	a: { b, c, d }

	a:
	{
		b
		c
		d
	}

 (I think i actually wanted the linear separator to be a semi-colon, but whatever)

As they're anonymous at this point you reference them as a, a.1, a.2 etc
I think what I wanted was for groups to be automatically created and unboxed,

So this whole question comes down to whether these two are the same or different

	name: value						...1
	name: { value }					...2


And whether they can be made the same or not. And also what happens when you do this:

	name: { name2: value }			...3

1 and 3 both have pretty well understood meanings, but 2 would actually be novel in most languages. Usually indexed or unnamed collection use an array syntax in that case like:

	name: [value]

I think for now to make things simpler I'll stick with distinguishing the singular from the multiple.
I really did want some sort of way of doing 'everything is a collection', but I'll leave it for now.
There may be some other way of allowing it by having a box or option type that auto-wraps/unwraps.
Or even a loop or iterator construct that handles singles the same as collections.


So in singles-distinguished:

	name: 						name -> empty value
	name: {}					name -> empty collection

	name: value					name -> single value
	name: { value }				name -> collection with one anonymous value
	name:
		value					name -> collection with one anonymous value

	name: { name: value }		name -> collection with one named value
	name:
		name: value				name -> collection with one named value


And in everything-is-a-collection:

	name:						name -> empty collection
	name: {}					name -> empty collection

	name: value					name -> collection with one anonymous value
	name: { value }				name -> collection with one anonymous value
	name:
		value					name -> collection with one anonymous value

	name: { name: value }		name -> collection with one named value
	name:
		name: value				name -> collection with one named value


So that kind of clears up the confusion.
Best keep an eye out for it.




But what about types?
---------------------

Buuuut.... does this actually gloss over some details?

	name: value

Truth is unless we have a default type, or a way to determine types based upon information within the value itself, this is actually insufficient.
What we actually need is something like:

	name:
		value: 'hello, world'
		type: string

For a data language this would mostly be a bit of a burden, so entirely optional.
Automatic typing based upon values is probably easier on the eye.
For example using rust's primitives you could pretty easily distinguish

	integers	- signed and unsigned
	floats		- signed and unsigned
	booleans

And with the addition of non-primitive string type you'd have nearly everything you need to get started.

So perhaps the above discussion about everything is a collection hid another detail:

In silver data even 'primitive' values are collections, or can be destructured into collections.
But the rabbit hole cannot be infinite, so let's see if it can be stopped:

	name: value

...means...

	name:
		value: ~some value~		either compound or primitive
		type: ~some type~		either compound or primitive


So each of those could go on until the tree terminates, usually at primitives.

Apart from primitive values terminators might have to include:
	references, themselves primitive, otherwise the tree becomes a graph with potential for cycles
	abstract types, or certain kinds of type expressions that don't resolve to concrete types

While we're at it there could be a zillion other ways to destructure a primitive or make it compound in some way.
The simplest exmaple is just providing more metadata:

	name:
		value: some concrete value for simplicity
		type: some concrete type
		description: it's fab
		comment: use it everywhere to make things sparkle


But really the possibility of decomposing any value is just a fact of life, and not especially controversial.
So in that sense, yes, every value could be (and might need to be) a structure, to hold things other than just it's raw value.
But decomposability is *not* the same as multiplicty.

So 'what about types' is about decomposability.


Back to multiplicity
--------------------
So if we take it for granted that anything *could* be decomposed, but that we have under control, what if anything can we say about multiplicity (the original question)?

Tbh honest at this point most of the stronger ideas pertain more to silver-language than silver-data.

In data i'll stick with idea that single and collections are distinct for now.



Syntax for multiplicity/generics
--------------------------------

This is going to be very preliminary, just explore some options.
The most obvious place to store this is in the metadata.

syntax for multiplicity

	player: type
		name: string
		position: number

	team: [1...12] of player

	team.player.1:
		name: 'Ken'
		position: 7

	team..type = [1...12] of player
	team..type = array[1...12] of player
	team[1]..type = player
	team.1..type = player
	team..index.type = integer
	team..index.first = 1
	team..index.last = 12
	team..index.before = 0		// or maybe undefined, depending on circumstances
	team..index.after = 13		// or maybe undefined, depending on circumstances
	team.1 =
		name: 'Ken'
		position: 7



That all looks not too bad as far as it goes. Array is a fundamental type in silver. But What about other types of collections?
What if I want a graph of bus stops?

	busStop: type
		location: coordinates
		ident: alphanumeric


	busStopNode:
		busStop: busStop
		adjacent: []busStop

	graph:

	busStopGraph: array of busStopNode

Hmmm in this case a graph is also just an array - is there a collection that can't be simply expressed as an array?

	stack
	queue
	list
	map
	vector

If we're oo-style then the presence of methods would prevent things from being simple arrays, but otherwise, nearly everything i can think of is an array of some sort or another... hmmm.
I'll shelve this thought for the moment.

Just a few other ideas i had about array syntax

	winners: [gold,silver,bronze] of competitor			// an array with just those three keys

	non-winners: [4...] of competitor					// positions 4 onwards

	competitors: [0...]									// traditional zero-based array
	competitors: [1...]									// 1 based array

	excelRow:	[aa...]	of cell							// auto incrementing alpha starting at aa
	postion: [integer]
	struct: [alphanumeric] of any						// kind of equivalent to a standard associative array












