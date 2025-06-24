### In this part let us explore how fucntions work in js and what is of role of variable environment here.

- ### For that let us create js proram

```js
var x = 1;//it is in the global space
a();
b();
console.log(x);

function a(){
    var x = 10;
    console.log(x);
}

function b(){
    var x = 100;
    console.log(x);
}

//here in this program we have same variable name
//to explore how variable environment work and access
//value from local memory space which is limited to
//the associated execution context only
```
```
Now, the output of the above code snippet will be:
10
100
1
And why is it like that let us go through on that
```

- As soon as we run the upper js program:
    - A Global Execution Context is created and that GEC will be pushed into the call stack.
    - The execution context will be created in two phases.
    - In the first phase (memory creation) memory will be allocated to all the variables and functions.
    - Variables will have a special value 'undefined' and for the functions the whole copy of the function will be stored.
    - Now, when a function is invoked a new seperate execution context is created and the it is also pushed into the call stack with it's own memory and code component.
    - The console inside each function will print their respective variable by accessing them from their local memory space. Js engine will search for 'x' inside the local memory. It means they will access variable from their respective execution context's variable environment or code component.
    - So, same variable name will not conflict because they are limited to their own execution context or local memory space.
- That is how every single execution context maintain it's own seperate space. Even if that execution context is created by a function or it is the global execution context or any other execution context they will have their own memory space, they will have their own virtual kind of an environment where they are running seperately, independent of each other.