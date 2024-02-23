Brace Syntax
============



Brace (alterntate) syntax
-------------------------
Matching the above examples

name: value
name:
{
	value
}


name
{
	value1
	value2
	value3
}


name
{
	name: value
	name: value
	name: value
}


name
{
	name
	{
		value
	}
	name
	{
		value
	}
	name
	{
		value
	}
}


name
{
	name1
	{
		value1
		value2
		value3
	}
	name2
	{
		value1
		value2
		value3
	}
	name3
	{
		value1
		value2
		value3
	}
}


linear structure
----------------
If you need to for brevity's sake put a few items into one line you can terminate with a semicolon.
Eg

	name: { n1: val1; n2: val2; }

	name:
		{ n1: val1; n2: val2; }

The braces in this case are mandatory - these wouldn't make very much sense:

	name: n1: val1; n2: val2;

	name:
		n1: val1; n2: val2;
