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
  * an aggregate root can be copmposed of a single aggregate
  * it enforces data consistency and follow ACID
  * root
    * maintain invariants
    * how to know an object should be an aggregate root
      * if deleting the object causes a cascade of deletes, then it should be an aggregate
      * does it make sense to have this object detached from its parent?
* default to one-way associations in the models
* in relationship references, use real object references not ids of objects
* object relationshipts are not the same as data relationships
* instead of having navigational methods in non-root objects in an aggregated, have an id of the root. It reduces confusion with ORMs and the complexity in the model
* invariant
  * Example: speed of light, 
  * business rules that must be true for the system to behave correctly. Example: end date must be after start date
* Recognizing signs of a misidentified aggregate
  * cross-aggregate invariants should not be enforced by any one aggregate
    * use a domain service instead
    * possible red flag about the model
* Aggregate tips
  * they're not always the answer for complexity
  * aggreagates can only connect by the root, i.e., members of an aggreagate can only communicate with the root of another aggregatate
  * don't overlook using foreign Keys for non-root entities
  * too many foreign keys to non-root entities may suggest a problem
  * aggregates of one are acceptable
  * rule of cascading deletes
* Key takewawys
  * avoid big ball of mud models
  * break the model up into aggregates
  * an aggregates represents a graph of objects in a transaction
  * aggregates encapuslate business rules and invariants
  * default to one-way relationships when modeling associations
  * don't feat evolving the design of your aggregates as you learn more about the domain



### Repositories

* definition: an abstraction your domain model uses do define what persistence needs it has
* only aggregate roots can use repositories?
* manage the lifecycles of objects
* benefits
  * common abstraction for persistence
  * promotes separation of concern
  * communicates designs decisions
    * controls access
  * enables testability
  * improved maintainability
* Guides & tips
  * think of it as an in-memory collection \(an illusion of a collection\)
  * use a global/known common access interface
  * create custom methods for custom queries
    * but be careful to not have lots of custom queries, use specs for that instead
* use repositories for aggregate roots only
* the client focuses on the model repository on persistence
* usual problems with repositories
  * N+1 Query errors
  * inappropriate use of eager or lazy loading
  * fetching more data than required
* Profiling the database can help identify if repositories have problems
* Generic Repositories
  * trade-offs
    * if the generic interface has a delete method, but some repository should not be deleted, then it could be a problem. Maybe use a generic interface but don't implement the methods not required
    * use a marker interface to avoid client code to use a repository with a non-aggregate root
* Query repositories vs command repositories
  * CQRS
  * splitting repositories between read and write help to keep repositories small
* Specification
  * specify the state of an objects
  * used in 3 ways: validation, selection & querying, creating for a specific purpose
  * "Create explicit predicate-lie Value Objects for specialized purposes. A Specification is a predicate that determines if an object satisfies some criteria", Eric Evans
  * bool isSatisfiedBy\(object someObject\)
  * Benefits
    * names classes via ubiquitoues language
    * reusable
    * separate persistence from Domain Model and UI
    * keep business logic out of persistence layer and db
    * help entities and aggregates follow the SRP
  * each specification is a value object and should be immutable



### Domain Events and Anti-corruption layers

* domain events and anti-corruption layers help to decouple the domain from other parts of the app
* anti-corruption layers: translators between bounded-contexts and legacy parts of the app
* domain events:
  * alert that some activity has happened
  * state changed
  * encapuslated as objects
* identifying domain events
  * "if that happens", "notify user when", "inform the user if"
  * represent the past
  * typically, they're immutable
  * name the event using the bounded context's ubiquitous language
  * use the command name causing the event to be fired
  * only create events when there's behaviour that needs to occur when the event happens and you want to decouple the behaviour from its trigger and the behaviour doesn't belong on the class that is triggering it
* Each event is a class
  * include when the event happened. Use past tense
  * include event-specific details
  * no behaviour or side-effects
* Hollywood principle: "don't call us, we'll call you"
  * use domain events to let other code \(application\) know of things that happend. Handlers in the app will listen \("we'll call you"\) for the events instead of having extra code \("don't call us"\) in the domain layer
* domain events should not fail. Don't write code that relies on exceptions thrown by event handlers
* Create base classes or Interfaces for Handler and DomainEvent
* the entity class has a field "events", as things happen events are added to the list, but are only dispatched in the repository after persistence is done
* side-effects are only triggered after persistence
* Integration Events
  * created and consumed beyond the domain, example Domain --&gt; UI App
* Anti-corruption layers
  * insulate bounded contexts
  * protect the domain from other systems and implementation details
  * it translates between bounded contexts and legacy app
  * simplifies communication between systems, like a fa/ca

#### UI

* Jimmy Nilsson
  * Developing core business applications with DDD and Microsoft .NET. TechEd NA 2013





