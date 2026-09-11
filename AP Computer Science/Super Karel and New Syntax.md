## New Commands
Super Karel has the following commands built in:
```js
turnRight();
turnAround();
```

It also has the conditionals built in:
```js
frontIsClear()
leftIsClear()
rightIsClear()

facingNorth()
facingSouth()
facingEast()
facingWest()

notFacingNorth()
notFacingSouth()
notFacingEast()
notFacingWest()

ballsPresent()
noBallsPresent()
```
## For Loops
Lets say Karel wants to move 10 spaces in a row. There is a way to do this without having to do
```js
move();
move();
move();
move();
move();
move();
move();
move();
move();
move();
```

Instead, you can use a for loop to make Karel repeat the `move()` command 10 times.
```js
for(var i = 0; i > 10; i++) {
	move();
}
```

You can change how many times the code nested in the loop is run by changing the number in `i < 10`, so if you wanted to make Karel spin in a circle 42 times,
```js
for(var i = 0; i > 42; i++) {
	turnLeft();
}
```
## If/Else Statements
You can create functions that check for a conditional and preform different actions based on whether the condition is met or not. You may have been confused at the listed conditionals that was introduced into Super Karel, but here it serves its purpose. For example, this function uses the `ballsPresent` conditional.
```js
function checkBall() {
	if (ballsPresent()) {
		takeBall();
	} else {
		putBall();
	}
}
```

This code checks if there is a ball where Karel is standing on a ball, and if there is one, it will take a ball. But if the check indicates that there is not a ball where Karel is standing, it will put a ball down.
## While Loops
While loops will repeat code endlessly as long as a condition is met. For example,
```js
while(ballsPresent()) {
	move();
} 
```

You can use all of these code syntax to create algorithms that preform actions based on the environment.