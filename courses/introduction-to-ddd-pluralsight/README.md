---
description: 'https://www.pluralsight.com/courses/fundamentals-domain-driven-design'
---

# Introduction to DDD - Pluralsight

* Justify the need of DDD. Business need to be complex enough
* Goals for learning about the domain:
  * understand client's business
  * identify processes beyond project scope
  * look for subdomain we should include
  * look for subdomains we can ignore
* identify subdomains
* Takeways from the customer conversation
  * get on the same page with the domain expert
  * customer get's a better idea of their own business by describing how they work
  * Avoid speaking in programmer terms
  * focus is on how the domain works, not how the software works
  * make the implicit knowledge of the domain expert explicit
* Bounded context
  * define a strong boundary around the concepts of each model
  * ensure mode's concepts don't leak into other models where they don't make sense
  * clearly separate contexts: namespaces, folders, projects, code base, teams, etc
  * Subdomain: is a problem space concept
    * a room that needs to be covered with carpet
  * Bounded context: is a solution space concept
    * cover the room with carpet from wall to wall \(subdomain and bounded context match\). Or use area rugs that solve the problem but don't cover 100% of the room \(subdomain and bounded context don't match\)
  * Context Maps
    * Demontrates how bounded contexts connect to one another while supporting communication between teams
    * shared kernel
      * shared concerns between bounded contexts/teams
    * translation errors will manifest as bugs when the language of domain experts and the language of developers don't align
    * "A project faces serious problems when its language is fractured" - Eric Evans
* Summary
  * Problem Domain: the specific problem the software you're working on is trying to solve
    * Core Domain: the key differentiator for the customer's business -- something they must do well and cannot outsource
    * Subdomains: separate applications of features your software must support or interact with
    * Bounded contexts: a specific responsibility, with explict boundaries that separate it from other parts of the system
    * Context mapping: the process of identifying bounded contexts and their relationship to one another
    * Shared kernel: part of the modeal that is shared by two or more teams, who agree not to change it without collaboration
    * Ubiquitous language: the language using terms from a domain model that programmers and domain experts use to discuss that particular sub-system

### Elements of a Domain Model

* Entity: a domain class with an identity for tracking
* Context: a bounded context defines the scope and buondaries of a subset of a domain
* "the domain is the heart of the business software"
* domain is about the behaviour 

#### Identifying events leads to understanding behaviour

* event storming, cf
  * past tense
* event modeling
  * eventmodeling.org
* Anemic domain model
  * focus on attributes
  * in domain model this is an anti-patern
  * how to identify them
    * looks like the real thing with obejcts named for nouns in the domain
    * little or no behaviour
    * equate to property bags with getters and setters
    * all business logic has been relagate to service objects
* Rich domain model
  * focus on behaviour and business logic of the domain

#### Understanding Entities

* 2 types of objects
  * defined by an identity \(Entity\)
  * defined by its value
* Vaughn Vernon
* Classes which id is a int, it means that they're created/used for CRUD
* Classes with id is a GUID, it means they're designed with DDD in mind
* message queues are used to synchronize data between bonded contexts

Resources

* Jimmy Bogard

### Value objects

* defined by its value
* used to measure, quantify, or describe a thing in the domain
* identity is based on composition of values
* immutable
* compared using all values
* no side effects
  * it can have methods that compute things, but don't change the state of the value object or any other state
* examples: String, dates objects, 
  * DateTimeRange
    * Start, end
    * DateTimeRange\(start, end\)
* instead of using ints or Gui ids as identifiers, use a value object class. Like: ClientIdValueObject. This could store the value in int or a gui id. It doesn't matter. The benefit is that it creates a strong type and avoid passing the wrong values in our code. For example, we wouldn't be able to pass a patient in in place of a client id becuase the type would be different
* generic logic
* Entities
  * methods are higher-level than value objects, more like use case communication
  * orchestration
  * if all the properties of an entity are primitive types, maybe they can grouped together in a value object

### Domain Services

* orchestration for operations that require several entities or object values
* orchestration of workflow
* not a natural part of an entity or value object
* defined interface in terms of other domain model elements
* stateless, but may have side effects
* lives in the core of the application
* Services in different layers
  * UI and App
  * Domain
  * Infrastructure

### Tackling Complexity with Aggregates

#### Data Complexity

* how to limit data complexity
  * limit by-directional relationships in the data model
  * use aggregates
* Aggregates
  * One or more entities that change together
  * it must have a root, which is the parent of all aggregates
  * an aggregate root can be copmpose of a single aggregate
  * it enforces data consistency and follow ACID
  * root
    * maintain invariants
    * how to know an object should be an aggregate root
      * if deleting the object causes a cascade of deletes, then it should be an aggregate
      * does it make sense to have this object detached from its parent?
* default to one-way associations in the models
* in relationship references, use real object references not ids of objects
* object relationshipts are not the same as data relationships
* instead of having navigational methods in non-root objects in an aggregated, have an id of the root. It reduces confusiong with ORMs and the complexity in the model
* invariant
  * Example: speed of light, 
  * business rules that must be true for the system to behave correctly. Example: end data must be after start date

