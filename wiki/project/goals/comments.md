Comments
========

I'm generally in favour of comments.

But I understand the criticisms, and have to try to address them.


Why I like comments
-------------------

* they humanise code
* they explain patterns and techniques that might not be obvious to readers
* they explain things have been tried and failed, and why this works (zero results)
* they can form documentation (what/how)
* they can indicate intention, even if the code does not do what it says (is/ought)
* they can indicate flaws/problems that are known to be present


What I don't like in comments
-----------------------------

A lot of the usual suspects, like stating the plainly obvious.

### Functional comments

This irks me quite a bit.
Things like:

* javadoc
* some HTML/XML comments, eg headers
* metadata in comments
* other kinds of decorators

There should be nothing functional in true comments.
Anything functional should be in the code proper.





References
----------


Comments could form a reference manual:
	https://ask.slashdot.org/comments.pl?sid=17117546&cid=60475596




### Rob Pike - Notes on Programming in C - February 21, 1989

http://doc.cat-v.org/bell_labs/pikestyle	#Comments


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
