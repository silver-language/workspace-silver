Brace Syntax
============
(experimental)



Blocks can also be denoted with braces:

	empty:
	{

	}

Items within brace blocks must be terminated with a semi-colon.

	Duck:
	{
		`Huey`;
		`Dewey`;
		`Louie`;
	}

	product1:
	{
		name:	`cat food`;
		price:	$9.99;
	}


Whitespace is not significant within brace blocks:

	product1: { 	name:	`cat food`; price:	$9.99; }


Once inside a brace block all further blocks must be brace-blocks:

	product-set:
	{
		product1:
		{
			name:	`cat food`;
			price:	$9.99;
		}
		product2:
		{
			name:	`corn flakes`;
			price:	$9.99;
		}
	}


Anonymous blocks can be created with the `block` keyword:

	product-set:
		block
			name:	`cat food`;
			price:	$9.99;

		block
			name:	`corn flakes`;
			price:	$9.99;

Or with braces - though note the indentation on the parent is still significant here. Without the indentation the items would be peers with `product-set`:

	product-set:
		{
			name:	`cat food`;
			price:	$9.99;
		}
		{
			name:	`corn flakes`;
			price:	$9.99;
		}



Types
-----

How could types work in brace syntax?

name : type value


name : type
	sub1: type1 value1
	sub2: type2 value2

name : type { sub1: type1 value1; sub2: type2 value2; }
