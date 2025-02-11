Comments and Documentation
==========================

I'm generally in favour of comments.

But I understand the criticisms, and have to try to address them.


Why I like comments
-------------------

They (can):

* humanise code
* explain patterns and techniques that might not be obvious to readers
* explain things that have been tried and failed, and why this works (zero results)
* can form documentation (what/how)
* indicate intention, even if the code does not do what it says (is/ought)
* indicate flaws/problems that are known to be present
* indicate where patterns are broken deliberately (eg DRY)
* indicate sources of code (third parties etc)
* indicate code of a temporary nature
* reduce gatekeeping (you have to be smart enough etc)

These all presume a certain level of quality to the comments.

I'm rather intrigued by Jupyter notebooks (though admittedly don't know much about them) in that they mix code and document, which from a certain perspective could be seen as comments.


Standard criticisms of comments
-------------------------------

They (can):

* be superfluous / state the obvious
* be incorrect/misleading/out of date (comments lie/get bugs)
* stand-in for poorly written code, when the code could be wrtten more clearly
* add refactoring burden
* commented out leftover code
* use as visual markers
* add visual clutter

I agree with most of these to a degree, except perhaps the last.
I'm guilty of all though.


Don't Write Comments | CodeAesthetic
https://www.youtube.com/watch?v=Bf7vDBBOBUA

	There's something like an inverse no true scotsman or a shifting goalposts here - if comments are good then they are documentation


Code Like a Pro : Comments | How to Write Code Professionally (With Code Examples)
https://www.youtube.com/watch?v=ZpFwlwt7PNo



### “Good code is self-documenting.”

That's such bullshit.


If Code Is Self-Documenting, Why Do Comments Exist?
https://www.youtube.com/watch?v=1NEa-OcsTow




What I don't like in comments
-----------------------------

A lot of the usual suspects, like stating the plainly obvious.

### Functional comments

This irks me quite a bit.
Things like:

* Javadoc: https://en.wikipedia.org/wiki/Javadoc
* JSDoc: https://en.wikipedia.org/wiki/JSDoc
* some HTML/XML comments, eg headers
* metadata in comments
* other kinds of decorators

There should be nothing functional in true comments.
Anything functional should be in the code proper.

### Line padders in comments

Things like this:

	/* This is the style recommended by Holub for C and C++.
	 * It is demonstrated in ''Enough Rope'', in rule 29.
	 */

To me it looks unbalanced, and the intermediate stars are totally unnecessary.
Once the comment is opened, there should be no further commenty-syntax until the comment is closed, a-la:

	/*
		Don't do it like that
		Do it like this instead
	*/

That way the comment content is *only* the content


Speculative solutions
---------------------

### Comments become first class elements in the language

For example, go from this:

	i=i+1;           /* Add one to i */

to this:

	i=i+1;
	comment += 'Add one to i';

Or in silver

	i: i+1
	comment:
		this is totally superfluous comment
		but you get the idea


That way:
* Comments are readable/manipulable by the ordinary parser
* Coders are more inclined to treat comments seriously or as documentation
* Comments can have logic rules/type rules etc
* Can be pulled out to form documentation or a wiki etc.
* Certain kinds can be made mandatory/optional by the type system
* Documentation is always with you no matter where are you are (space, underwater etc)


### The state of the code should be enshrined in the code

This is about the change-over-time or transient nature of code.
Code evolves, bugs get introduced and fixed, requirements change etc.

If code changes then make change a first class citizen of the code.

Traditionally this is done with tools like bug/issue trackers.

There is value in those systems, but:

* They're usually completely different systems several steps away from the code.
* A bug could be fixed, but not updated in the issue tracker, or vice versa.
* Often there isn't a dependent relationship between them.

The solution to this is to move issue/task tracking into the code itself.

This could be as simple as something like:

	result: transform(input)
	issue: this transform takes into account x and y, but not z

Where the code is parsed looking for issues - some systems do this by looking for TODOs in comments.

But better still is to have a separate folder in the repo where all tasks/issues are tracked.

* If a bug exists in the code an issue exists in the task folder
* If a bug gets fixed the issue gets deleted or archived
* Code change boundaries - commits/merges - are synchronized with task changes
* Tasks also have types, schemas, logic etc and can be validated against the code, read, manipulated, pulled out to form reports, dependency graphs etc.
* The issue tracker is always with you no matter where are you are (space, underwater etc)




Comments Vs Documentation
-------------------------

> These all presume a certain level of quality to the comments.

> There's something like an inverse no true scotsman or a shifting goalposts here - if comments are good then they are documentation


Returning to my own statements.

At this point we're starting to argue semantics - I want comments to be good enough to form documentation, which makes them no longer comments? Are we just quibbling about words?

Most of the criticisms are about low value or redundant comments.
Most of the cases where people are in favour of comments are when they are high-value or necessary.

So with respect to turning comments, documentation and code-state into first class citizens I might need to come up with better terminlogy or a system.

* comments in metadata? is metadata mutable in the first place?
* have no element called 'comment' - force something else?
* have documentation elements? bit of a mouthful
* have no traditional 'hard' comments at all? Probably not - far too useful for debugging - could enforce rules for them though.








References
----------
https://en.wikipedia.org/wiki/Comment_(computer_programming)

https://stackoverflow.blog/2021/12/23/best-practices-for-writing-code-comments/

https://www.freecodecamp.org/news/code-comments-the-good-the-bad-and-the-ugly-be9cc65fbf83/

Comments could form a reference manual:
	https://ask.slashdot.org/comments.pl?sid=17117546&cid=60475596




### Rob Pike - Notes on Programming in C - February 21, 1989

http://doc.cat-v.org/bell_labs/pikestyle#Comments


	A delicate matter, requiring taste and judgement.  I tend to err on the side of eliminating comments, for several reasons.  First, if the code is clear, and uses good type names and variable names, it should explain itself.  Second, comments aren't checked by the compiler, so there is no guarantee they're right, especially after the code is modified.  A misleading comment can be very confusing.  Third, the issue of typography: comments clutter code.

	But I do comment sometimes.  Almost exclusively, I use them as an introduction to what follows.  Examples: explaining the use of global variables and types (the one thing I always comment in large programs); as an introduction to an unusual or critical procedure; or to mark off sections of a large computation.

	There is a famously bad comment style:

		i=i+1;           /* Add one to i */

	and there are worse ways to do it:

	/**********************************
	*                                 *
	*          Add one to i           *
	*                                 *
	**********************************/

				i=i+1;

	Don't laugh now, wait until you see it in real life.

	Avoid cute typography in comments, avoid big blocks of comments except perhaps before vital sections like the declaration of the central data structure (comments on data are usually much more helpful than on algorithms); basically, avoid comments.  If your code needs a comment to be understood, it would be better to rewrite it so it's easier to understand.
