Comparison operators:
```js
>= equal or greater than
<= equal or less then
>  greater than
<  less than
== equal to
!= not equal to
```

Example: This program determines if you have 25 points or a value or more across all variables to determine the `isAllStar` variable.

```js
function start(){
	var points = 18;
	var rebounds = 10;
	var assists = 12;
	var isAllStar = 
	    points == 25 || 
	        points >= 10 && 
	        rebounds >= 10 && 
	        assists >= 10;
	println("Is all star? = " + isAllStar);
}

CONSOLE
──────────────────────
Is all star? = True
```
