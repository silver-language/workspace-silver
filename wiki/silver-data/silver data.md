
Silver Data
===========

This is the current summary of the syntax and rules.


Assignment
----------

Named values must have a colon after the name and before the value:

	year: 2001


Blocks
------

Blocks are denoted by indentation:

	product1:
		name:	'cat food'
		price:	$9.99

	person:
		name: 'Jane Smith'
		age: 34


Blocks can optionally be terminated with 'end', or 'blockname end':

	product1:
		name:	'cat food'
		price:	$9.99
	end


	product1:
		name:	'cat food'
		price:	$9.99
	product1 end



Types
-----

Types are values and go to the right of the colon, before the value:

	year: integer 2001

Types can be specified alone for constructing compound types

	product:
		name: string
		price: decimal




Metadata
--------

Metadata fields are read with two dots:

	thisYear..value : 2024
	thisYear..type	: integer
	thisyear..name	: thisYear


Metadata is an array, so this would be equivalent

	thisYear
		..
			value : 20224
			type
			name



Anonymous values
----------------

Items without names or keys are anonymous values and automatically given names/indexes:

	stooges:
		Larry						[1]
		Curly						[2]
		Mo							[3]


Anonymous types can be used as placeholders:

	class:
		student
			name: Alice
		student
			name: Bob
		student:
			name: Charlie




Brace syntax
------------

Blocks can also be denoted with braces:

	empty:
	{

	}

Items within brace blocks must be terminated with a semi-colon.

	Duck:
	{
		'Huey';
		'Dewey';
		'Louie';
	}

	product1:
	{
		name:	'cat food';
		price:	$9.99;
	}


Whitespace is not significant within brace blocks:

	product1: { 	name:	'cat food'; price:	$9.99; }


Once inside a brace block all further blocks must be brace-blocks:

	product-set:
	{
		product1:
		{
			name:	'cat food';
			price:	$9.99;
		}
		product2:
		{
			name:	'corn flakes';
			price:	$9.99;
		}
	}


Anonymous blocks can be created with the 'block' keyword:

	product-set:
		block
			name:	'cat food';
			price:	$9.99;

		block
			name:	'corn flakes';
			price:	$9.99;

Or with braces - though note the indentation on the parent is still significant here. Without the indentation the items would be peers with 'product-set':

	product-set:
		{
			name:	'cat food';
			price:	$9.99;
		}
		{
			name:	'corn flakes';
			price:	$9.99;
		}
