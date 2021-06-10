# How JavaScript Works Behind the Scenes

What is the JavaScript Engine and how is JavaScript translated to machine code?

## Introduction

In this file, we're going to build a deeper overview of JavaScript. Read the previous file, n. 11, to get the overview.

## 1. The Javascript Engine and Runtime

The JavaScript Engine is a program that **executes** JavaScript code.

Every browser has its own JavaScript Engine. The most famous Engine is the one from Chrome: the V8 Engine. These notes are taking it into consideration.

### JavaScript Engine

The Engine is made of two fundamental structures: the **Call Stack** and the **Heap**. The Call Stack is where our code is executed: and it executes the code using the execution context. The Heap is a data structure pool that contains all objects in memory. It's where the objects are stored.

How is it translated to Machine Code?

To answer that, we gotta review our notes on Computer Science.

### Compilation vs. Interpretation

**Compilation** is the process where the entire code is **converted to Machine Code at once** and written to a binary file that can be executed by the computer. So, there two steps: first, the code is compiled (a portable file is created); second, the code (now machine code) is executed. Sidenote: execution (step 2) can happen waaaay after compilation (step 1). Both steps get our program running.

**Interpretation** is the process where there is an **interpreter** that runs through the source code and **executes it line by line**. The code is read and executed at the same time. There's just one step now. Of course, code still needs to be converted to Machine Code but it is done and executed in one step. They are much slower than compiled languages.

JavaScript used to be an interpretation language. But now it is not: it's a "just-in-time" compilation language, which is a mixed option of compilation and interpretation. This is modern Javascript. The entire code is converted into machine code at once and then executed immediately. There are 2 steps here but with no portable file.

### Engine Executes JS

Four steps.

**PARSE -> COMPILE -> EXECUTE -> OPTIMIZE**

1. The first step is to **parse** the code.

Essentially, it means the engine reads the code and is parsed into an Abstract Syntax Tree (AST) data structure: each code bit is separated according to its own category (const, functions, keywords) and saved into a tree structure. *PS: this tree has nothing to do with the DOM, they're not related in any way*.

2. The second step is to **compile** the code.

In this step, you take the AST file and compile it to Machine Code. Then, this code is executed right away (third step).

3. The third step is to **execute** the code.

As soon as the AST file is compiled to Machine Code, it is then executed. Remember, Javascript Engine works with **just-in-time** compilation. This execution happens in the Call Stack. 

But let's dig a little deeper.

In order to make it all so fast, the file is compiled to an un-optimized version of Machine Code, so it can be executed right away. Then, it enters this cicle to optimaze the Machine Code... as it runs along. In the background, this code is optimazide and compiled again and again to an optimized version. It all happens during execution!

4. So, the fourth step is to **optimize** the code, as it is executed.

Just as seen above. This is what makes modern Engines so fast. All this happens in special threads that we can't access from code: completely separated from the main thread where we work in our code.

### Runtime in the Browser

The engine alone is not enough. We need the Web APIs (DOM, timers, fetch API, others) also.

Web APIs are functionalities provided to the engines... they are not part of JS. The JS gets access to the web APIs through the **global window object**. The Runtime is like a box: it contains everything related to JS that we need. 

What else do we need?

The **Callback Queue**.

This is a Data Structure that contains all the callback functions that are waiting to be executed.

For example, when we place an addEventListener in an HTML element on DOM. Suppose it waits for a "click" to happen ("onClick"). The "onClick" function is a callback function because it is waiting for an event to happen so it can be executed. The callback function is placed inside the **Callback Queue**. When the **Call Stack** (inside the Engine) is empty, the **Event Loop** takes the callback function *from inside* the **Callback Queue** and *places it inside* the **Call Stack** (inside the Engine).

The Event Loop is essential for the non-blocking concurrency model. It is a fundamental piece of JavaScript development.

*PS: The Runtime can also happen outside the browser, for example, in the Node.js. In this case, we say "Runtime in the Node.js". It's a bit differente because Node.js does not have a browser, so it does not have the Web APIs. Instead, we have "C++ bindings & thread pool".*

## 2. Execution Context and the Call Stack

Let's imagine our code just finished compiling and is now ready to be executed. What happens now?

A **Global Execution Context** (GEC) for top-level code is created.

Exactly **one** GEC is created per program. It is the default context created for code that is not inside any function.

Top-level code is *code outside functions*. In the beginning, only code outside functions are executed and it makes sense: code inside functions are executed upon calling the function. An execution context is an environment in which a piece of JavaScript is executed - it stores all the necessary information for some code to be executed.

After the creation of a GEC, the following step is the **execution of top-level code** inside global Execution Context (EC).

And the final step is **execution of functions and waiting for callbacks**. One Execution Context (EC) is created per function - for **each** function call, a new execution context is created.

### Execution Context (EC) in detail

What is inside an EC?

Items | Examples | In Arrow Functions
:----- | :-------- | :-------------------
Variable Environment | let, const and var declarations; functions; arguments objects | NO (to "arguments objects") and YES (to everything else)
Scope Chain | Basically consists of references to variables located outside of the current function | YES
"This" Keyword | More coming on this | NO

They are all created during the "creation phase" - right before execution. 

### Call Stack in detail

The Call Stack is the "place" where ECs get stacked on top of each other to **keep track of where we are in the execution**. 

## 3. Scoping and Scope in JS: concepts

Each EC has a variable environment, a scope chain and a "this" keyword.

### Concepts

**Scoping** controls how our programs' variables are organized and accessed. 

**Lexical Scoping** is how scoping is controlled by **placement** of functions and blocks in the code. This is influenced by where we write in our code. 

**Scope** is the space or environment in which a certain variable is declared: there is global scope, function scope and block scope.

**Scope of a variable** is the region of our code where a certain variable can be accessed.

They are all different things.

### Global Scope, Function Scope and Block Scope

Here's a table to remember.

Name | In details | Variables accessibility
:---- | :-------- | :----------------------
Global Scope | Top-level code; it resides outside any function or block code | Variables declared here are accessible *everywhere*
Function Scope | Also called local scope; it resides inside a function | Variables declared here are accessible only inside the function (not outside it)
Block Scope | Everything inside curly braces (for example, if block, for loop block, while loop block, etc.) | Variables declared here are accessible only inside block (but this only applies to let and const variables). In strict mode, functions are also block scoped

*PS: var variables only care about function scope and not block scope.*

### Scope Chain

The procedure to access a variable is called "variable lookup in scope chain" which, in turn, means that a particular scope has access to variables from all **outer** scopes. The reverse is not true, though. **Pay attention to this**.

You access the parent-scope related to current-scope but not the child-scope of current-scope.

Important to note: *```let``` and ```const``` are BLOCK-SCOPED while ```var``` is FUNCTION-SCOPED.* 

The Scope Chain has nothing to do with the **order** in which functions are called. The Scope Chain in a certain scope is equal to adding together **all the variable environments** of the all parent-scopes.

## 4. Variable Environment: Hoisting and TDZ

Remember: EC contains "variable environment", "scope chain" and "this keyword". This section is about variable environment - specifically on hoisting and the Temporal Dead Zone (TDZ).

How are variables created in JS?

Through hoisting. 

Hoisting makes some types of variables accessible/usable in the code before they are actually declared. Behind the scenes, the code is scanned for variable declarations, and for each variable a new property is created in the variable environment object.

What | Hoisted? | Initial Value | Scope
:--- | :------- | :------------ | :-----
Function declarations | YES | Actual function | Block scope (true for 'strict mode')
Var variables | YES | undefined | Function scope
let and const variables | NO - (technically yes but not in practice) | \<unintiallized>, Temporal Dead Zone (TDZ) | Block scope
Function expressions and Arrow functions | Depends if declared with var or let/const | Depends | Depends

The TDZ is the space from when the variable is called until it is actually defined in the code. Why have it? Because it makes easier to avoid and catch errors -> being able to access variables before declaration is a bad practice and should be avoided. It makes const variables actually work.

Why have hoisting? Because it made functions useful before actual declaration. The var hoisting is just a byproduct.

## 5. The "This" Keyword

Remember: EC contains "variable environment", "scope chain" and "this keyword". This section is about "this" keyword, a very special variable in JS.

What is it?

```this``` is a special variable automatically **created for every Execution Context** (EC), which *includes every function*. This special variable takes the value of the "owner" of the function in which ```this``` keyword is used.

The value of "this" keyword **is NOT** static.

It changes.

It depends on **how** the function is called. Its value is **only assigned** when the function **is actually called**. This is very important.

So, how can a function be called then? Because this is important.

There are four ways.

How to call a Function| Meaning | ```this``` keyword
:-------------------- | :------ | :-------------
Method | A function is called inside an object, because it's an object value | ```this``` -> points to the Object that is calling the method
Simple function call | Not attached to any object | ```this``` -> points to ```undefined``` in case of 'strict mode'; or it points to ```window``` (in the browser)
Arrow functions | Not a way to call functions but important to mention | ```this``` -> points to surrounding function. They don't use the ```this``` keyword themselves, so the ```this``` keyword refers to surrounding function (lexical this)
Event Listener | The reaction to an event | ```this``` -> points to DOM element that the handler is attached to
```new, call, apply, bind``` | More coming in next notes | More to come

**Important to note**: ```this``` does not point to the function itself and does not point to its variable environment.

You should never use an arrow function as a method. Precisely because of errors on "this" keyword.

## 6. Primitive Types vs. Reference Types (Objects)

This can cause a lot of confusion. It's important to understand how primitive types and reference types are stored in memory because they are radically different.

Remember the Engine? It consists basically of two important structures: the Call Stack and the Heap.

**Primitive types are stored in the Call Stack**. The variable points to an address in memory which, in turn, stores a value. 

When we create another variable and replicates the first value to it, both variables point to the same address in memory. If we change one variable's value, then this variable will now point to another address in memory that holds the new value. The other variable will keep pointing to the previous memory address.

**Reference types (objects) are stored in the Heap**. The object points to an address in memory which, in turn, holds a value. *This value is a reference to a location in the Heap* - that's why we call it "Reference" Types. But see? There's two steps here.

When we create another object by replicating a previous object to this new one, both objects point to the same address in memory which, in turn, points to a specific address in the Heap. If we change anything inside this object, regardless in which pointer (or name object), **the change is done in the Heap**. And it's only ONE object in the Heap, with two pointers to a memory address... which in turn points to this ONE object in the Heap.

That's why if we change an object property, it changes *apparently* in both objects. That's because it's only one object but two pointers to the memory address in the Call Stack. The value in this memory address references to an address in the Heap *to the actual object stored in memory*. The object itself is not replicated, it's the same one, it's only one. The pointer is replicated. See the difference?

### How to copy an object

If you want to copy an object to create a new one, you should use the ```Object.assign({}, originalObject)``` function.

Check out the example below.

```javascript
// Original object is 'john'
const john = {
    firstName: 'John',
    lastName: 'Smith',
    age: 35,
};

// Let's copy the 'john' object
const johnCopy = Object.assign({}, john);

// Only NOW we can now change a property value (lastName) without
// affecting the original Object (remember it would be the same object)
johnCopy.lastName = 'Jones';

console.log('John Last Name: ', john.lastName);             // > Smith
console.log('JohnCopy Last Name: ', johnCopy.lastName);     // > Jones
```
But, beware: **this Object.assign function only makes a shallow copy, not a deep clone**. To put this simply: if we had an object inside an object... it would not work. It would only make an actual copy on the first level (outer object).