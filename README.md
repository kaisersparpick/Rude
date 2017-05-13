# Rude

## What?

**Rude is a control-flow pattern with a rule-based dispatcher**. 

As a behavioural design pattern, it promotes [loose coupling](https://en.wikipedia.org/wiki/Loose_coupling), whereby control-flow is encapsulated within a *dispatcher*.
This dynamic model implements a non-branching strategy to handle complex conditions and to solve the problems that arise from the rigid static model of conditional control structures.

The participants in this pattern are
  - a dispatcher
  - a set of receivers
  - a set of commands
  
The pattern conforms to the [Separation of Concerns](https://en.wikipedia.org/wiki/Separation_of_concerns) principle of [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming). 

The `rules` for controlling the process flow can be completely separated and decoupled from the application code, and can also be dynamically generated and/or loaded from a datasource. Hence, the control-flow logic can be modified without changing the rest of the system. Therefore, this pattern also implements the [Open/Closed principle](https://en.wikipedia.org/wiki/Open/closed_principle).

**The Dispatcher**

The dispatcher is only concerned with the bookkeeping of command execution. When invoked, it dispatches a command/action to the receiver, which then executes it.

**The Receiver**

The receiver is only concerned with *how* to execute the commands, it doesn't know *when* or under what condition.




## When?

When do you need Rude?

Can you implement your conditions in the form of *simple*
 - if-then-else statements
 - switches
 - ternary operators? 

Then the answer is **NO**. 

Are your conditions nested (or deeply nested)? \
Are your conditions likely to change? \
Is your cyclomatic complexity index too high? \
Do you want to load the control-flow logic dynamically? \
Does your application need a way to store the state or position in a complex workflow?

Then the answer is **YES**.


## Why?

  - Rude allows for an on-demand execution of a chain of `dynamic if-then-else` statements - hereinafter referred to as `rules`.
  - The control flow is easy to manage and the logic can be modified by simply changing the callbacks in the `rules`.
  - The chain of condition checking can be exited or paused at any given point.
  - The position in the `rule` hierarchy can be stored and the execution resumed at a later stage by setting the `entry point`. 
  - Each `rule` is seen as a separate and *independent logical unit*.
  - Individual `rules` and groups of rules can be easily moved around.
  - `Rules` can be generated dynamically or loaded from a datasource. 
  - The dispatcher makes it possible to ditch the rigid static conditional model in favour of a considerably more flexible one.


## How?

1. First of all: clean up your code. Refactoring messy code with multiple nested conditional blocks usually involves the following techniques: 
    * Moving conditionals into seperate functions
	    * This also makes unit testing easy :)
    * Replacing conditionals with guard clauses or [subtype polymorphism](https://en.wikipedia.org/wiki/Subtyping)
2. Refactor your code so that your functions/methods represent *logical units*. 
3. Work out your `rules` and their hierarchy. Each rule must have a `Condition`, and can have a `Yes` (truthy) and a `No` (falsy) callback. 
4. Look at the **examples** and adjust them to your needs. 

## Examples

Although Rude is a *pattern*, you can find a few actual implementations here

  * [Rude.Net](https://github.com/kaisersparpick/Rude.Net) -- a C# implementation of Rude
  * [Rude.js](https://github.com/kaisersparpick/Rude.js) -- a JavaScript (ES6) implementation of Rude
  * [Rude.pl](https://github.com/kaisersparpick/Rude.pl) -- a Perl implementation of Rude
  * Python (soon)
  * Ruby (soon)
  * PHP (soon)
