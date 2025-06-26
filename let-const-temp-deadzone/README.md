### Do you know what is a temporal deadzone?
### Are let & const declarations hoisted?
### What is the difference between SyntaxError, ReferenceError and TypeError?

### We will cover all of these in this part.

- **Yes let & const declarations are Hoisted**
- But they are hoisted very diffrently than the 'var' declarations.
- So, saying let & const are not hoisted is not the right answer rather they are in the 'temopral deal zone' for the time being.

```js
console.log(b);//we can do this in js
//beacuse before start executing a single line of code
//js allocates memory to all it's variables and functions
//that is why we can access them even before initializing them
//in other language we won't be able to do this
//this is possible because of hoisting
let a = 10;
var b = 100;

//now peopele argue that if var b is hoisted and let a is also hoisted
//then we should also be able to access let a like the following 

console.log(a);

let a = 10;
var b = 100;

//but this gives us an error
//ReferenceError: Cannot access 'a' before initialization
//so, this errors tells us that we can only access 'a'
//only after after we have assigned or initialize some value to this variable 'a'
//so, if we log the variable after putting some value
//then we will be able to access it

let a = 10;
console.log(a);
var b = 100;

//but how to know
//whether this variable was hoisted or not
```
```
- Now let's see what happens when we run the code
- Even before executing a single line of code
- Js will allocates memory to all the variables and functions
- So, let a will be allocated memory
- And var b will be also allocated memory
- So, both of them are allocated memory
- This is what is hoisting!!!
- But there is a catch
- If we look carefully var b is allocated memory in the global scope and it is in the global scope
- Whether let a is not allocated memory in the global memory space and it is also not in the global scope
- Rather let a is allocated memory outside global memory space and it is in the other separate scope 'Script'
- We can not access this memory space
- We can not access this let and const declarations before we have putting some value in them.
- So, let and const are also hoisted but the thing is we can only access them only after their initialization.
- But even after initialization they remains in a separate memory space.
```
### Now let's talk about what is 'Temporal DeadZone'
- Temporal Dead Zone is the time since when this let variable was hoisted and till it is initialized some value
- That time between that is known a 'temporal dead zone'
```js
console.log(a);//a is hoisted and allocated memory space outside global 
//and also assigned 'undefined' placeholder
//'a' is in the temporal deadzone 
//as no value was initialized till now
//this is the phase known as tmp. dead zone

let a = 10;//we have initialized 'a' here
//temporal dead zone ends or finished
var b = 100;

//so that phase from hoisting
//till it's initialize with some value 
//get some value
//that phase is known as the tmp. dead zone
```
### *Whenever we try to access a variable inside a Temporal Dead Zone it gives us an ReferenceError** 
- can not access 'a' before initialization

```js 
line 3 --> let a = 10;
//so, anything before line 3 was the 
//temporal dead zone for 'a'
```
- Do we see this ReferenceError before
- If we try to access any random variable which is not there in our program

```js
console.log(x);//we never decalred 'x'
//output: ReferenceError: x is not defined
//when js engine tries to find the value of 'x'
//in the current scope it was unable to find it
//'x' was not there, no memory space for 'x'
//no reference of 'was' there
//so 'x' was nowhere defined
```
### Now let's see another interesting thing
```js
let a = 10;
console.log(a);
var b = 100;

window.b//output: 100
//as b is in the global scope
//which refers the globa object window
//var b is attached with the window object
//that is why we can access b through window

//but but, will 'a' be attached with window
//the answer is 'NO'
//because 'a' is in a separate storage or space
//that is reserved space for let and const
//that is not the global space
```

### So, till now what we observed is let is little strict than var.
### But there is one more level of strictness over here 'that is something we can not do redeclaration'

```js
let a = 10;
//now if we try to duplicate or 
//try to initialize let a again
//like the following
let a = 10;
//it will through an error
//this time it is a SyntaxError
//
//SyntaxError: Identifier 'a' has already-
//been declared
//no code will run even if
console.log('hello');
let a = 10;
let a = 10;
//js will just stop upfront
//it won't even execute a single line of code
//it does not even log
//it does not even reach a single line of code
//it's just up front says syntax error
//complete syntax error

//it is same for var also along with let
let a = 10;
var a = 10;
//we can not use the same name
//in the same scope
//to re-declare a variable

//but for var only
var a = 10;
var a = 1000;
//it is doable
```
### Now let's see what happens in case of const
```js
let a = 10;

const b = 1000;

//in case of const declaration
//it bhaves very much like let
//but there is difference
//it is even more strict than let

//it behaves the same way in hoisting
//it is stores in a separate memory space
//not is global, outside global space
//we can not access it before initialization
//it goes through the tmp. dead zone

//so what do we mean by more strict

//in case of let
//on the first place we can just declare
let a;
//and I can initailize it later
//anywhere in the program
a = 10;
console.log(a);
//it is totally fine

//but we can not do the same thing in case of const
const b;
b = 1000;
//if we try assign some value
//later in the program
//we can not do that
//we directly get SynataxError
//SyntaxError: Missing initializer in const declaration

//so, when we declare const b
//it expects we initialize it with some value
//in the same line

//Syntax error means code doesn't even run
//it just rejected up front
//like an invalid js code
```
### Now discover another type of error

```js
//if we try to do something like the following
const b =11000;

b = 343;
//we are trying to re assign some value
//in a const variable

//it gives us an TypeError
//TypeError: Assignment to constant variable
//so this is not a syntax error rather a type error
```
### Now let's see the difference between the syntax error, reference error and type error

- TypeError says that: Assignment to constant variable, so we are trying to assign any other value to a const variable.
    - why it is a type error. beacuse variable 'b' was type of const
- const b; do not initialize it. it will give a syntax error. beacuse here we have missing syntax. same for redeclaration of let a let a; there is some problem with the syntax of our code.
- And the reference error is something when js engine tries find a specific variable inside the memory space and we can not access it. like temporal dead zone. and not defined one. never placed in the memory.

### The best way of avoid temporal dead zone is to put our declaration and initialization on the top of the scope. So, as soon as our code stats executing/running it hits the initialization part at the first and then we go into the logic.

```
Variable initialization is the process of assigning an initial value to a variable when it is created, or declared, in a computer program. This ensures the variable starts with a known value rather than an unpredictable "garbage" value.
```
