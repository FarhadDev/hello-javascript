# Hoisting in Javascript

```javascript
var x = 7;

function getName() {
    console.log("Hello JavaScript");
}

getName();
console.log(x);
```
```
Output of the above code is: 
Hello Javascript
7
```

```javascript
//now let just move the following two line on the top of the program
// getName();
// console.log(x);

getName();
console.log(x);

var x = 7;

function getName() {
    console.log("Hello JavaScript");
}

//now what we expect to see here. 
//here what changed is we are trying to access getName() even before we have initialized it.
//we are trying to access 'x' even before we put some value in it.
//in most of the programming language the upper code will through an error. we can not access variables and functions before initializing them.
```
```
So, now what will be the output of the above code:
It is:
Hello Javascript
undefined
```
```javascript
//now let's just remove the initialization of variable 'x'

getName();
console.log(x);


function getName() {
    console.log("Hello JavaScript");
}
```
```
Now the output will be:
Hello Javascript
Uncaught ReferenceError: x is not defined

In previous case the value of 'x' was printed undefined and now it is saying 'x' is not defined.

What the heck is going on. Isn't undefined and not defined the samw thing? NO it's not.
```

### Now these all intersting things in javascript is known as "Hoisting".

## Hoisting is a phenomena in javascript by which we can access variables and functions even before we have initialized it or we put some value in them. We can access them without any error.

```javascript
//so wherever this 
var x = 7;
//there in the program it does not matter we can just access it anywhere in the program. 
```

### Now let's see one more interesting thing

```javascript
//getName();
//console.log(x);

var x = 7;

function getName() {
    console.log("Hello JavaScript");
}

console.log(getName);
//here we are not invoking the function, we just log the getName method.
```
```
It will print the function itself:
f getName(){
    console.log("Hello Javascript");
}
```
```js
//but what if we try to access
console.log(getName);
//even before we initializing the function.
var x = 7;

function getName() {
    console.log("Hello JavaScript");
}

//now what will we get for get name
//what should we get: undefined????
//let's see
```
```
It again gives us the function or prints the function:
f getName(){
    console.log("Hello Javascript");
}

So, in case of 'x' it was giving us undefined when we didn't initialize but in case of getName method it is printing that function.

Looks weired right. Now let's see how things works behind the scene.
```

- ### Now can we remember
    - Wherver we run a javascript program a execution context is created.
    - And it is created in two phases and the first phase is memory creation phase.
    - So, the answer lies there only and the whole concepts lies there only.

```js
var x = 7;

function getName() {
    console.log("Hello JavaScript");
}

getName();
console.log(x);
console.log(getName);
```
```
Even before the whole code start executing the memory is allocated for each and every variables and functions.
```
```js
getName();
console.log(x);
console.log(getName);

var x = 7;

function getName() {
    console.log("Hello JavaScript");
}

//if we remove the var x = 7 form this code js that means we have not reseved the memory for 'x' we have just reserved the memory for getName.
//that is why 'removing x' will result ReferenceError: x is not defined.
//if 'x' is there and we try to access before intialize it will result undefined as phase one mechanism of execution context.
```
### Now let's see another intersting thing

```js
getName();
console.log(x);
console.log(getName);

var x = 7;

var getName = () => {
    console.log("Hello JavaScript");
}

//now we have getName as the arrow function.
// now what will be the output????

```
```
The output for using getName as the arrow function will be:
Ucaught TypeError: getName is not a function --> when invoking the function in first line of the program.
When the getName is an arrow function it behaves just like another variable. Now the getName does not behave like a function.
In the memory allocation phase of the execution context just like it allocates undefined to 'x' it will also allocate 'undefined' for 'getName' when it is written as an arrow function.
```

### There is another way of declaring a function

```js
var getName = function () {
    console.log("Hello Javascript");
}

//in this case also like the arrow function getName will behave just like a variable.
//only in the case of proper function decletaion it will copy the whole function in the memory space.
```





