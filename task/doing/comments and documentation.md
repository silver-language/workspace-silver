Comments and Documentation
==========================

My long discussion piece (still working on) 

	wiki/project/goals/comments and documentation.md

is starting to bring into focus the need for different kinds of comments/descriptions/documentation for different purposes.

### True comments (eg ignore this chunk) 

Should be temporary, and probably culled at certain boundaries like merge, eg they don't live longer than a branch.
Could possibly be a feature that must be switched on/managed to discourage/limit their use.

I still have no idea what they should look like.

### Documentation/description comments 

Can live in the code, or elsewhere with references to code in question.

### Transient/change of state/task comments 

I'm still not sure about. If it's *very* important it can live in code, otherwise move out with references


Metadata
--------

In some cases some of these should be first-class, other times it might be possible to use metadata, eg:


	brokenJob: Function
		..task: TSK123
		..description:
			This function takes some text and transforms it into other text
		parameter: 
			input: Text
		type: Text
		...dostuff...
		result: output
	brokenJob end

That could signal to the dev there are relevent outstanding tasks here. 
These could maybe be auto-generated/validated.

One advantage of using metadata in this way is it doesn't clutter the primary namespace of your structure, eg in the above, 'task' and 'description' are still available.
There are probably downsides though.

