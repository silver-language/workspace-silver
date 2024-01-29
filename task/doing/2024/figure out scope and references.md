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

	silver.core
