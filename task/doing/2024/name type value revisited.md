Name type value revisited
=========================

```
name : Type value
```

Need to briefly revisit this to settle upon some terminology.
(Not sure if I've cleared this up somewhere else.)


Values, Types, Expressions
--------------------------

In the lexer/parser I need specific names for the parts on the right hand side of the colon.

I'm not sure which of these groupings makes the most sense:


	name: expression ( type? value? )

	name: value (type? expression?)


https://en.wikipedia.org/wiki/Expression_(computer_science)



I think these are statements:

	name: Type value
	name: Type
	name: value

And the right hand sides are expressions:

	Type value
	Type
	value

Where those expressions are composed of 1 or more sub-expressions:

	(Type expression)? (value expression)?

So essentially everything on the right is composed of expressions that yield either types or values


Are types values?
-----------------

At one point in the past I had sort of concluded that types *are*  values, so I want to clear up that terminology.

I either need to expand the idea of values to include types, or exclude types from values

So either expressions yield values, and values are type values or ordinary values:

	expressions{
		values{
			| type values
			| type inhabitant (ordinary) values
		}
	}

Or, I separate them into type-expressions and value-expressions:

	type-expressions{
		types
	}

	value-expressions{
		values
	}

The second looks better at this stage.



Possible Complications?
-----------------------

Some reason why it might be nice to think of types as values:

* They can be expressed/manipulated in ordinary silver-data syntax
* They can be returned by functions
* They're on the right hand side of an assignment
* They can include ordinary values (eg array length)







Refs
----
https://cs.stackexchange.com/questions/151231/what-is-the-difference-between-type-inhabitant-and-subtyping







According to wikipedia an expression yields a value, so



