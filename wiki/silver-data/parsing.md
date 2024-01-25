
Parsing
=======

While there are still a few design decisions left to iron out, here's the start of some parsing ideas.


Algorithm sketch
----------------
One big loop over file lines:


start

	contextIndent = 0


	filemap:
	{
		line...
		{
			number			// line number in file
			text			// raw text of line
			indent			// tab count
			data			// text minus indent
			block			// pointer to datastructure
		}
	}


	datastruct:		// where we're constructing the datamap
	{
		...$blockname...
		{
			(block | value

			)
		}

	}


	for line
	{
		if not empty
		{
			lineIndent = consume tabs before text
			text = text after indent

			match (lineIndent - contextIndent)
			0:
				comment: same level as the context, continue adding to it
			1:
				comment: we're in one from the context, a new scope is starting
			>1:
				comment: this is an error, cannot do
			-1:
				comment: close the current context and returning to the parent
			-x:
				comment: close the current context and return x levels above

		}
	}
end









File datastructure
-------------------

file map structures

	package

		directory

			filename
				line
					indent
					assignment -> instruction or block
				line
				line



Data datastructure
------------------

During processing - this might become the 'private' datastructure:

	block
		source -> file.line.char
		assignment
			sequence number
				source -> file.line.char



After processing the 'public' datastructure:

	block
		assignment
		...



Langauge datastructure
----------------------

	block
		source -> file.line.char
		assignment
			sequence number
				source -> file.line.char



