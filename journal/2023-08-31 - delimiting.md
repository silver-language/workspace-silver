Delimiting
==========

*Ways to demarcate items*


In data formats and languages a few strategies are used to group or delineate items.
Roughly I see them as usually being in these categories:

* Item separators: start, between, and end tokens.

	Examples: bullets, numbers, and capital letters (start), commas (between), and semicolons and full-stops (end)

* Wrapping
	*	Identical tokens - eg single and double quotes, asterisks for emphasis, slashes for regex
	*	Simple paired opener/closer - eg brackets
	*	Compound opener-closer pairs - eg xml tags

* Fixed-size

	Items have specified numbers of characters or bytes


Main Types of Delimiting
------------------------

### 1. Separator tokens


Separator tokens are placed either at the beginning, between, or after items.

#### Beginning tokens

	token item token item

Examples:
* bulleted or numbered lists: * item1 * item2 * item3
* Capital letters used to start sentences
* Inline comments in many programming languages fall under this category when embedded within other forms

	-- sql comment

	// c-style comments

	\# shell script comments


#### Between tokens

	item token item token item

The comma is a simple example, but perhaps even more obvious is whitespace to separate words.

https://en.wikipedia.org/wiki/Delimiter#Content_boundary


#### After tokens, or termination

	item token item token

Examples:
* full-stops at the end of sentences
* line ends (carriage returns/line feeds) in text files and many languages such as python
* c-style semicolon terminated languages



#### Token combinations

Different tokens can be used to combine the above into structures.
Many common formats and languages are in this category.

	item token1 item token1 item
	token2
	item token1 item token1 item

For example CSV uses nested separators or terminators: token1 = comma, token2 = line end


### 2. Wrapping

Items are wrapped or contained by matching tokens.

	start-token item end-token


#### Same character tokens

The simplest form is when the same character is used as the token at the start and end of an item.

	token-character item token-character

Examples:
*	Quote characters for strings: "Alice" 'Bob' \`Carol\`
*	light markup such as *asterisks* or _underscores_ for italics; -strikethroughs-
*	replacement tokens: #value# %value%


Multi-character versions work the same way, eg:
*	##value##
*	@@value@@


#### Paired single character tokens

Where a set pair of start and end tokens wrap items.

	start-character item end-character


Single character examples:

* Standard keyboard characters: () [] {} <>
* Spanish punctuation eg	¿? ¡! «»
* Angled or open-close quotes “”


#### Static multi character tokens

A set pair of multi-character strings form the start and end tokens.

	start-token item end-token

Examples
* empty xml tags: <> item </>
* c-style comments: /* item */
* xml, html etc comments: \<\!-- item -->


#### Dynamic paired tokens

The start and end token pairs are defined depending on context/language.

	start-token item end-token

For example:

*	XML, HTML, SVG etc: \<tagname>item\<\/tagname>


Languages such as python probably more naturally fit into this category than start-token. In this form the indentation forms the start token and the line end becomes the end token.


	Some context
		subcontext
		subcontext
		...


### 3. N-ary constructs


Where a fixed delimiter set is used for a constructs of defined length. Binary and ternary forms are common in progrgamming languages.

#### Binary construct
This is just a standard separator form with length 2:
	first-item separator second-item
Common examples are assignment and binary mathematical expressions.


#### Ternary construct
Separator or start-token form, length 3, tokens usualy differ:

	start-token item1 middle-token item2 end-token

	start-token item1 middle-token-1 item2 middle-token-2 item 3

Examples:
* if *condition* then *item* else *item*
* condition ? true : false
* try catch finally
* regex s/search/replace/


### 4. Fixed size/width
No delimiters are (necessarily) used, but a definition of fixed sizes demarcates items. The only example of this I’ve directly worked on is ABA/CEMTEX. I presume many database raw formats are like this.


### 5. Modifiers
Not necessarily strictly a form of delimitng, but a way of visually marking boundaries within item data.
Examples:
	Capital letters at the start of sentences – do not change the meaning, but are a visual start marker.
	CamelCase variations
