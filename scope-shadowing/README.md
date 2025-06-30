### A block is defined by '{}' these curlybraces.

```js
{}//this is a valid js code
//this is a block
//it's doing nothing here

//but why do we use block and what is the use of it
```

- Block is also known as compound statement.
- A block is used to combine multiple js statements into one group.

```js
{
    //compound statement
    var a = 10;
    console.log(a);
}
```

### We group multiple statements together in a block so that we can use it where js expects one statement.

```js
if(true)//syntaxError:Unexpected end of input
//because it expects a statement here(one statement)

//but if we want to write multiple statements
//we can only do that by grouping statemts together

if(true){
    //compound statement
    var a = 10;
    console.log(a);
}

//so, these multiple statements can be used
//in a place where js expects a single statement

if(true) console.log("hello");//one statement
//but when need multiple statement
//then use {block} to group statements together
```

### Now, let's see what is a block scope.

- **Block scope means what all variables and functions we can access inside this block**

### Now, let's 3 types variable inside of a block and observe how they behave and what happens behind the scene.

```js
{
var a = 10;
let b = 20;
const c = 30;
}

//when we run this code
//a will be in the global scope
//b and c will be in the block scope (outside global or not it global)
//so, b and c are hoisted and assigned undefined
//in a separte memory space that is reserved for block
//in case of 'a' it is hoisted inside the global scope
//so, finally variable declared with var
//hoisted in a global scope
//and variable declared with let and const
//hoisted in a block scope
//that is why that statement came into picture
//that, let and const are block scoped
//that means they are stored in a separate memory space
//which is reserved for block

//that is why we can not access let and const
//outside of the scope since they are inside block scope
//but, we can access var even outside the scope since it is global scoped
```

```js
{
var a = 10;
let b = 20;
const c = 30;

console.log(a);//Output: 10
console.log(b);//Output: 20
console.log(c);//Output: 30
}

//after finishing executing the block 
//the block memory space will be gone 
//and only global will remain
//only a will be present in the global

console.log(a);//Output: 10
console.log(b);//Output: ReferenceError: b is not defined
console.log(c);
```

### Now, let's see what is shadowing in js 

```js
var a = 100;//if we have a same named variable outside of the block
{
var a = 10;//this variable shodows the variable that is outside of the scope
let b = 20;
const c = 30;

console.log(a);//Output: 10 not 100 (it was shadowed)
console.log(b);//Output: 20
console.log(c);//Output: 30
}
console.log(a);//Output: 10 still 10
//because they pointed to the same memory location
```

### But that is not the same case for 'let'

```js
let b = 100;
{
var a = 10;
let b = 20;
const c = 30;

console.log(a);//Output: 10
console.log(b);//Output: 20 shadowed the upper 'b' in the Script scope(separate memory location)
console.log(c);//Output: 30
}
console.log(b);// Output: 100 because of scope
//now there is 'b' in two scopes
//one is block
//another one in script, outside of the block

//so we have got three types of scopes
//one is global where var is attached
//another one is block scope where let and const attached
//anothe one is separate memory space where let and const are hoisted

//for const the same is same as let
//shadowing not only limited with scope
//it works the same way for the function as well
```

### Now, let's see what is illegal shadowing

```js
var a = 20;
{
    var a =20;
}
//this was straight forward

//but we can not do the following
let a = 20;
{
    var a =20;
}
//Output: SyntaxError: Identifier 'a' has already been declared
//so, it we want to shadow a let variable inside the block using a var we can not do that

let a = 20;
{
    let a =20;
}

//this is fine 
//we can shadow let using a let
//but we can not shadow let using var

//but can we do the following
var a = 20;
{
    let a =20;
}
//yes, we can

let a = 20;
function x(){
    var a =20;
}
//no, erro, var inside it's boundary, no illegal
```

### Block scope also follows lexical scope. So, these scopes are lexically present

```js
const a = 20;
{
    const a = 100;
    {
        const a = 200;
        console.log(a);//a will get access from the nearest 'a' 
    }
    console.log(a);//100
}
```

