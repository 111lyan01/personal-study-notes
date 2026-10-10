There are some of the logical operators in JavaScript:
```js
var this = true;
var that = false;
// AND operator. [and] is true if [this] and [that] are true
var and = this && that;
// OR operator. [or] is true if either [this] or [that] is true
var or = this || that;
// NOT operator. [not] is true if [this] is equal to not the value of [that]
var not = this =! that
println(this)
println(that)
println(and)
println(or)
println(not)

CONSOLE
──────────────────────
true
false
false
true
true
```

Here's an example:
```js
function start(){
	var reqAge = readBoolean("Are you at least thirty five years old?");
	var isUSCitizen = readBoolean("Are you a US Citizen?");
	var canBePresident = reqAge && isUSCitizen;
	println("Can be president: " + canBePresident);
}

CONSOLE
──────────────────────
Are you at least thirty five years old? [USER INPUTTED: True]
Are you a US Citizen? [USER INPUTTED: True]
Can be president: True

CONSOLE (alt)
──────────────────────
Are you at least thirty five years old? [USER INPUTTED: False]
Are you a US Citizen? [USER INPUTTED: True]
Can be president: False
```

