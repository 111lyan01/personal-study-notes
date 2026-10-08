Variables can assign a integer, float, string, or boolean value to an object.

```js
CODE
──────────────────────
var grapes = 10;
var apples = 5;
println("grapes = " + grapes);
println("apples = " + apples);
apples = 12;
println("apples =" + apples);
println(apples + grapes);

CONSOLE
──────────────────────
grapes = 10
apples = 5
apples = 12
17
```

You can call a variable to change its assigned value, and you can add/subtract and apply math operations to a variable:

```js
CODE
──────────────────────
var numExample = 3;
println("numExample: " + numExample);
numExample = numExample + 1;
println("numExample + 1: " + numExample);
numExample = numExample * 3;
println("numExample * 3: " + numExample);
// A simpler way of applying math operations
numExample += 4
println("numExample + 4: " + numExample);
numExample /= 2
println("numExample / 2: " + numExample);
var reassignExample = 4;
println("reassignExample: " + reassignExample);
reassignExample = numExample
print("reassignExample assigned to numExample: " + reassignExample);

CONSOLE
──────────────────────
numExample: 3  
numExample + 1: 4  
numExample * 3: 12  
numExample + 4: 16  
numExample / 2: 8 
reassignExample: 4  
reassignExample assigned to numExample: 8
```
