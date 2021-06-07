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
----- | -------- | -------------------
Variable Environment | let, const and var declarations; functions; arguments objects | NO (to "arguments objects") and YES (to everything else)
Scope Chain | Basically consists of references to variables located outside of the current function | YES
"This" Keyword | More coming on this | NO

They are all created during the "creation phase" - right before execution. 

## Call Stack in detail

The Call Stack is the "place" where ECs get stacked on top of each other to **keep track of where we are in the execution**. 

