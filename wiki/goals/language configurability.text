Language Configurability
========================

Idea
	keywords, structure, properties, behaviour can be manipulated at a project or folder level

Description
	If you have a specific problem space that requires a specific kind of terminology/semantics
	you can override the base or common features of the language to your needs

Examples:
	In the base language I'd like to distinguish between functions (pure) and procedures (side effects)
	as simple starting types.

	But you may want to add additonal descriptive words to distinguish further between other kinds of
	functions - non-commutable, lambdas, higher order, side effects, relation, etc.

	It might be useful just to change the words used for certain constructs in a particualr problem space.

	You might want to (gulp) change the block structure and delimiting.
		With this one you could 'mimic' json for example.



Considerations:
	There needs to be an efficient way to mask or override one data set with another.

	There needs to be well defined boundaries for the configurability
		For example what happens when a an overridden project/subfolder references/uses another with different
		semantics?
		Especially when you've renamed something in the referred project.
		Proper namespacing would have to be enforced.

	Redefinition must be acyclic.
