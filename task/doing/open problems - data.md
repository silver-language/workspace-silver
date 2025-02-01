Open problems - data
====================

```yaml
type: overview-task
category: silver-data
status: partial progress, ongoing
priority: low
```


References
----------

I need a way to have references to other parts of data:

* within a document
* to another document
* to an aliased document (import)
* to a global scope

Also need to determine how to type a reference, for eg:

	student: array
		name: string
		course: -> course-list.item

Or just:

	student: array
		name: string
		course: course-list.item


I'm not sure that I need a special syntax for this - is it as simple as just stating the type?
This last example also requires that we need a way to specify things like one-of, one-or-more-of etc.

I'm pretty sure this is going to be rather more involved.



Aliasing (imports)
------------------
Often called something like import. I don't like that much - it seems to me to often just be a shortcut reference, or an alias.
Need way to specify aliases relevent for a document.

Could be something straightforward like:

	alias:
		file: silver.core.system.file
		date: silver.core.time.date
		class: module.university.course.class

This seems to suggest I don't need a special syntax for references, but not sure yet.
There may more cases to consider.


Module allowances/restrictions
------------------------------

Other than just aliasing certain modules to make them easy to use, I want ways to explicitly state what is and isn't allowed in certain contexts.
This is important because I want language features and modules (beyond a core minimum) to be explictly declared.
The scoping of these allowances/restrictions will need some consideration.


Collections of items-of-type (Generics)
---------------------------------------

	Student: Array
		name: String
		course: String

	Class: Array of Student

I've used the 'of' syntax informally in a few discussion bits, but I need to decide on something.


Placeholders for generics
-------------------------

Using the above example, if we're creating a small class

	class101: Class
		Student
			name: Carol
			course: medicine
		Student
			name: Bob
			course: biology

In these examples 'student' becomes a generic placeholder so the indentation makes sense.
I'm fine with that, and it allows some nice things like lambdas.
But in some cases it might get cumbersome, so I've wondered if you could do something like this:

	class101: Class
		*
			name: Carol
			course: medicine
		*
			name: Bob
			course: biology

Where the types were well known.
It would have to come as secondary consideration though, after all more important syntax was decided, particularly path matching/references that could profitably use an asterisk.


The difference between one-of-an-item and many-of-an-item
---------------------------------------------------------

Say you had this schema:

	student: array
		name: string
		course: string

	class: array of student

The presentations look the same for one-of-a-student and an array of length one of a student:

Single student:


	1001: student
		name: Alice
		course: medicine


Array of student:

	1001:
		name: Alice
		course: medicine

Without more context these look the same.
I'm not sure this is a problem just yet - context might clear it up just fine.



Text that happens to begin with a type
--------------------------------------

	myBlock: SomeType
		Integer is a type of number
		String is a standard type
		Function is a special kind of block
		Boolean can only be true or false

How do we allow text like that?

### Force SomeType to only allow string children

	myBlock: Array of String
		Integer is a type of number
		String is a standard type
		Function is a special kind of block
		Boolean can only be true or false

### Require quotes around strings

	myBlock: SomeType
		'Integer is a type of number'
		'String is a standard type'
		'Function is a special kind of block'
		'Boolean can only be true or false'

Requiring quotes is probably a bit better because it's more obvious, but string-only blocks could be done.



Using Type names for block ends
-------------------------------

So far I've only used ordinary names for block ends:

	foo: Array of String
		lorem ipsum
		dolor sit
		amet
	foo end

But there are a couple of cases where it might be useful to end the block with the type instead.
The most obvious is Types block themselves:

	Function: Type
		type: Type
		parameter: Array of Parameter
		result: Any
	Function end

That's pretty straightforward, it's just the name again, but this time the type - I'll make this mandatory.

The other one though is for anonymous blocks (blocks without names) - let's try with a lambda:

	Function					// no colon, this is the type of the block, not the name
		type: String
		parameter:
			string: String
		result: frobnicate(string)
	Function end

Okay so it looks the same as typedef end above, but in this case it's ending the block of the anonymous function.
In all previous discussion I'd only allowed an anonymous end like this:

	Function					// no colon, this is the type of the block, not the name
		type: String
		parameter:
			string: String
		result: frobnicate(string)
	end

Need to decide on one of these.
There'll be a few use cases to consider - large data documents will be one.
My initial preference is enforce named-only for block ends for consistency.
For large nested documents where named ends are probably the most helpful, it's probably better to for the user to actually just use a name, but we'll see.



When block ends are required
----------------------------

This one irks me a bit because it's slightly inconsistent, but I want to make block ends mandatory for all but the innermost blocks.
I'll see how that works out.
It might make things weird, for instance without editor support, indenting and outdenting might require additional edits.
With editor support, indenting and outdenting would add or remove block ends as needed.


