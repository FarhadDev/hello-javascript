```js
function x(){
    var i = 7;
    setTimeout(function (){
        console.log(i);
    },3000)
}
x();
//here the output will be 7 after 3 sec
```

### Now see a different case

```js
function x(){
    var i = 7;
    setTimeout(function (){
        console.log(i);
    },3000)
    console.log("Hello Javascript");
}
x();

//now, here it seems like js will wait for 3 sec
//then prints 7 and then prints Hello Javascript
//but that's not the case
//js won't for anyone
//rather the output will be Hello Javascript
//after 3 sec prints 7
//time tides js wait for none
```

### But why the output is like this for the upper example

- The callback function inside the setTimeout forms a closure
- So, this function remembers the reference to i
- So, wherever the function goes it takes the reference of i along with it
- Now, what setTimeout do is it takes the callback function and stores in some place and attaches a timer to it
- And js procedes and don't wait
- It just goes to next line and print "Hello Javascript"
- Once that timer expires, once that 3000 milsec is finished it takes that function and **puts it again to the callstack** and runs it. That's how setTimeout works.
- setTimeout takes this callback functiona and attaches a timer and when the timer expires then it calls that function.

### Now let's another crapy code chunk

## Let's say we are given a problem we need to print one, two, three, four, five in the console after each and every second.

# One after one second, two after two second and goes on...

```js
//Now most of us will think about the for loop
//like the following

function x(){
    for(var i=1; i<=5; i++){
        setTimeout(function(){
            console.log(i);
        },i*1000)
        console.log("Hello Javascript");
    }
}
x();

//But NOOOO. that's not how it works
//the output here is
//6 6 6 6 6
//why it is printing 6????
//it printed after correct pause
//like after one sec prints 6
//after 2 sec prints 6 and so on...
```

### Now it is behaving this way because of the closures

- So, let's remember what is a closure
- A closure is like function along with it's lexical environments.
- So, even if the function is taken out from it's original scope, if it is executed in some other scope still it remembers it lexical environments.
- Now what will happen when this setTimeout takes this function ans stores it somewhere else and attaches a timer.
- So, that function remembers the reference to that 'i'
- Not the value of 'i', reference to 'i'
- When the loops runs the first time 
    - It makes a copy of the function and attaches a timer and also remembers the reference of 'i'
    - Similarly these five copy of this functions all of them are pointing to same reference of 'i'
    - Now, js don't wait for anything
    - It will run the loop again and again and stores these five functions and move on and does not wait those timers to expire
    - So, it will print "Hello Javascript"
    - And when the timer expires it is too late
    - Because the loop was constantly running 1,2,3,4,5,6
    - So, the 'i' value became 6
    - Increment went to 6
    - And when that callback function runs by that time the value of 'i' is 6
    - In the memory location it is 6
    - That's why it is printing 6 every time
    - All of these callback functions or copy of these functions 'i' is spotted in the same space in memory

### Now, how we can fix this???

### A simple and quick fix is to use let instead of var

```js
function x(){
    for(let i=1; i<=5; i++){
        setTimeout(function(){
            console.log(i);
        },i*1000)
        console.log("Hello Javascript");
    }
}
x();
```

- Now let has block scope
- That means for each and every loop iteration
- Whenever every time loop runs this 'i' is a new variable altogether
- And each time setTimeout is run
- The callback function has a new copy of 'i' with it
- Because this let variables are block scoped
- Each and every time the setTimeout is called 
- The function forms a closure with a new variable itself
- It makes five new copies of 'i' and each callbacks forms a closures with them

### Now another crap. We need to solve this using 'var'

## Now again only closure will help us

```js
//somehow we need to give 'i' a new copy in every iteration

function x(){
    for(var i=1; i<=5; i++){
       function close(i){
         setTimeout(function(){
            console.log(i);
        },i*1000)
       }
       close(i);
    }
     console.log("Hello Javascript");
}
x();

//we have wrapped setTimeout inside the close function
//and somehow we need to supply the 'i' everytime with a new copy of 'i'
//why this works???
//everytime we call the close function with 'i'
//it creates a new copy of 'i' for itself 
```