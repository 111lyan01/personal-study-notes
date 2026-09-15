## Basic Syntax
Karel has the following commands available. Use two forward slashes to create a comment for that line or a forward slash followed by an asterisk for multi line comments.
```js
move();
takeBall();
putBall();
turnLeft();

// a basic comment
// another line comment
/* multi line comment
   running the program will
   ignore everything written here */

```
## Functions
Functions can clean up code and help shorten repeated code. Here is a function that lets Karel turn right.
```js
function turnRight() {
	turnLeft();
	turnLeft();
	turnLeft();
}
```

This function can now be called by simply invoking it like a normal command.
```js
turnRight();
```

Functions can be used inside other functions too. For example, this function also uses the `turnRight()` function that was defined earlier. It also uses another defined function called `move3()` to move three times.
```js
function turnRight() {
	turnLeft();
	turnLeft();
	turnLeft();
}

function move3() {
	move();
	move();
	move();
}

function turnRightAndMove() {
	move3();
	turnRight();
}
```

The start function is a function that (pretty self-explanatory) runs on start of the program.
```js
function start() {
	move();
	turnLeft();
	// other code here...
}
```