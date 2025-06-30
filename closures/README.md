### Let's just a see a basic example of closure

```js
function x(){
    var a = 7;
    function y(){
        console.log(a);
    }
    y();
}
x();//in browser Closure(scope) annotation

//Output: 7

//when y tries to run it tries to find a
//in it's local memory space
//if it does not find it
//then goes to it's lexical parent

//that is basically closure  
```

### Closure basically means that a function bind together with it's lexical environment. So, function along with it's lexica scope forms a closure.

### function y() was bind to the variables of x. So, it forms a closure and it has access to it's parent's lexical scope.

### MDN: A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (lexical environment). In other words, a closure gives you access to another function's scope from an inner function. In javascript, closures are created every time a function is created, at function creation time.

### Functions are the heart of javascript. We can literally assign function to a variable. Because in js function is first class citizen. We can pass a function in one function as a parameter. Most of the programming language don't allow this. Even we can return a function from another function.

```js
function x (){
    var a = 7;
    function y(){
        console.log(a);
    }
    return y;
}
var z = x();//js is synchronus, so after running this line 'x' is gone once it retuns 'y'.
//'x' is no longer in the call stack, 
//'x's execution context is no longer in the call stack

console.log(z);//Output: y(){console.log(a);}

//now what happens to this 'y' now.
//our 'z' contains 'y' now

//when 'y' inside of a fucntion we all know what happens
//we know all that lexical scope, 
//lexical binding, lexical reference, 
//parents and scope chain and everything

//but once the 'y' function has been returned outside
//it no longer resides 'x'
//now how will it behave in other lexical scope
//now this 'z' has the reference of 'y' contains 'y' in it
//how it will behave outside the scope

//.........
//so many line of code, at one point
//.......

//now we want to call the function z()

z();

//now, it will try to find variable 'a'
//but where is 'a'
//we are trying to execute 'z()' outside
//and 'a' is not there in the global scope
//and 'x' is gone it's no longer in the call stack
//what will it print when we invoke z

//****
//Output: 7
//****

//Intersing right
```

### Here comes closure into picture

### Functions are so beautiful, when functions are returned from another function they still maintains their **lexical scope**. They remember where they were actually present lexically.

### Though 'x' is not there still the y() remembers it's lexical scope, where it came from. So, it remembers there was something known as 'a' and it has bindings.

### When we returned the y(), not just that function code was rerurned but **closure** was returned.

### That closure enclosed function along with it's lexical scope was returned. And it was put inside 'z'.

### So, when we execute 'z' somewhere else in our program, it still remembers 'a' , still remembers the reference to 'a'.

## Function along with it's lexical scope bundled together forms a closure.

### Now let's cover some corner cases

```js
function x(){
    var a = 7;
    function y(){
        console.log(a);
    }
    a = 100;
    return y;
}
var z = x();
console.log(z);
//******
z();

//Output: 100

//so, why the output is not 7???
//because, z comes along with it's lexical scope
//mean returned with it's lexical scope
//'a' does not refer to the value
//it is 'a's refernce which was returned
//functions along with the reference to those variables was returned
//reference to 'a' persist
//function remembers the reference to that a's memory location
//when z() is excuted that refernce to a points to 100
//so, that means 100 is still in the memory present, preserved because of closure
//so, when 'x' was gone it was not 'garbage collected'
//because it has to be used later  
```

### Now let's go one more level deep inside the scope chain

```js
function z(){
    var b = 900;
    function x(){
        var a = 7;
        function y(){
            console.log(a, b);
        }
        y();
    }
    x();
}
z();

//so, now y() forms a closure with z() and x()
//means clousre formed with z() remembering b = 900;
//closure formed with x() remembering a = 7
```

### Now let's see some usage of closures

- Uses of Closures
 - Module design pattern
 - Currying
 - Functions like once
 - memoize
 - maintaining state in async world
 - setTimeouts
 - Iterators
 - and many more...
