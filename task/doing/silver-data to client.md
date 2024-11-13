Silver data to client
=====================

```yaml
type: epic
status: not started
blocks: publishing
priority: low
```

Thoughts
--------
This has been going through my head lately.
There are a few layers to this and how a parser for another language might work will probably depend on what features that language has.

Ideally:
* create named types dynamically as specified
* translate silver-data specified types to something locally applicable


A few ideas, depending on what's available
------------------------------------------


### Omit the types altogether

Eg json with no schema

Just provide basic structs/objects with the values in whatever seems most appropriate.

Not too hard for leaf nodes, but all structs are typeless.

### Omit the types, provide a schema
Eg json with json schema
https://en.wikipedia.org/wiki/JSON#Metadata_and_schema

Provide an additional schema to declare the types.
Not too sure how this works in practise - havn't ever used json-schema - so would have to investigate.


### Use additional structure to store types (and metadata)

Another option would be for the client to receive something like this:

```
[name]:
	type: Typename as specified by silver-data
	value: single or multiple
```
This might mean extra layers to traverse to get to your data, eg something like

```
	person.value.name.value
```
This could have to be an optional variant to omitting the types.
I would see it useful in cases where metadata needs to be present, but client language naming is restrictive.


### Add metadata using special names

Instead of having extra layers, use a special key permitted (but not commonly used) by the language to store types/metadata.

In Go I think the only non-alphabetic initial character allowed is `_`, so you could have something like these:

```
	customer1234:
		_type: Person
		name: Alice
		email: test@example.com

	customer1234:
		_meta:
			type: Person
			comment: foo
		name: Alice
		email: test@example.com

```

In some languages leading underscores have syntactic or conventional meanings such as `private`, so this won't always be the best choice - see https://en.wikipedia.org/wiki/Underscore#Programming_conventions


A dot `.` might be available as a first character in some languages:

```
	customer1234:
		.type: Person
		name: Alice
		email: test@example.com

	customer1234:
		.meta:
			type: Person
			comment: foo
		name: Alice
		email: test@example.com

```

Or as a key name itself (similar to Silver):

```
	customer1234:
		.:
			type: Person
			comment: foo
		name: Alice
		email: test@example.com
```

### Add type information to object metadata

I'm not sure about this one, but some languages may have built-in metadata that is mutable or can be added to.


### Use a preprocessor to generate type code
For statically typed languages use a pre-processor to create code that can create the types.
This would probably only work in situations where you still have a compile step.


### Use reflection or other metaprogramming techniques
Again, depends on language.


### Create types dynamically
I think this would be the best option, but really depends on language support.




