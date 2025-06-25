## Do you know what is the shortest javascript program?
### It is the empty file with tha .js extension.

### Even the file is empty and there is nothing to execute still javascript engine doing a lot behind the scene.

## Now let us see what happens behind the scene when we run the shortest javascript program.

### Let's just put a debugger on the first line on the browser and execute.
- A global execution context is created.
 - Js engine still creates this global execution context and sets up the memory space.
 - It also does something intersting.
 - Js engine also creates something known as window.
 - In console write window. Where it is coming from?
 - Window is like a big object with a lot of variables and methods.
 - There variables and methods are created by the Js engine and into the global space, we can access all these variables and functions anywhere in our js program.
 - Just like this window js will also create a "this" keyword. 
 - If we console "this" we also get something.
 - And at the global level this "this" point to the "window" object.
 - So, what is window?
 - Window is actually a global object which is created along with the global execution context.
 - So, wherever a js program run a global object is created, a global execution context is created and along with that global execution context a "this variable" is created.
 - So, this global object in case of browser, it is known as "window".
 - Reminder, js is not only runs in browser, js runs also in browsers and lot of other devices as well.
 - Wherever js is running there must be a js engine there. In chrome v8, mozilla has it's own.
 - All these js engines has a responsibility to this global object. In browser it is "window" and in node it is something else.
 - So, at the global level (this === window).
 - Whenever we create an execution context a "this" is created along with it. Even of the functional execution context.
 - But wait, what the heck is that "global space".
 - This global space is nothing but any code we right is js which is not inside a function.

 ```js
 var a = 10;// this is inside global space

 function b(){// the function is inside the global space
    var x = 10;// but this x is not inside the global space as it is inside a fucntion
 }
 ```

 #### So, wherever we create variables and functions in the global space what happens, these variables and functions get attached to that global object. Window object in case of browser.

 - We can access them like just window.a

 ```js
 console.log(window.a);
 console.log(a);
 //if we don't put anything in fornt of a it automatically assumes that we are reffering to the global space.
 ```

 ```js
 //if we try to log x over here
 console.log(x);//output: Uncaught ReferrnceError: x is not defined
 //because it is assuming we are reffering to the global space.
 ```
  
