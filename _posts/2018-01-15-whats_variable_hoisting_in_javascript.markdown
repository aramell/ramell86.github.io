---
layout: post
title:      "What's variable hoisting in JavaScript?"
date:       2018-01-15 21:28:57 -0500
permalink:  whats_variable_hoisting_in_javascript
---

Good question.  Most other programming languages do not have this type of "feature" so its important to why its different for JavaScript.  Otherwise you could be dubbing for hours trying to find this.  From an high level, hoisting means that a variable might be available before it is are actually declared in the traditional `var a = "new variable` way.  A lof of this has to do with how and where the variable is declared.

Using the `var` variable declartion treats the variable as if it was declared at the top of the functions scope or the global scope if its outside of a function.  Best to show an example:

```
function testFunction(){
   console.log(test)
   var test = "this is a test"
}
```


This will result in `testFunction` returning `undefined`.  Javascript works by hoisting this `var` variable declaration to the top of their respective scopes.  One thing that confused me early on is that it returned `undefined` and not the actual value.  Javascript only hoists the actual variable declaration  `var test`, not the variable declaration **and its value/definition**.  Once you realize that part of it, it makes sense that its returning undefined and not an error.  

On the other hand using the newer ES6 style `let` variable declaration limits the variable's scope to only that functions scope.

```
function testFunction(){
   let test = "this is a test"
	 console.log(test)
}
```

Hoisting in this new `testFunction` does not happen using the `let` variable declaration and in turn results in a `ReferenceError: test is not defined`.  

So best practice is to help keep things readable and limit the chance for errors its best to use the `let` declaration and declare the variables at the top of each function.
