
Silver Data
===========

Lots of the documents in this folder are where i'm figuring out the ideas.
In this document I'll keep the current summary of the rules.





Named values must have a colon after the name and before the value:

	year: 2000



Blocks are denoted by indentation:

	product1:
		name:	'cat food'
		price:	$9.99

	person:
		name: 'Jane Smith'
		age: 34


Items without names or keys are anonymous and automatically given names/indexes:


	Stooges:
		Larry						[1]
		Curly						[2]
		Mo							[3]


Blocks can optionally be terminated with 'end', or 'blockname end':

	product1:
		name:	'cat food'
		price:	$9.99
	end


	product1:
		name:	'cat food'
		price:	$9.99
	product1 end




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


