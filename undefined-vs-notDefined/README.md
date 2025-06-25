```js
var a = 7;

//js will try to allocate memory space to this 'a'
//even before a single line of code is executed

//when js allocates memory to the variables and fucntions
//for the 'variables' it tries to put a placeholder
//it like a placeholder that is placed in the memory
//that placeholder or special keyword is 'undefined'

console.log(x)//now this something we have not allocated memory to
//and we are trying to access it
//since no memory is allocated for 'x' in the memory space
//it will result 'x is not defined' as it's not there in the program
//and no memory was allocated in the memory creation phase while creating the execution context.
//so 'not defined' is something whcih has not been allocated memory
```
```
So, undefined is not equal to empty.
Like it is not taking some memory or somethig.
NO. It is a special keywoed it takes up it's own memory.
But we can assume it to be a placeholder which is kept for the time being utill the variable is assigned some other value.
Till that point it will store this placeholder known as 'undefined'.
```
```js
//now let's say we never put any value to a variable
var a;//just initialization, not value assigned

console.log(a);

//so, throughout the whole program the placeholder 'undefined' will be kept inside 'a'.
```

- Js is a loosely typed language.
- Means it does not attches it's variables to any specific data type.
- Suppose we have created a = 'bob'(string) later on we can put a = 10(number).

```js
a = undefined//should try to avoid this though it's okay, 
//but it can lead to inconsistency.
//bacause what undefined means
//it states that in the whole code
//that variable was not assigned anything or any value