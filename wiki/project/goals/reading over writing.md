Prioritise Reading over Writing
===============================

	Silver is for humans.


Lots of programming languages aim to be readable, but it's subjective, and depends on the background of your presumed audience.

Stating a language is 'readable' is a bit like saying "this car is drivable" or "that food is edible" - most are, but some more than others.

More generally, the '-ability' of a thing depends on purpose and who you're targetting.

So being readable depends - I'll try to articulate what I mean by readable here, and why.

But overall, readability gets higher priority than writability.



Prioritise humans over systems
------------------------------

Silver itself aims to be as widely read and as agnostic as possible, so tries not to be oriented towards any particular system**.

Your particular field likely has established vocabulary and symbols - when writing your data or module or program you should use them as appropriate to your audience, but try to write for humans first.

** with caveats


Prioritise plain language
-------------------------

All natural languages evolve and have time and place variations.
Use the plainest, most widely understood terms where you can.

* don't use slang or jargon where a plain word is available.

### Avoid idiomatic english

This one might be difficult to be objective with.
Try to be clear to as wide an audience as possible, not just your company, region, demographic, country etc.


### Avoid terminology trying to be trendy, cool, funky, cute, hip, obscure

	txt spk
	l33tsp34k
	emojis ;-)
	anything that requires looking it up on Urban Dictionary
	memes






Prioritise the vertical over the horizontal
-------------------------------------------

I'll have to try to find some research or something to back me up, but I think humans are naturally pretty good at scanning lists of things, or other spatially structured data like grids.

In text I think it's easier to achieve structure vertically, so that will be prioritised.


Prioritise nouns over verbs
---------------------------

Nouns are easier.

In human language we tend to learn the words for *things* before we learn modifiers such as tense, action, plurality, etc.

Nouns from other languages are learnt and borrowed quite readily, grammar not so much.

Things are are also easier to understand than processes:

* food is easier to understand than cooking
* animals are easier to understand than evolution
* numbers are easier to understand that rates of change

In computing parlance this means declarative over imperative.

Refs: https://en.wikipedia.org/wiki/Declarative_programming https://en.wikipedia.org/wiki/Imperative_programming


Nouns are more suggestive of data and imutability.


Prioritise collections over plurals
-----------------------------------

Natural language plurals can be weird and inconsistent, so avoid where possible.

Where the context allows it may be sufficent to use the singular:

* goose[3] over geese[3]
* child[1] over children[1]
* matrix[0] over matrices[0]

Ref: https://www.thoughtco.com/irregular-plural-nouns-in-english-1692634

Collective nouns where available, eg:

* team over players
* class over students
* fleet over ships
* portfolio over investments

Another strategy is to use a collection modifier:

* potatoBag over potatoes
* directoryGroup over directories
* propertySet over properties


### Collections are also more clearly nouns

There is an unfortunate ambiguity in english between some plurals and verbs.
Avoiding plurals aids clarity in such cases.

Examples:

>   imports (noun):   plural of import
>
>   imports (verb):   third-person singular simple present indicative of import


>   runs (noun):      plural of run
>
>   runs (verb):      third-person singular simple present indicative of run

>   errors (noun):    plural of errors
>
>   errors (verb):    third-person singular simple present indicative of error



Ref: https://en.wiktionary.org/wiki/imports https://en.wiktionary.org/wiki/runs https://en.wiktionary.org/wiki/errors




Prioritise lowercase over uppercase
-----------------------------------


Lowercase in english is easier to parse than uppercase.

https://medium.com/@benameji/uppercase-or-lowercase-9e01258e035c
https://ux.stackexchange.com/questions/72622/how-easy-to-read-are-small-caps-vs-lower-case
https://ux.stackexchange.com/questions/11043/all-capital-titles-good-or-bad
https://www.theguardian.com/media/mind-your-language/2010/oct/04/new-york-street-signs-capitals



### Don't capitalise anything that doesn't need capitalisation

And even then avoid capital letters unless really necessary.

Everyone will know what you mean if you type http.

	select
	constant

not

	SELECT
	CONSTANT

Don't capitalise verbs - I'm looking at you C#.

### Other thoughts

I had wondered at times whether it might be possible to translate the whole language, and whether using bicameral systems would hinder that.
I think now the translation idea is pretty unlikely, and wondering what if anything, capital letters coud be used for.

As hinted above I don't see much point in arbitrary or even convention-based capitalisation rules.
So some capitalisation schemes out there:

* whole keywords - seems to have been a thing in some older languages, SQL
* whole tags - data formats like XML and HTML in the early days, thankfully no longer
* verbs/method names - I've only seen this in C# - seems weird to me
* class names - not too bad
* constants - seems common in c-ish languages, not particularly fond of this, especially as immutability becomes more common
* public private members - Go uses an uppercase first letter to signify exported function and variables
* intercaps/camelcase - i think these are fine

So making something optional only to be picked and fixed by prettiers seems dumb - it becomes optionally mandatory.
At this point the only thing I can think of where a concept was important enough to deserve capitals, and make them mandatory, is types.

But even then not 100% sure. It would definitely make some code clearer, but maybe some parts uglier.




Priortise full words over shortenings
-------------------------------------

* Full words are easier to visually parse.
* Saving a few keystrokes while typing is a very short-lived gain

For example:

	function
		not
			f
			fn
			fu
			fun
			func
			funct
			...
	integer
		not
			int
	character
		not
			char
	string
		not
			str
	source
		not
			src
	variable
		not
			var
	object
		not
			obj
	constant
		not
			const



Prioritise readability without an ide or syntax highlighting
------------------------------------------------------------

Those things are great, but you might not always have them.
You might be:

* On someone else's computer
* On a slow remote connection
* On paper or a whiteboard
* On a phone
* Underwater
* In space

If it can be read and understood with a simple text editor, then good.





Avoid CS jargon where a more straightforward word exists
--------------------------------------------------------

Try to use to most obvious english meaning of words rather than cs jargon.

	string		-> text
	source		-> code, program text, program data
	(python)
		def 	-> function
	map
		not sure yet
		when used prefer map as a noun not a verb though

Prefer well established meanings in:
	ordinary use
	maths
	science



We're normal humans, most of that ages badly.
If you're doing something truly iconic like sending a rocket to Jupiter then maybe, otherwise normal words are sufficient.





Whitespace & formatting
-----------------------

Kevlin Henney - Seven Ineffective Coding Habits of Many Programmers
	https://youtu.be/ZsHMHukIlJY?t=1374


Linux kernel 80 char limit:

	https://lkml.org/lkml/2020/5/29/1038
	https://www.phoronix.com/scan.php?page=news_item&px=Linux-Kernel-Deprecates-80-Col
	https://www.phoronix.com/forums/forum/phoronix/general-discussion/1183214-the-linux-kernel-deprecates-the-80-character-line-coding-style
	https://linux.slashdot.org/story/20/05/31/211211/linus-torvalds-argues-against-80-column-line-length-coding-style-as-linux-kernel-deprecates-it?sbsrc=md


Area under indent:
	https://stevedower.id.au/blog/most-critical-python-metric

https://developers.slashdot.org/story/20/10/11/2127247/spaces-or-tabs-microsoft-developers-reveal-their-preferences







References
----------

https://tech.slashdot.org/story/20/06/10/1922255/tech-terms-face-scrutiny-amid-anti-racism-efforts
https://tech.slashdot.org/comments.pl?sid=16549610&cid=60168670

https://developers.slashdot.org/story/20/06/14/1722223/github-android-python-go-more-software-adopts-race-neutral-terminology


### Syntax

https://www.reddit.com/r/ProgrammingLanguages/comments/1ajo99d/why_not_use_guillemets_and_for_type_parameter/

https://go.googlesource.com/proposal/+/refs/heads/master/design/43651-type-parameters.md



https://www.reddit.com/r/ProgrammerHumor/comments/rlgkbl/i_know_a_programmer_when_i_see_one/

### Could other whitespace characters be used?

https://en.wikipedia.org/wiki/Whitespace_character

https://en.wikipedia.org/wiki/C0_and_C1_control_codes