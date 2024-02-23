Reading and Writing
===================

Silver is for humans.

Easy to read. Easy to write.

* use whole words
* be general where you can, but specific when needed.
* should be fairly readable without an ide or syntax highlighting
* don't use slang or jargon where a plain word is available





https://www.reddit.com/r/ProgrammerHumor/comments/rlgkbl/i_know_a_programmer_when_i_see_one/





Syntax
------

https://www.reddit.com/r/ProgrammingLanguages/comments/1ajo99d/why_not_use_guillemets_and_for_type_parameter/

https://go.googlesource.com/proposal/+/refs/heads/master/design/43651-type-parameters.md



Terminology
-----------


### Don't capitalise anything that doesn't need capitalisation


And even then avoid capital letters unless really necessary.

Everyone will know what you mean if you type http.

	select
		not
			SELECT
	constant
		not
			CONST
			CONSTANT

Don't capitalise verbs - I'm looking at you C#.


### Don't shorten or contract words unless really necessary

For keywords this will be mandatory, for your own variables, a guideline.

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
			(but preferably text)
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



### Avoid verbs

This is more to do with:
	data-orientation
	declarative rather than imperative programming
	immutability
So probably deserves a separate article.



### Avoid CS jargon where a more straightforward word exists

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


### Avoid Plurals

Use singular form even when addressing a group.

	so cat[1]
	not cats[1]

	product[xyz]
	not products[xyz]

	child[0]
	not children[0]



Plurals have funky rules in english so best to avoid.
Also the most common form of plural, the addition of an 's', is easily confused with a verb,
	eg
		imports
			(n) things that are imported
			(v) the act of importing



### Avoid idiomatic english

This one might be difficult to be objective with.
Try to be clear to as wide an audience as possible, not just your company, region, demographic, country etc.


### Avoid ambiguity

Along with the above, avoid using words that have multiple meanings, where your chosen meaning isn't obvious.
The node.js 'imports' keyword in an obvious example.



### Avoid terminology trying to be trendy, cool, funky, cute, hip, obscure

Use ordinary conventional syntax and grammar for your language.
Avoid:

	txt spk
	l33tsp34k
	emojis ;-)
	anything that requires looking it up on Urban Dictionary
	memes

We're normal humans, most of that ages badly.
If you're doing something truly iconic like sending a rocket to Jupiter then maybe, otherwise normal words are sufficient.





References
----------

https://tech.slashdot.org/story/20/06/10/1922255/tech-terms-face-scrutiny-amid-anti-racism-efforts
https://tech.slashdot.org/comments.pl?sid=16549610&cid=60168670

https://developers.slashdot.org/story/20/06/14/1722223/github-android-python-go-more-software-adopts-race-neutral-terminology
