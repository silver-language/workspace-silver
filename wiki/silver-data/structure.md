
Structure
=========

Everything should be parseable into basic name:value structures.


Basic syntax
------------
Child scopes delimited by tabs.
Colons are mandatory for single lines (where no other block inidicators are in use), but otherwise optional, though recommended.


name: value


name
	value

name
	value1
	value2
	value3


name
	name1: value
	name2: value
	name3: value


name
	name1
		value
	name2
		value
	name3
		value


name
	name1
		value1
		value2
		value3
	name2
		value1
		value2
		value3
	name3
		value1
		value2
		value3





Explicit and implicit names
--------------------------

Anywhere that you go

	name: value

	name:
		value

	name:
		value
		value
		value

You create an explicit name, ie one of your creation and knowledge
Implicit names are also created for every line of code and structure.





Block ends
----------

Ends aren't required in the normal syntax, but are useful for readability in large blocks.
Blocks can be closed explicitly with either the end keyword alone, or the 'name end' construct.

name
	name1
		value1
		value2
		value3

	name2
		value1
		value2
		value3
	end

	name3
		value1
		value2
		value3
	name3 end
name end






YAML
----

I'll be honest it looks a fair bit like yaml, but i wasn't trying to copy it or anything.
Just similar goals, similar solutions.
I don't have at this a separate list syntax though, and even if i did it wouldn't use dashes (ugh).

Also two spaces yuck.






TODO
----

	clarify the difference between these two so i get terminology correct:

	https://en.wikipedia.org/wiki/Associative_array
	https://en.wikipedia.org/wiki/Record_(computer_science)
