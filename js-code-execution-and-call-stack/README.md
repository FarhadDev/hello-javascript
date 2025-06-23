# What heppens when we run a javasctipt program?
### Answer: An execution context is created.

- This execution context is created in two phases.
- The first phase is known as the "creation phase". This is also known as the "memory creation phase."
    - When we run the code in the memory creation phase, javascript will allocate memory to all the variables and functions.
    - Now the question is what does it stores?
        - When it allocates memory to variable "n" it stores a special value called "UNDEFINED".
        - In case of functions it literally stores the whole code of the function inside this memory space.
        - So, in the first phase javascript sceems through the whole program line by line and it allocates memory to the all the variables and fuctions.

    - Now let us talk about the second phase. The second phase is the code execution phase. Let's see how this code is now executed after the memory allocation.
        - Now javascript once again runs through the whole js program line by line and it executes the code now.
        - As soon as it encouters the first line "var n = 2" is actually places the 2 inside "n".
        - So, till now the value of "n" is "undefined", now in the second phase of the creation of execution context which is the code execution phase the "2" value of "n" gets inside in place of undefined.
        - Functions are like a mini program. And whenever a new function is invoked() or a mini program is invoked "A altogether new execution context is created".
        - The whole program we were running inside an "Global Execution Context". Now, when we run a function() or invoke() a function brand new exection context is created.
        - Now again we will go through the creation of the execution context for the new execution context and again there will be two phases. Memory creation phase and code execution phase.
        - ##### When we say all the variables and functions it involves the parameters also while invoking a function.
        - Now, when we encounter the "return" statement of the function it just simply tells the function "you are done with your work now, just return the whole control back to Execution Context where the function was invoked".
        - Retun value is collected from the local memory space.
        - One more thing which happens when the whole function is executed is that the whole execution context for that instance of that function will be "deleted".

    - Now there is nothing to execute and javascript is done with all it's work and the prorgram is finished so what will happen is the Global Execution Context will be deleted, it goes off. That is how the whole javascipt code is executed.

    - # But don't you think all these is too much to manage for javascript engine like execution context is created one by one inside one another one and goes on.
        - It is difficult to manage for javascript engine but it does it very beautifully.
        - ##### So, how it does it?
        - It handles everything to manage this execution context creation, deletion, control-- "It Manages a Stack".
        - ##### This is known as the "Call Stack".
        - So, what is this call stack now?
        - The call stack is a stack and everytime in the bottom of the stack we have our "Global Execution Context".
        - That means when a javascript program runs this call stack gets populated with the "GEC".
        - Whenever a function is invoked() or a new execution context is created that new execution context is put inside the stack.
        - Once we done with the function execution and retun, the E1 is poped out of the stack.
        - So, E1 is poped out and control goes back to the GEC.
        - Another function invoked E2 pop in inside the stack and same cycle.
        - So, this call stack is only for maning this execution context.
        - So, whenever a execution is created it is pushed into the stacka nd whever a execution context is deleted it is moved out from the stack.
        - And finally after the whole program is executed the call stack gets empty.

        - ### Call stack maintains the "order of execution" of the execution contexts.

        - Call stack is also known by very fancy names.
            - Execution Context Stack
            - Program Stack
            - Control Stack
            - Runtime Stack
            - Machine Stack
