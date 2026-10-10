## Adding a constant
To put a constant variable, you define a variable outside the start function and put in SNAKE_CASE style. You can use this as a fixed number to apply to other variables. For example, this program will convert whatever the user puts in miles to kilometers.

```js
CODE
──────────────────────
MILES_TO_KM = 1.60934
function start() {
	var miles = readInt("how many miles did you travel?")
	var kilometers = miles * MILES_TO_KILOMETERS
	println("You ran " + kilometers + "km!")
}

CONSOLE
──────────────────────
how many miles did you travel? [user inputted: 4]
You ran 6.43736km!
```

## Basic Math Operators
You can use `+ - * /` to use addition, subtraction, multiplication, and division.
```js
CODE
──────────────────────
var a = 5
var b = 10
var c = a + b
var d = c / 5
var e = d * b
println(c)
println(d)
println(e)

CONSOLE
──────────────────────
15
3
30
```
