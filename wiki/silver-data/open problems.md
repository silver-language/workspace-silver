Open problems
=============



References
----------

I think I need a way to have references to other parts of data:

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


Collections of items-of-type
----------------------------

	student: array
		name: string
		course: string

	class: array of student

I've used the 'of' syntax informally in a few discussion bits, but I need to decide on something.


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
