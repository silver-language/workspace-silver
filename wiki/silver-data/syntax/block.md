Blocks
======


Blocks are denoted with indentation using tabs:

```js
product1:
	name:	`cat food`
	price:	$4.99

product2:
	name:	`cornflakes`
	price: 	$9.99
```


Basic blocks can optionally be terminated with `end`, or `[blockname] end`:

```js
product1:
	name:	`cat food`
	price:	$4.99
end

product2:
	name:	`cat food`
	price:	$9.99
product2 end
```

Block ends are mandatory beyond 1 level deep:

```js

shoppingCart:

	product1:
		name:	`cat food`
		price:	$4.99

	product2:
		name:	`cornflakes`
		price:	$9.99

shoppingCart end
```



