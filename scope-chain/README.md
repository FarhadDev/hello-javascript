### Scope in javascript is directly related to lexical environment.

- If we understand **Lexical Environment** it will help us understanding scope, the scope chain and it will also help us to understand the closure also.

```js 
function a(){

}

var b = 10;
a();

//can we access 'b' inside the function a()
```

```js
function a (){
    console.log(b);
}

var b = 10;
a();

// when js engine reach "console.log(b);" this statement
//and it tries to execute console.log(b);
//what will js do
//js will try to find out whether 'b' esixts in the local memory space or not.
//when we say local memory space
//js engine will try to find this 'b'
//inside the local memory of this a()'s execution context
//function a's local memory will try to find out b
//and it won't be there
//because we never created 'b' inside a function
//now it will print???
//will it print undefined remember that special placeholder in case of hoisting
//will it print not defined like the b never existed
//will it just simply prints the value
//now if we runs this code Output: 10!!!!
//it prints up 10 that means this b can access the b which was outside of this function
```
- Now make it more interesting
```js
function a (){
    c();
    function c (){
        console.log(b);
    }
}

var b = 10;
a();

//now what will it print????
//output: 10; it can again access 10
//so that means even indide the function
//which is inside another function
//which is inside the global scope
//I can access b
```
- Now can we access b if we takes b inside the fuction a

```js
function a (){
    var b = 10;
    c();
    function c (){
        console.log(b);
    }
}

a();

//yes. it will also prints 10.
```
- But but can we access b outside of the function if declared or initialized inside the function like the following

```js
function a (){
    var b = 10;
    c();
    function c (){
        
    }
}

console.log(b);
a();

//now what will happen??
//it says b is not defined
```
- Here comes scope into picture
- **Scope means where we can access a specific variable or fucntion in our code**

- Now what is the scope of this variable b
- That means where can I access this variable b
- Other way of seeing scope is "Is b inside the scope"
- When we say is b inside the function c
- It means can I access b inside function c
- So, there is two way of look at scope
 - What is scope of variable b
 - Is b is inside the scope of a function

### As we told earlier scope is directly dependent on the lexical environment.

- Now let us see what is lexical environment with visual represenation.
- Whenever an execution context is created a lexical environment is also created.
- So, **lexical environment is the local memory along with the lexical environment of it's parent**.
- What is parent??? what is lexical???
- **Lexical as term means in HIERARCHY or in a sequence**
- c() is lexically sitting inside a()
- That is lexical 'in order - in hierarchy'
- In code terms we can assume it to be where that specific code is present physically - inside the code.
- c() physically presents inside the a()
- a() is lexically inside the global scope
- whenever this execution context is created we will get the reference to the lexical environment of it's parent.
- for c()'s execution context it will hold the reference of a()'s lexical environment
- global also has this reference to it's lex. env. ot it's parent at global level this reference to the outer environment points to NULL because it has no parent

### **So, scope chain is nothing but the cahin of all lexical environment and the parent references.**

### All the explanation will be more clear in the following figure:









