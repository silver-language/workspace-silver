Starting or solo Colon
======================

```yaml
type: decision task
category: syntax
status: mostly done
blocks: lexer/parser
priority: medium
open: 2024-09-19
```


**Can a statement begin with a colon, like these:**

```yaml
: "A value without a name"
: SomeType
: Integer 1234

myStruct: Struct
	: val1
	: val2
```

Equivalent to anonymous
-----------------------

It looks weird, and it's not something I'd ever really intended, but in effect it would be another way of saying the expression is anonymous.
Those examples above would be the same as:

```yaml
"A value without a name"
SomeType
Integer 1234

myStruct: Struct
	val1
	val2
```

So I think there may be some uses for this in certain circumstances:

* Clarity - to make it clear that the statement is some type of entity expression, and not a name
* Placeholder - might work for typed anonymous blocks

I want to explore the second one.


Placeholder for typed anonymous blocks
--------------------------------------

In some previous discussions I've considered using types as placeholders for arrays of anonymous objects.

Say we have these types:

```yaml
Customer: Array
	name: String
	email: String

CustomersList: Array of Customer
```

And we want to construct a new customer document from a spreadsheet or something for inputting:

```yaml
newCustomers: CustomerList
	Customer
		name: Alice
		email: alice@example.com
	Customer
		name: Bob
		email: bob@example.com
```

In this case the new customers don't have their own key/id yet as they havn't been added to the database, so they're effectively anonymous thus far.
The `Customer` type is used a placeholder to give the objects structure - I've discussed this elsewhere.
However, the type of the members is indicated by the `CustomerList` type, so it's handy but a bit redundant - fine for a short document, but wordy for anything large.
Elsewhere I'd wondered if you could use a generic placeholder like an asterisk for cases like this, but could the colon do the job here?:

```yaml
newCustomers: CustomerList
	:
		name: Alice
		email: alice@example.com
	:
		name: Bob
		email: bob@example.com
```

It's odd, but in this case it sort of makes sense - the name is anonymous, and the type is known.

### Aside: brevity by usiing aliases

There might be other ways to achieve brevity in cases like this - for example if the type coud be aliased.
I have no established syntax for aliases, but could be something like:

```yaml
C: Customer			// C is another name for Customer
//or
C = Customer		// C equals Customer

// yielding:

newCustomers: CustomerList
	C
		name: Alice
		email: alice@example.com
	C
		name: Bob
		email: bob@example.com
```

I'll leave this as a thought for now.


Any problems?
=============
Any really terse syntax like this, especially where symbols are involved, could have problems.

* Negatively affect readability
* Higher chance of structure/syntax/formatting errors
* There'd almost certainly be cases where this would be a syntax error, so the parser would have to catch those

I'd say it wouldn't be too bad in large or auto generated/auto consumed documents where there's lots of repetition of structure, eg database/table/csv style style stuff.
But not so great for handwritten docs or anything with plenty of arbitrary structure, eg programs, documents.


Wrapup
=======
Leave this as a experimental/tentative recommendation.



