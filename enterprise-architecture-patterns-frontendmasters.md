---
description: 'https://frontendmasters.com/courses/enterprise-patterns/'
---

# Enterprise Architecture Patterns - FrontendMasters

Iron Triangle of Programming:

* Handling of state
* Flow of control: communication
* Code volume

How do I manage state, communication \(flow of control\) with the least amount of code possible.

**The Axis of Evil**

Can I **know** the result of this code at all times?

Can I **reuse** this code? &gt;&gt; portable

Can I **test** this code? &gt;&gt; testable

"It’s impossible to write good test for bad code"

Friction from writing tests comes from having not testable code

* Hidden State
* Violating the SRP
* Nested logic
* Time

How to solve them: dependency injection + extract method

Always move code to be fine-grained code. Little functions doing specific things.

**4 elements of programming**

1. Describing things -&gt; Data structures \(nouns\)
2. Performing actions -&gt; functions \(verbs\)
3. Makings decisions -&gt; conditionals
4. Repeating via iteration -&gt; iterators
5. Time

**Observables**

Communicate state over time \(Flow of control\)

Encapsulate, transport, and transform data

Communicates state over time

Observables combine two patterns: iterator and observer

Value consumption for observable are push

|  | single | multiple |
| :--- | :--- | :--- |
| Pull | function | enumerable |
| push | promise | observable |

|  | Single | multiple |
| :--- | :--- | :--- |
| Synchronous | Function | Enumerable |
| asynchronous | promise | Observable |

Micro level: axis of evil

Meso level: feature complexity

Macro level: time domain, async programming. Observables to manage flow of control

**Distributed Complexity**

