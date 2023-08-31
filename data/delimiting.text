Delimiting
==========

Ways to demarcate items


In data formats and languaages a few strategies are used to group or delineate items.
Roughly I see them as usually being in these categories


	separation
		variants:
		terminator token
		start token

	wrapping
		same token
		simple paired opener/closer
		compound opener closer

	fixed-size
		items have specified numbers of characters or bytes


Separation
----------

The main characteristic is that tokens are placed between items

	item token item token item

	eg
		Many or most written languages use space as a separator
		https://en.wikipedia.org/wiki/Delimiter#Content_boundary


Termination places the token at the ends

	item token item token

	eg
		c-style semicolon terminated languages
		line end termination such as python


Start token would place the token at the beginning

	token item token item

	eg
		bullet list: * item1 * item2 * item3
		some inline comments might fall under this category when embedded within other forms
			-- sql comment
			// c-style comments
			# shell script comments


Combinations
	Different tokens can be used to combine the above into structures.
	Many common formats are in this category

	separation within separation

		item token1 item token1 item
		token2
		item token1 item token1 item

		eg
			CSV (t1= character, t2=newline)





Wrapping
--------
Items are wrapped or contained by matching tokens.


Identical tokens

	The simplest form is when the same token is used at the start and end of an item

		token item token  token item token

		eg
			simple quote characters "foo" and 'bar' for strings
			light markup such as *asterisks* for bold or _underscores_ for italics
			replacement tokens #value#

	Multi-char versions would work the same way, though I can't think of many examples right now.
	Occasionaly you see substitutions using multiples of the same char
		eg
			##value##
			@@value@@





Paired tokens

	where a set pair of start and end tokens wrap items

	single char examples
		ascii () [] {} <>
		Spanish punctuation eg	¿? ¡! «»
		Angled or open-close quotes “”

	multi-char tokens

		begin item end
		empty xml tags: <> item </>
		c-style comments: /* item */
		xml, html et al comments <!-- item -->



