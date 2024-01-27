
Silver-data reader for foreign language
=========================================


I'm going to take a little diversion here and sketch out what a silver-data reader/writer might look like for different language.
This might help me figure out what should go into the actual silver-data/silver-core.

The example we'll take is data transport between a native silver system and a system written in a different language (java, c#, python, rust, go etc).
The transport will use silver-data.

Some different cases:
* Both parties can collaborate on the data exchange
* Foreign-language client attempts to consume a native silver-data source
* Native silver client attempts to consume a service written in a foreign language, but presented as silver-data

And maybe:

* A native silver client attempts to consume a service presented in another data format




Foreign language client consuming a silver-data source
------------------------------------------------------
Going with this one first as it cuts to the meat of the problem.

A foreign language reader needs

* To parse the data into trees/strings
* To use types/schemas presented by the service as hints for mapping into their own native datatypes

A small piece of silver-data with inline types might look like:

	student1: person
		name: string Alice
		birthday: date 1991-01-09
		course: string medicine

The schema for person might look like:

	person: array
		name: string
		birthday: date
		course: string

So you could send this response:

	schema:
		person: array
			name: string
			birthday: date
			course: string
		data: array of student

	data:
		student1: person
			name: Alice
			birthday: 1991-01-09
			course: medicine


(I haven't yet decided how to write collection-of-thing, but that will do for now.)
