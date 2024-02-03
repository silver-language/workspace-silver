Figure out Scope and References
===============================

This might get heavy, might not.

The rules for silver language will probably be a bit more strict, for instance I think I want functions to be pure.

There are no functions in silver data, so that's one less concern, but otherwise I'm dealing with similar problems.


Scopes to deal with:

* universal - things are core silver
* modules/plugins - whatever is brought in and allowed
* project
* directory
* file


Universal and Modules
---------------------

These should gain canonical namespaces, something like

	silver.core.system.file
	silver.core.time.date
	module.blah...

etc

Project, directory and file
---------------------------

A project will define it's own namespace, from which you can use relative paths

	myProject/component/util

Or construct logical paths using an alias like system

path:
	project.core : myProject/component/util


Within a file you'd use dot syntax for the file structure:

	service.myHandler

It might be possible to combine these:

	myWebservice/api/web/fooEndpoint.getAllFoo



So at this point it'll seems that we'll need two different systems - logical paths and literal/relative paths.

I think it would be smart at this point review how a few other languages handle this - I'm not smart enough to get it right without some help.


Some other things I'd also like to with these:
 * visibility/readability - can the path be found/read?
 * execute permissions	- can the path be used/executed?



Review other languages
----------------------
Gonna start with rust, go and node.
