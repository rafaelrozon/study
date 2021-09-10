# Clean Architecture: Patterns, Practices, and Principles \(Pluralsight\)

### Intro

* What is software architecture?
  * High level
  * structure
  * layers
  * components
  * relationships
* Levels of architectural abstraction \(from high level to low level\):
  * System
  * sub-system
  * layers
  * components
  * classers
  * data and methods
* Bad Architecture
  * complex
  * incoherent
  * brittle
  * not testable
  * rigid
* Good architecture
  * simple
  * understandable
  * flexible
  * emergent
  * testable
  * maintainable
* Clean architecture is designed for the inhabitants \(developers and end users\) of the architecture, not the architect or the machine
* Why
  * Focus on the essential
  * Build only what is necessary
  * Optimize for maintainability
* Context is king
* all decisions are trafeoffs
* align with business goals

### Domain-centric Applications

* Domain-centric architectures
  * Hexagonal Architecture
  * Onion Architecture
  * Clean Architecture
* Pros
  * focus on domain
  * less coupling
  * Allows for DDD
* Cons
  * change is difficult
  * Requires more thought
  * Initial higher cost
* Project Structure
  * domain: has aggregate roots, value objects

### Application Layer

* What are layers?
  * levels of abstraction
  * single-responsibility
  * isolate roles and skills
  * multiple implementations
  * varying rates of change
* Application Layer
  * implements use cases
  * high-level application logic
  * knows about the domain
  * no knowledge of other layers
  * contain interfaces of its dependencies that expect other layers to provide
* Inversion of control \(dependency is in the inverse direction of flow of control\)
  * indenpendent deployability
  * flexible and maintainable
* Why use an application layer
  * Pros
    * focus on use cases
    * easy to understand
    * follows DIP \(dependency inversion principle\)
  * Cons
    * additional layer cost
    * requires extra thought
    * IoC is counter-intuitive
* 
