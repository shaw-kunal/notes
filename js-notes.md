BASIC CONCEPT:

 1. DATA TYPE IN   :
ans:  primittive data types 
     - string, number, null , undefined ,  boolean  , sysmbol
      note:  symbol used to create unique identifier for object eg: let sym = Symbol('unique') 

      Non primmittive data types: 
      object,  array, function, 
    

2. primittive type :   it is most basic data types ans they are immutable and  are store by value.
eg:  let name = "kunal"

Reference types: are object that are multable and are stored by referece. When you assign a reernce type varible to another variable , both variable point to the same memory location.





3. . Mutability and Immutability
Mutability: A type is mutable if its value can be changed after it is created. Reference types (like objects and arrays) are mutable.
<!-- 
let arr = [1, 2, 3];
arr[0] = 10; // Mutates the original array
console.log(arr); // Output: [10, 2, 3]

 -->

Immutability: A type is immutable if its value cannot be changed after it is created. Primitive types (like strings and numbers) are immutable.

<!-- 

let str = "Hello";
str[0] = "h"; // Does not change the original string
console.log(str); // Output: "Hello"

 -->
<!-- ########################################################################################################################################## -->

 4. Scope and closure: 


 Scope: it define the  visibility of  variables. In javascript , there are three types of scopes.

 Global Scope:  
 function scope
 block scope:  { }

 1. Global Scope: Varible decalre globally (outside any function) have global scope.
 Global variable can be accessed from any where in javascript program.

 
2. Function Scope: Variable decalre within a function are only accessible inside that function . They can not be accessed from outside.

usage of Var: variable  decalred with var inside a function are function-scoped. If decalred outside a function , they are globally scoped.
 behaviour of let and const inside it are similar to  funcion scoped.


<!-- 
eg: function example(){
   var x = 10;

   console.lo(x) //10
};
   console.lo(x) //reference error
 -->


3. Block scope: Block scope referes to the area with in curly braces  {},  and variable declare inside the block are accessible only inside the block.

Behavior of var: var does not respect block scope. It is hoisted to the nearest function scope, meaning if it's declared inside a block, it will still be accessible outside the block but within the function.

<!-- 
if(true){
  var a = 4;

}

console.log(a)// 4 
-->

<!-- ########################################################################################################################################### -->

Closure:A closure is a feature in javascript where a function remember the varaible or lexical enviroment  from  the scope where it was create even when it's is called outside that scope.

<!-- eg: 

function outerFunction(){
  let outerVar = "I am from the outer scope";
  function innerFunction(){
    console.log(outerVar);
  }
  return innerFunction;
}
const closureFun = outerFunction();
closureFun();
-->


<!-- ######################################################################## -->

Describe the function scope and block scope and how var , let,const behave in each?

ans: 
1. Function Scope: Variable decalre within a function are only accessible inside that function . They can not be accessed from outside.

usage of Var: variable  decalred with var inside a function are function-scoped. If decalred outside a function , they are globally scoped.
 behaviour of let and const inside it are similar to  funcion scoped.


<!-- 
eg: function example(){
   var x = 10;

   console.lo(x) //10
};
   console.lo(x) //reference error
 -->


2. Block scope: Block scope referes to the area with in curly braces  {},  and variable declare inside the block are accessible only inside the block.

Behavior of var: var does not respect block scope. It is hoisted to the nearest function scope, meaning if it’s declared inside a block, it will still be accessible outside the block but within the function.

<!-- 
if(true){
  var a = 4;

}

console.log(a)// 4 
-->
Behavior of let and const: let and const are block-scoped. They are confined to the block in which they are defined and cannot be accessed outside of it.
<!-- 
if (true) {
    let b = 10;
    const c = 15;
}
console.log(b, c); // ReferenceError: b and c are not defined -->


####################################################################################################################################################

Closures and their practical uses.   

ans:  A closure is a feaute in javascript wheare a function remember the varaible or lexical enviroment  from  the scope where it was create even when it's is called outside that scope.


How it work: 
when a function is defined inside another function, the inner fuction has access to :

1. it own  scope.
2. the scope of the outer fuction.
3. Global scope.

Pratical uses:

 Closure are widely used in javscript for a variety of tasks.

1. Data Privacy/ encapsulation:

<!--  

  function counter(){
  let  count = 0;

  return 
  {
     increment : function(){
     count++;
     },

     decrement: function(){
     count--;
     }
  }
}

const myCounter = counter();
myCounter.increment(); // 1
myCounter.increment(); // 2
myCounter.decrement(); // 1

-->

2. creating function with preant argument  


<!-- 

  function multiply(a) {
    return function(b) {
        return a * b;
    }
}

const double = multiply(2); // "a" is remembered as 2
console.log(double(5)); // 10

 -->


3. memoization / caching:

 closure can help store computed values(cache) and avoid recomputation.

 eg: 

 <!-- 
   function memoize(fn){
     let cache= {};
     return  function(arg){
        if(cache[arg]){
          console.log("Fetching from cache:", chache[arg]);
          return cache[arg];
        }else{
        let res = fn(arg);
        chach[arg] = result;
        console.log("calculting result:", result);
        return result;
        }
     }
   }

   const square = memoize(x=> x*x); 
  -->


  ############################################################################################################################################

 Q. Define Callback , Promise and asycn/await??

 ans:  In javascript, Callback , promises and async/await  are machanism used to handle asynchronous  operation. Each method provides a ways to manage  task.

 1. callback : A callback is function that is passed as an argument to another function and is executed after some asychorous operation is completed.

  eg: after 10 second , just show a greeting message.
  function gretting
   

but there is issue called as callback hell:  when multiple async operation are chain using the callback, it is difficult to read and maintain  the code , and code become horizonatally expanded. 

<!-- 
fetchData((result) => {
    console.log(result);
    anotherAsyncFunction((response) => {
        console.log(response);
        yetAnotherAsyncFunction((finalData) => {
            console.log(finalData);
        });
    });
});

 -->



 2. Promises:  A promise is an object that represents the eventual completion or faiture of an asynchronous operation. It can  be in one of three state.

 * pending : Initial state, neither fullfill  nor rejected.
 * Fulfilled
 * Rejected:

<!-- 
 eg: const myPromise = new Promise((resolve, reject)=>{

        setTimeOut(()=>{
              resolve("Promise resolve");
        },[5000])
 })

  myPromise.then((result)=>console.log(result))
 -->


3. Async and await :  is a syntatic sugar built on top of Promise, introduces in ES2017. It allows writing  asynchronous code in sync style, making it easier to read and maintain

. async keyword is used to declare a function as asynchronous. An asycn function always return a promise.

. await: this keywork paruse the execuaton of the fucntion untill the promise is resolve or reject. it can only be used inside async functions.






##########################################################################################################################################


Q. Event Loop:  Javascript is single threaded,  meaning it can only  do one thing at a time. However we often want to run task without  blocking other code (like waiting for user input, timer etc). The event loop helps manages tasks.


the event loop job is to :
 1. Look at the call stack ( where  javasript code is  execuated)
 
 2. Look at the task queue ( where tasks like  setTimeOut,event etch wait)

3. if the callstack is empty , it moves tasks from the task queue to call stack for execution.


MircroTask: Microtask are similar to task but have higher priority. These include:-

Promises-
MutationObserver-


Now event loop checks the microtask queue before moving on to  tasks queue. If there are microtasks, they will be execuated right after the current task finishes but before moving on next one.

execution order: 
1. Code in the callstack runs first.
2. After that , all microtasks are executed.
3. Then, tasks from the tasks queue(like setTimeout) are execuated.



###################################################################################################################################################.

Q. Arrow function vs regular functions - 
ans: Both Arrow functions and regular functions are two ways to defined  functions in javacript, and they have some key differences.

The main differnce  between arrow function and  regular function
is   that arrow function does not have their own this contex.Instead , they inherit this from the surrounding lexical scope, which can be useful in certain situation.


###################################################################################################################################################.

Q. prototypes and inheritance in javascript: 
 ans: in javascript , prototypes and inheritance are core concept  that enables object to share properties and method, promoting  code resuse and modularity.


 1. '''Prototypes''': Every Javascript object has an internal property called [[prototype]], whcih refers to another object. This mechinism allows an object to  inherience propertiese and  method from another object.

Prototype Object: When you create an object, you can specify its prototype using Object.create(), or it is automatically set when using constructor functions or classes.

<!-- 



 const animal = {
  sound: 'generic sound',
  makeSound() {
    console.log(this.sound);
  }
};


const dog = Object.create(animal);

dog.sound = "bark"
  dog.makeSound();
 -->


2. constructor function and prototype:
 You can create Object with constructor function. Each costructor function has a prototype protype where you can define shared properties or method.

 Exmaple:
 
  <!--
  
  function Animal(sound){
      this.sound = sound;
 } 

 Animal.prototype.makeSound = function(){
     console.log(this.sound);
 }
 

 const dog = new Animal('bark');
 const cat = new Animal("meow');

  dog.makeSound(); // Output: 'bark'
  cat.makeSound(); // Output: 'meow'

 -->

 3. 





















###################################################################################################################################################


In JavaScript, call(), apply(), and bind() are methods that allow you to set the this context (i.e., the object that a function should operate on). They are primarily used for function borrowing and explicitly setting the context of a function.

1. call()
call() immediately invokes the function, allowing you to pass arguments one by one.

Syntax:
javascript

function.call(thisArg, arg1, arg2, ...)

const person = {
  firstName: 'John',
  lastName: 'Doe',
  fullName: function() {
    console.log(this.firstName + ' ' + this.lastName);
  }
};

const person2 = {
  firstName: 'Jane',
  lastName: 'Smith'
};

// Using call to borrow fullName method from person
person.p.call(person2);  // Output: Jane Smith
2. apply()
apply() is similar to call(), but it takes arguments as an array or array-like object instead of listing them one by one.

Syntax:
javascript
Copy code
function.apply(thisArg, [argsArray])
Example:
javascript
Copy code
function greet(greeting, punctuation) {
  console.log(greeting + ', ' + this.firstName + punctuation);
}

const person = {
  firstName: 'John'
};

greet.apply(person, ['Hello', '!']);  // Output: Hello, John!
3. bind()
bind() does not immediately invoke the function. Instead, it returns a new function with the this context set to the provided value. You can call this new function later.

Syntax:
javascript
Copy code
const boundFunction = function.bind(thisArg, arg1, arg2, ...)
Example:
javascript
Copy code
const person = {
  firstName: 'John',
  lastName: 'Doe',
  fullName: function() {
    console.log(this.firstName + ' ' + this.lastName);
  }
};

const person2 = {
  firstName: 'Jane',
  lastName: 'Smith'
};

// Using bind to create a new function with person2 as the this context
const boundFullName = person.fullName.bind(person2);

boundFullName();  // Output: Jane Smith
Key Differences:
Feature	     |   call()	                          |  apply()	                            |bind()
Invocation	 |   Immediately invokes the function	|  Immediately invokes the function     |	Returns a new function (does not invoke immediately)
Arguments    |	Passed one by one	                |   Passed as an array	 |       Passed one by one (or partial application)
Use Case	When you know arguments in advance and want to call immediately	When you have arguments as an array	When you need a function for later use with a specific this context





################################
what is prototype chainging ?

Prototype chaining in javascript is a feature of its OOP. Every javascript object has a prototype, which is reference to another object. This prototype object can have its own prototype ans so on , forming a chain .

when you access a property or method on an obect, javascript look for it on the object first, if it does not find it, it looks up the prototype  chian to find it.


let animal = {
  eats:true,
  walk(){
    console.log("Animal walks");
  }
}

let rabbits ={
  jumps : true;
}
rabbits.__proto__ = animal;

console.log(rabbits.jumps);
consol.log(rabbits.eats);
rabbits.walk();

#######################################################

What is jSON ?

JSON  is a light weight data format that is easy for humans to read and write and east for machines to parse and generate. It's commonly  used to transmit data between a server and web application as text.


key feature of json :
 ->light weight 
 -> for data interchange format
 -> text based
 -> language indepent

################################################################

what it the purpose of array splice method ?
Array splice method is used for add /remove element from the array and  return the remove item. The first argument specifies the array position/index for insertion or deleteion where as optional second  argument indicate the number of element to be deleted. Each addtional argument is added to the array.



<!-- let arr = [1,2,3,4,5]

let arr1 = arr.splice(2,3);
arr = arr.splice(1)
console.log(arr1)
 -->




###############################################################
Q. what is difference between the object and map?

Object and map both  are used to store the key value pair but they have different characteristc and use cases.

1. key type: 
in object , key type must be string or symbol.  other data type like number or object  automatically converted into string.

In map ,  keys can be of any type (object , function, arrat ,number)
<!-- const map = new Map();

map.set("name", "kunal");
 -->

2. Iteration: 
  Object: you can iterate over and object using for...in loop 

  map: Maps maintain the insertion order of keys and are directly iterable using for...of loops.

<!-- 
for(let [key, value] of map){
  console.log(key, value)
} -->

3. OBJECT:there is no direct method to find the  size of the object
   you must calculate the size manually using Object.keys().length

   let obj = {a:1,b:2}

   <!-- console.log(Object.keys(obj).length) -->

   
   MAP:  maps are optimized for frequent additions, deletions and lookups. Maps perform better when handling a large number of key-value pairs.

   4.Order of Keys:
    Object:
    Since ES6, object keys are ordered in a specific way: integer-like keys are sorted, and string keys follow the order of insertion.
    Map:
    Maps preserve the insertion order of keys.


################################################################

Q.what is the difference between == and === operators?

 Javascript provides  both strict(===) and type-converting(==) equality compairson. 

 
 (==) loosely euality- compare two values after perforing  type  conversion 
 <!-- 5=='5'//true -->

 (===) strict equality : compare two values without type conversion 
 <!-- 5==='5' //false -->





 ###############################################################

Q. what is lambda expression or arrow functions.
ans : An arrow fucntion is a shorter  syntax for a functio expression and does not have own its , arguments, super or new target . These functions are best suited for non-method functions, and they can not be used as constructor.



 ###############################################################


Q. what is first class function ? 

ans : first class function means  when functions in that language are treated like any other variable .

For example: in such language , a function can be passed as an argument to other function , can be return by another function and can be assigned as a value to a varibale


<!-- 

 const handler = ()=> consol.log("this is click handler)

 document.addEventListner("click", handler);
 -->

#############################################################

Q. what is first order function ?
ans: A first order function that does not accept another function as an argument and does not return a function as its return value.

<!-- 
const firstOrder = () => consle.log("i am a first order function")
 -->


###########################################################

Q. what is higer order function ?;
ans : A higher order function that accept another functiona as an argument or return a function as a return value or both. 


<!-- 
const firstOrderFunc = () =>
  console.log("Hello, I am a First order function");
const higherOrder = (ReturnFirstOrderFunc) => ReturnFirstOrderFunc();
higherOrder(firstOrderFunc);
 -->

 #######################################################
Q. what is unary function ?
A unary function (i.e. monadic) is a function that accepts exactly one argument. It stands for a single argument accepted by a function.


<!-- const unaryFunction = (a) => console.log(a + 10); // Add 10 to the given argument and display the value -->


Q. Event Loop: The event loop is the heart of how javascript handle the asynchronous operation.

Javascript is single threaded meaning it runs one thing at a time. But thaks to the events loop. it can still handle async taks like setTimeout ,promises, fetch ,etc.

1. call stack: Where code is executed line by line.
Web APIs: Browser APIs like setTimeout, DOM events.

Callback Queue: Stores async callbacks (from timers, DOM events).

Event Loop: Keeps checking if the call stack is empty, then moves the first task from the queue into the stack.



2.Event Bubbling:
When an event occurs on a nested element, it bubbles up from the target element to its parents.

3. event Capturing:Opposite of bubbling: the event is captured from the outermost parent down to the target.

how to enable capturing:
element.addEventListener('click', handler, **true**);




#Hoisting in variables and function declarations.



whenever a function is called or the program strats, javascript create and environment called an execution context.

There are 2 types of execuiton context:
Globla Execution Context : Created when your script runs: 
Function Execution Context (FEC): Created every time a function is called


Phase of execution context:

##Memory Creation phase(a.k.a Creation Phase):
Variables and functions are hoisted
Variables are set to undefined
Functions are fully stored in memory


##Execution phase
Code runs line by line.
Variable get actual values.
Functions are executed.


Hosting: Javascript move declarations to the top during memory phase.










#############################################################
💡 What is a Higher-Order Function?

A higher order function is a function that
1.Takes another function as an argument, or return a function.


map() - Transform an array.
filter() – Filter elements based on a condition
Returns a new array containing only the elements that pass a test.🔹 It doesn’t change the original array;

reduce() => reduce array to a single value.

it runs a function on each element and reduce the array into single value.


const numbers = [1,2,3,4]
const total = numbers.reduce((acc,curr)=>acc+curr,0);

<!-- 
eg:
array.reduce((accumulator, currentValue, index, array) => {
  return updatedAccumulator;
}, initialValue);

const fruits = ['apple', 'banana', 'apple', 'orange'];

const count =  fruits.reduce((acc,curr)=>{
   acc[fruit] = (acc[fruit] || 0 )+ 1
},{})

consoel.




 -->








List of Questions from js-notes.md
Describe the function scope and block scope and how var, let, const behave in each?

Closures and their practical uses?

Define Callback, Promise and async/await?

Event Loop: Javascript is single threaded, meaning it can only do one thing at a time. However we often want to run task without blocking other code (like waiting for user input, timer etc). The event loop helps manages tasks?

Arrow function vs regular functions?

Prototypes and inheritance in javascript?

What is prototype chaining?

What is JSON?

What is the purpose of array splice method?

What is difference between the object and map?

What is the difference between == and === operators?

What is lambda expression or arrow functions?

What is first class function?

What is first order function?

What is higher order function?

What is unary function?

What is Event Loop?

What is Hoisting in variables and function declarations?

What is a Higher-Order Function?

<!--#### Event Loop and Asynchronous JavaScript Interview Questions ########-->
<!-- Q. What is the difference between the task queue and microtask queue in JavaScript? -->

Task Queue (Macrotask Queue):
-Handles regular asynchronous tasks like setTimeout, setInterval, I/O , UI rendering, and event callbacks
-Lower priority than microtasks
-Tasks are processed one at a time, allowing UI updates between tasks

Microtask Queue:

-Handles Promise callbacks (.then(), .catch(), .finally()), queueMicrotask(), and process.nextTick() (in Node.js)
-Higher priority than tasks
-All microtasks are processed completely before the next task is handled

<!-- Q)How does the event loop prioritize tasks? Explain the execution order. -->

The execution order follows this pattern:

1.Execute all synchronous code in the call stack
2.Once call stack is empty, process all microtasks until the microtask queue is empty
3.Perform a single task from the task queue
4.Update rendering if needed
5.Return to step 2

This means microtasks always get priority over tasks, and all microtasks that are generated during the processing of other microtasks will also be processed before moving to the next task.

 <!-- Q.What types of operations go into the microtask queue versus the task queue?> -->
Task Queue (Macrotask Queue):
Handles setTimeout, setInterval, I/O, UI events
Microtask Queue: Handles Promise callbacks (.then, .catch, .finally), queueMicrotask()




<!-- Q.If you have a setTimeout with 0ms delay and a Promise that resolves immediately, which one executes first and why?
The Promise resolves first. -->

Why:
JavaScript uses an event loop with two main queues:
Microtask queue (e.g., Promises)
Macrotask queue (e.g., setTimeout, setInterval)
Even if setTimeout is set to 0ms, it is placed in the macrotask queue, which is processed after the microtask queue is emptied.

<!-- 
Explain how the call stack, event loop, and task queue work together to handle asynchronous operations. -->

In JavaScript, asynchronous operations are handled using the call stack, event loop, and task queues. Here's how they work together:

<!-- Call Stack: -->
This is where JavaScript executes code synchronously, function by function.

<!-- Web APIs: -->
When asynchronous code like setTimeout, AJAX, or Promises are encountered, they're handed off to browser APIs, which handle them separately.

<!-- Task Queues: -->
Microtask Queue: For Promises and queueMicrotask. These run after the current stack but before any macrotasks.
Macrotask Queue: For tasks like setTimeout, setInterval, and DOM events.

<!-- Event Loop: -->
It constantly checks if the call stack is empty.
If yes, it first clears all microtasks.
Then picks the next macrotask and pushes it to the stack.



<!-- What is "callback hell" and how do Promises and async/await help solve this problem? -->
Callback Hell is when you nest many callbacks inside each other, leading to messy, hard-to-read code.



<!-- How does the browser render UI updates in relation to the event loop? -->

The browser renders UI updates after the microtask queue is empty and before the next macrotask begins.
Detailed Flow:
JS runs on the call stack.

-Microtasks (like Promises) are executed after the current task.
-UI rendering happens right after microtasks, before picking the next task from the macrotask queue (e.g., setTimeout).
-Then, the event loop picks the next macrotask.


<!-- 
What happens when the microtask queue keeps getting new microtasks? Can this block the rendering? -->

Yes, if the microtask queue keeps getting new microtasks, it can block rendering.

Why?
The browser only renders UI after the microtask queue is empty.

If microtasks keep adding more microtasks (e.g., recursive Promises), the queue never empties, and rendering is delayed.





<!-- Explain how JavaScript handles concurrent operations despite being single-threaded. -->
JavaScript achieves concurrency by offloading async tasks to external APIs and using the event loop to process their callbacks asynchronously, keeping the single thread free to execute code without blocking.



<!-- What are Web Workers and how do they relate to the main thread's event loop? -->
Web Workers are background scripts that run in separate threads from the main JavaScript thread.

Key points:
They allow parallel execution of JavaScript, so heavy computations don’t block the main thread or UI rendering.

Web Workers have their own event loop, call stack, and memory.

Communication between the main thread and workers happens via message passing (postMessage), which is asynchronous.

The main thread’s event loop continues running independently while workers do their tasks in parallel.

Summary for interview:
Web Workers run scripts in separate threads with their own event loops, enabling parallel processing and preventing the main thread from being blocked, improving app responsiveness.







<!-- How does error handling work in the event loop with async operations? -->
Errors in async operations are handled through callbacks, promises, or async/await. The event loop keeps running, passing errors to appropriate handlers without blocking other tasks.


<!-- What happens when you have a long-running synchronous task in JavaScript? How does it affect the event loop? -->
Long synchronous tasks block the call stack and event loop, preventing async operations and UI rendering until the task completes, leading to a frozen or laggy user experience.








<!-- How do microtasks affect the rendering of a web page? -->
Microtasks run before rendering; excessive or infinite microtasks can block UI updates and delay page rendering.







<!-- What is "task starvation" in the context of the event loop? -->
In the event loop context:
If microtasks (like Promises) keep adding more microtasks, macrotasks (like setTimeout) can get starved—they never get a chance to run.

This causes some callbacks or UI updates to be indefinitely postponed, hurting responsiveness.


<!-- How does Node.js's event loop differ from the browser's event loop? -->
Key Differences Between Node.js and Browser Event Loops:

Phases:

Node.js event loop has multiple phases:

Timers (e.g., setTimeout)

Pending callbacks

Idle, prepare

Poll (I/O events)

Check (setImmediate)

Close callbacks

Browser event loop is simpler, mainly handling macrotasks (timers, UI events) and microtasks.

APIs and Tasks:

Node.js event loop manages I/O callbacks, file system, and networking differently, optimized for server-side workloads.

Browsers manage rendering, user interactions, painting, and compositing tasks alongside script execution.

Microtasks Handling:

Both run microtasks (Promises) after each macrotask, but Node.js has subtle differences in timing and priorities.




<!-- What happens when you create a Promise inside a Promise's then() handler? How does the event loop handle this? -->
Creating a Promise inside a .then() adds new microtasks that the event loop queues after the current microtasks finish, ensuring promise resolutions happen in sequence without blocking the event loop.






