# Const

## Overview

In this lesson, you will get to know ES2015's const keyword.

## Objectives

1. Learn the syntax for declaring constants.
2. Understand when to use constants.
3. Understand the differences between declaring constants and declaring using let and var.
4. Understand naming conventions for constants.

<!-- iframe of video lecture goes here -->

*Note: The code examples from this lesson can be run by pasting them into [Babel's online REPL](https://babeljs.io/repl/)*

## Declaring Contants

In order to create read-only variables (or constants) we use the const keyword. It is a good idea to use constants for values that will not change their value throughout your application. For example `var age = 7;` is indicating a value age that is something that in real life can increase. Each time we have a birthday our age increases. It is likely that in use within our application the same will be true. It is for these reasons that var or let keywprds are appropriate to declare such a variable. Let's look a different type of value. How about a specific age that defines when a user is a legal adult. This is reffered to as "the age of majority" in common law. In most places in The United States for example the age of majority is at 18 years old. In use in an application this represents a value that will most likely remain the same. We can declare a constant for this value using `const AGE_OF_MAJORITY = 18;`. Notice that we used all uppercase characters to declare out constant. This is a convention so that when other developers read our code they will know that we intended AGE_OF_MAJORITY to be read only and never change. Let's try to set a new value and see what happens:  
```javascript
const AGE_OF_MAJORITY = 18;
AGE_OF_MAJORITY = 19;  // Change not accepted!
console.log(AGE_OF_MAJORITY); // 18
```  
You can see that all attempts to set a new value for our constant do not work. It will always hold the first value when we declared it using the const keyword.

In fact, trying to redeclare a constant within the same code block will throw the following error:  
```javascript
const AGE_OF_MAJORITY = 18;
const AGE_OF_MAJORITY = 21; // Uncaught TypeError: Identifier 'AGE_OF_MAJORITY' has already been declared.
```

Additonally it is worth noting that constants must be assigned a value when they are declared otherwise they will forever hodl the value of undefined. Example:  
```javascript
const MIN_HEIGHT;
MIN_HEIGHT = 1;
console.log(MIN_HEIGHT); // undefined
```
So you see, we must always assign a value the first time we declare a constant:  
```javascript
const MIN_HEIGHT = 1;
console.log(MIN_HEIGHT); // 1
```

### Scope

Variables declared using the const keyword carry the same block scope as the let keyword. This means it is accessable only between the `{}` curley braces that it is defined within. See the lesson on Let keyword for more details on declaration scope.

### Best Practices

Let's take a look at the following code example, so we mihght better understand when using constants will make our code more readable and maintainable:  
```javascript
function advice(age) {
  if (age > 18) {
    var suggestion = "Hope your saving for retirement...";
    console.log(suggestion); //Hope your saving for retirement...
  } else {
    var praise = "Happy birthday kid!";
    console.log(praise); //Happy birthday kid!
  }
}

advice(19);
```  
Inside the advice function we check if they age that is passed into the function is greater than eighteen. Here we might not know exactly what 18 represents or what we are trying to determine for sure in the if condition. It would make our code even clearer that 18 actually represents the "age of majority" or common law age where a person is legally an adult and no longer considered a child. Let's refactor our code by using a constant in the condition instead:  
```javascript
function advice(age) {
  const AGE_OF_MAJORITY = 18;

  if (age > AGE_OF_MAJORITY) {
    var suggestion = "Hope your saving for retirement...";
    console.log(suggestion); //Hope your saving for retirement...
  } else {
    var praise = "Happy birthday kid!";
    console.log(praise); //Happy birthday kid!
  }
}

advice(19);
```  
This new code is written so that it is clear that we are checking if the age passed into the function is more than the age of majority (legal age of and adult). Now we will sleep comfortable at night knowing that others who read our code will have a clear idea of what we intended.

## Summary

1. You can create constants like this `const MAX_AGE = 18;`.
2. You should use constants to represent variables that should be read only.
3. It is a best practice to uppcase your constant names like this `const PI = 3.14;`.
4. A constants value can not be changed after it has been declared.
5. Constants carry block scope the same as the let keyword.

## Resources

- [MDN - JavaScript - Const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)
- [ES5 to ES6 Feature Comparison](http://es6-features.org/)
