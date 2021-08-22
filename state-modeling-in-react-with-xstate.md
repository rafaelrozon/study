---
description: 'https://frontendmasters.com/courses/xstate-react/'
---

# State Modeling in React with XState

Context

* data that doesn’t fit into a finite state.
* "Infinite" state
* It’s changed with assign function

When the target field of a transition is undefined, the machine continue on the current state. It may be useful to change the context without changing the state

 Don’t add data in the machine that can be derived from the machine itself. Like UI logic, if it can be derived from the machine, keep it out of the machine.

Eventless transitions

* How to have a dynamic initial state? Answer: use an eventless transitions
  * Define an initial state like unknown. Then in the unknown state have a "always" transition list. Each item in the list can have guards that will move the state machine to the next dynamic state
* Careful to know get into a infinite loop

Sharing machine state with multiple components

* Create a React context
* Add an interpreted machine to the context \(service\)
* get the service from the context
* Pass the service to the useService hook

How to make a transition forbidden

* Set it’s v value to undefined
* 
Side-Effects

* Actions
* Invoking actors
* Spawning actors

Things that can be invoked:

* Promise
* Callback
* Observable
* Another machine
* 
State machine describes the behaviour of one actor.

An actor-model system describes the behaviour of how actors talk to each other.

Learn how to draw sequence diagram.

Context should be treated as immutable

