## Basic Syntax
Karel has the following commands available
```js
move();
takeBall();
putBall();
turnLeft();
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

