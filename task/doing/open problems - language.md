Open problems
=============





### Specify a type that contains other types, but not values

Eg in a the type of Function, the parameters accept types, but not values.


	Function: Type
		parameter: Array of Parameter
		type: Type
		result: Type or Value
	Function end

	Parameter: Type

Something like that.
But not sure yet.




### Interfaces vs types
Is there a need for a distinction here - or am i reading too much into it?


### Path matching

This is a generic version of references from silver-data (which I haven't even decided upon yet).

Say I decide something like this for references:

	project.moduleName.item.child[3]

or whatever, I also want to be to add things like wildcards, eg:

	project.*.item.meta.name

So i can get a list of item names in all modules (say).

This sort of stuff is present in lots of languages so need to do a review
* xpath



