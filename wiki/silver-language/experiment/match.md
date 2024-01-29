Match
=====

I think this is going to be weird...

The only simple way i can think of for doing this is to reuse the name field for matching:

	match myVar
		1: doSomething
		3: somethingElse

Not sure I really want to do that...
Unless I radically change how things work in SL... I might need some new syntax??
For example I'd to be able to things like have expressions in matches:

	match myVar
		myVar > 5		: doSomething
		isEven(myVar)	: somethingElse

But that *really* puts pressure on what can be on the left side of the colon....

If all SL is SD, then pretty much any boolean expression, function call etc, becomes a valid SD name.

That would mean you 

Unless I change the rules, and make SL a superset of SD?
Or make special rules for parsing SL?

I dunno - it could get kind of interesting, but also get really really really confusing.
For instance this would weird, but kind of readable:

	myVar:
		'b=5'		: abcd
		'sqrt(100)'	: false
		'false'		: 37

But without the quotes it could get really pretty misleading.

I might sit on this for now and see what turns up elsewhere


