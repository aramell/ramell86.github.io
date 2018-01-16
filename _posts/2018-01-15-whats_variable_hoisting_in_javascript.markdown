---
layout: post
title:      "What's variable hoisting in JavaScript?"
date:       2018-01-16 02:28:57 +0000
permalink:  whats_variable_hoisting_in_javascript
---

Good question.  Most other language do not have this so its important to learn this type of behavior otherwise it can throw your for hours of debugging.  From an high level or overview this means that variable might be available before they are actually declared.  A lof of this has to do with how they are declared.

Using the `var` variable declartion treats the variable as if it was declared at the top of the functions scope or the global scope if its outside of a function.  Best to show an example:

```
function testFunction(){
   console.log(test)
   var test = "this is a test"
}
```


This will result in `testFunction` returning `undefined`.  Javascript works by hoisting these `var` variable declarations to the top of their respective scopes.  One thing that confused me is that it returned `undefined` and not the actual value.  Javascript only hoists the actual variable declation  `var test`, not the variable declaration **and its value**.  Once you realize that part of it, it makes sense that its returning undefined and not an error.  

On the other hand using the newer ES6 style `let` variable declaration limits the variable's scope to only that functions scope.

```
function testFunction(){
   let test = "this is a test"
	 console.log(test)
}
```

Hoisting in this new `testFunction` does not happen using the `let` variable declaration and in turn results in a `ReferenceError: test is not defined`.  

So best practice is to help keep things readable and limit the chance for errors its best to use the `let` declaration and declare the variables at the top of each function.
