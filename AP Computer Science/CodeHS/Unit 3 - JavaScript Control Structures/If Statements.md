>[!WARNING] NOTE
>Review [[Super Karel and New Syntax#If/Else Statements]] if you are unfamiliar with this.

Example
```js
function start(){
    var age = readInt("What is your age? ");
    if(age >= 13 && age <=19) {
        println("Yes, you are a teenager.");
    }else{
        println("No, you are not a teenager.");
    };
}

CONSOLE
──────────────────────
What is your age? [INPUT: 12]
No, you are not a teenager.
// RERUN
What is your age? [INPUT: 17]
Yes, you are a teenager.
```

## Else if
Figure it out lmao its simple
```js
function start(){
	var userWants = readLine("What meal do you want?");
	if(userWants == "breakfast") {
	    println("you should eat something that is not from adams");
	}else if(userWants == "lunch") {
	    println("you should eat something that is not from lasalle");
	}else if(userWants = "dinner") {
	    println("food, i guess?");
	}
}

CONSOLE
──────────────────────
What meal do you want? [INPUT: dinner]
food, i guess?
// RERUN
What meal do you want? [INPUT: lunch]
you should eat something that is not from lasalle
```
