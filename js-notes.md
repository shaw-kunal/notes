BASIC CONCEPT:

 1. DATA TYPE IN JAVASCRIPT:
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


 4. Scope and closure: 


 Scope: it define the  visibiluty of  variables. In javascript , there are three types of scopes.

 Global Scope:  
 function scope
 block scope:  { }



Closure: A closure is a function that  remember the varaible or lexical enviroment  from  the scope where it was create even when it's is called outside that scope.

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


########################################################################

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

2. creating function with present argument  


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
   

but there is issue called as callback hell:  when multiple async operation are chain using the callback, it is difficult to read and main the code , and code become horizonatally expanded. 

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



 2. Promises:  A promise is an object that represents the eventual completion or failture of an asynchronous operation. It can  be in one of three state.

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

3. if the callstack is empty , it moves tasks fro the task queue to call stack for execution.


MircroTask: Microtask are similar to task but have higher priority. These include:-

Promises-
MutationObserver-


Now event loop checks the microtask queue before moving on to  tasks queue. If there are microtasks, they will be execuated right after the currect task finishes but before moving on next one.

execution order: 
1. Code in the callstack runs first.
2. After that , all microtasks are executed.
3. Then, tasks from the tasks queue(like setTimeout) are execuated.



###################################################################################################################################################.

Q. Arrow function vs regular functions - 
ans: Both functions and regular functions are two ways to defined  functions in javacript, and they have some key differences.

The main differnce  between arrow function and  regular function
is   that arrow function does not have their own this contex.Instead , they inherit this from the surrounding lexical scope, which can be useful in certain situation.


###################################################################################################################################################.

Q. prototypes and inheritance in javascript: 
 ans: in javascript , prototypes and inheritance are core concept  that enables object to share properties and method, promoting  code resuse and modularity.


 1. Prototypes: Every Javascript object has an internal property called [[prototype]], whcih refers to another object. This mechinism allows an object to  inherience propertiese and  method from another object.

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
Copy code
function.call(thisArg, arg1, arg2, ...)
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

// Using call to borrow fullName method from person
person.fullName.call(person2);  // Output: Jane Smith
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
Feature	call()	apply()	bind()
Invocation	Immediately invokes the function	Immediately invokes the function	Returns a new function (does not invoke immediately)
Arguments	Passed one by one	Passed as an array	Passed one by one (or partial application)
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
 ->light riith 
 -> for data interchange format
 -> text based
 -> language indepent

################################################################

what it the purpose of array splic method ?
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
