---
layout: post
title:      "Understanding JavaScript Scopes using Identifiers "
date:       2020-02-26 00:03:34 +0000
permalink:  understanding_javascript_scopes_using_identifiers
---


Let’s look at this code together, can you guess what the outcome will be? 
```
function canYouScopeCorrectly() {
  var a = "Outer "; 
  let b = "Outer"; 
  const c = "Outer";
  d = "Outer";   
	
  if (true) {
    var a = "Inner ";
    let b = "Inner";
    const c = "Inner";
    d = "Inner";
  }
	
  // what will each statement log to the console?
  console.log(a);  // ? scope
  console.log(b);  // ? scope
  console.log(c);  // ? scope
  console.log(d);  // ? scope
}
```

Before we look at the answer let’s talk about the identifiers ( var, let, const & global). 





- When '**var**' is declared, we use it as a malleable identifier, it can be changed depending on what scope it is in. It is not very strong; it can be convinced about what value to hold in itself. Declaring 'var' is like saying: "this is my opinion, but I might change my mind later depending on what I see". So, if we want to stay true to a believe, 'var' is not a declaration we want to make. 
However, it does not mean it cannot be useful, it has better positioning when it comes to testing answers and console logging answers.
Take away: we know 'var' will change its mind as it sees new information. 


```
var number;

number = 2
console.log(number)
-> 2

number = 3
console.log(number)
-> 3

```



- '**Let**' identifier is a little stronger than 'var', it can recognize its surrounding and its block. It knows where stands. This means that it can stay in one place and not absorb information we don’t want it to by accident like 'var'. However, in our console we can give it a new value. That is okay, we are having a conversation and we need convince 'let' to hold this new information. That is better.

```
let number;

number = 1
console.log(number)
-> 1

number = 2
console.log(number)
->2
```



- **'const**'  identifier is taking it a step further than 'let'. 'const' is short for constant. We can infer that the information won’t change either, and it also knows about it place in a scope, it also knows where it stands.

```
const number = 1
VM1531:1 Uncaught SyntaxError: Identifier 'number' has already been declared
    at <anonymous>:1:1
```
'const' even knew that already used 'number' as a variable with the 'let' identifier, how cool is that?  We can see that 'const' is also a little bit smarter, sometimes we need that. 

```
const logic = 1 

console.log(logic)
-> 1

logic = 2
VM2061:1 Uncaught TypeError: Assignment to constant variable.
    at <anonymous>:1:7

const logic = 2;
VM1948:1 Uncaught SyntaxError: Identifier 'logic' has already been declared
    at <anonymous>:1:1
```



- '**Global**' identifiers are not used often but for this example we need to discuss their power. Declaring something globally is like screaming at the top of your lungs so everyone can hear you, and yes, everyone did hear you. 'global' was also heard in the 'inner' scope, so just like our 'var' identifier, it can be manipulated. Sometimes we don’t need to yell to get our point across, work smart not hard, therefore 'let' and 'const', they are your best friends in JavaScript




So, what is the answer of our first function? let’s find out!
```
canYouScopeCorrectly();

 // what will each statement log to the console?
  console.log('var', a);  // ? scope
  console.log('let', b);  // ? scope
  console.log('const', c);  // ? scope
  console.log('global', d);  // ? scope


-> var Inner 
-> let  Outer
-> const Outer
-> global Inner




```




```



// lets take a look again
// what will each statement log to the console?

function canYouScopeCorrectly() {
  var a = "Outer "; 
  let b = "Outer"; 
  const c = "Outer";
  d = "Outer";   
	
  if (true) {
    var a = "Inner ";
    let b = "Inner";
        console.log('let (inside)', b);  // ? scope <-
    const c = "Inner";
		    console.log('const (inside)' , c);  // ? scope <-
    d = "Inner";
  }
	
	
  console.log('var', a);  // ? scope <-
  console.log('let (outside)', b);  // ? scope <-
  console.log('const (outside)', c);  // ? scope <-
  console.log('global', d);  // ? scope <-
}



-> let (inside) Inner               
-> const (inside) Inner
-> var Inner 
-> let (outside) Outer
-> const (outside) Outer
-> global Inner


```
