# JavaScript Overview

What is JavaScript?

Our first definition was:

```
"Javascript is a high-level object-oriented, multi-paradigm programming language."
- Jonas Schmedtmann.
```

But here's another one:

```
"Javascript is a high-level, prototype-based object-oriented, multi-paradigm, interpreted or just-in-time compiled, dynamic, single-threaded, gargabe-collected programming language with first-class functions and a non-blocking event loop concurrecy model."
- Jonas Schmedtmann.
```

It says a lot.

Let's break the information into small pieces and talk about them.

## High-level

Computers need hardware to work. The low-level languages manually handle resources. "C" is a low-level language. The high-level languages do not manually handle resources because they work with abstractions that take that work from the user. "Javascript" and "Python" are high-level languages.

## Garbage-collected

The "Garbage Collector" is an algorithmn inside the Javascript Engine that handles computer resources by automatically "cleaning" the memory so we don't have to.

## Interpreted or Just-in-time Compiled

Computers only understand 1 and 0.

Every program must convert themselves to 1 and 0 so machines understand it. That means every code should be machine-translated to 1 and 0. Javascript handles that internally in its Engine.

## Multi-paradigm

A paradigm is an approach and mindset of structuring code, which will direct your coding style and technique.

There are three popular paradigms:

1. **Procedural programming**: it's organized code with some functions in between. What we have been doing so far.
2. **Object-oriented programming** (oop)
3. **Functional programming** (fp)

Javascript allows all three paradigms above.

It's the user's choice to pick one that fits best.

## Prototype-based object-oriented

Take the arrays we create in Javascript, for example.

It "copies" itself from an Array Prototype already created and available. This prototype has its own properties and methods. Our created array inhrerits these properties and methods from the prototype.

More on this later.

## First-class functions

Functions are treated as variables. We can pass them into other functions as parameters, and return them from functions. 

*This allows functional programming to happen.*

## Dynamic

Remember dynamic data types? Javascript is a dynamically-typed language. The data type of a variable can be automatically changed.

## Single-threaded

*A thread is a set of instructions that is executed in the computer CPU. It's where our code is executed in the machine processor.*

"Concurrency model" is how the Javascript Engine handles multiple tasks happening at the same time.

Why would we need that the "concurrency model"?

Because **Javascript runs in one single-thread**, so it can only do **one thing at a time**.

So, what about a long-running task? A task that needs a really long time to conclude itself?

Sounds like it would block the single thread. However, we want non-blocking behaviour! We achieve that by using an **event loop**.

By using an event loop, it takes long-running tasks and **executes them in the "background" and puts them back in the main thread once they are finished**.

## Check the definition again

Should make sense now.

```
"Javascript is a high-level, prototype-based object-oriented, multi-paradigm, interpreted or just-in-time compiled, dynamic, single-threaded, gargabe-collected programming language with first-class functions and a non-blocking event loop concurrecy model."
- Jonas Schmedtmann.
```