# Module 1 - Web Application & Software Architecture



## Things to keep in mind

- single points of failure
- performance bottlenecks
- how the app/system will be used?



## Different Tiers in Software Architecture

### What is a tier?

It's a local and physical separation of components in an application or a web service. A components could be a database, backend application server, user interface, messaging, caching, etc

### Single tier

- All parts of the app run in the same machine
- Example: MS Office, PC Games, image editing
- Advantages
  - no network latency which leads to better peformance
  - data is easily accessible in teh machine
  - data safety because is not tranfered over the wire
- Disadvantages
  - Business cannot make changes to teh app, no updates, patches, etc
  - code is vunerable to reverse engineering and tweaking
  - app performance and look and feel may be inconsistent because it depends on user's machine capacity

### Two-tier application

- Client-server 
  - Client: user interface and business logic
  - Backend: database
- Examples: a to-do list app, planner, productivity app, online browser, app-based games
- Advantages:
  - less network calls for handling business logic
  - less cost with servers
- Disadvantages
  - code is vunerable

### Three-Tier Applications

- UI, Application Logic, and database are in different machines

### N-Tier Applications

- an application that has more than 3 tiers
- Components: cache, message queues, load balancers, search servers, etc
- Why we need many tiers: Single Responsibility Principle & Separation of Concerns

### Single Responsiblituy Principle

- give only one responsibility to a component and let it execute it well
- different tiers help to keep the single reponsiblity principle

### Separation of concerns

- It means: be concerned with your work only and stop worrying aobut the rest of the stuff

- Keeping the componenets separate make them reusable
- Loosely coupled components make them easier to scale

### Layers vs Tiers

Layers are conceptual organization of code.

Tiers are physical separation of components.



## Web Architecture

### Client-Server Architecture

- Request-response model

  - client sends request to a server that responds with data

    

- Building-block of the web

- It's different from peer-to-peer

- Client

  - UI
  - Thin client: no business logic
  - Think client: UI + business logic (some or all)

### REST

- A REST API is an aPI implementation that adheres to the rEST architectural constraints.
- REST responses can be cached
- API Gateway
  - it just means that an API wraps business logic and other services. It acts as an interface with the outside world.

### HTTP Push & Pull

HTTP PULL

- default mode
- client sends a request and server replies with a response
- the client pulls data from the server
- Implementation: AJAX

HTTP PUSH

- Client sends request only once. After that server will send updates to the client whenever something new happens.
- Implementation: Ajax Long polling, Web Sockets, HTML5 Event Source, Message Queues, Streaming over HTTP
- TTL: Time to Live
  - from 30 to 60 secs
  - the client sends a requests and if the server doesn't respond within the TTL, the client will break the connection. This helps the servers to not have many open connections. 
- Persistent Connection
  - it remains open between client and server, behiond the TTL 
  - Heartbeat interceptors: blank request responses between the client and the server to prevent the browser from killing the connection
  - This can consume a lot of resources but may be justifiable depending on the use case.A game for example would make sense.
- HTTP Push Based Technologies
  - Web Sockets
    - two-way communication
    - TCP
    - use case: messaging, chat applications, real-time social streams, games
  - Ajax Long Polling
    - the server holds the response until it has an update to send
    - Pros: fewer number of requests compared to regular polling mechanism
    - use case: simple async data fetch
  - HTML5 Event-Source API and Server-Sent Events
    - The server push messages (events) to the client
    - client creates connection on initial request
      - gets rid of blank request-response cycles
    - the server has to support Server-Sent Events and the HTML5 Event-Source API has to be available
    - one direction only
    - use cases: Twitter feed, displaying stock quotes, real-time notifications
  - Streaming over HTTP
    - large data sets over HTTP
    - Use with JavaScript Stream
    - use case: multimedia content (images, videos, audio, etc)



## What is Scabability?

- It's the ability of an application to handle increased workload without sacrifising the latency
- The response time of an application should not increase if the number of users increase

### What is latency?

The amount of time a system takes to respond to a user request

### Vertical Scalability (scalling up)

- Adding more power to a server. Example: more memory.
- Pros:
  - no code changes required
  - less cost to administer the system
- Cons:
  - there's a limit to what we can increase in a single server
  - availability risk. There's still a few servers to respond to users. 

### Horizontal Scalability (scalling out)

- Adding more hardware to the resources pool
- Pros:
  - dynamically scale in real-time
  - no limit on increasing the capacity of the system
- Cons
  - The code needs to be refactored to be stateless. Because where the code is running, a node, can be destroyed anytime. If it happens and the code has data/state, then the state is lost. Instead, the code has to use some external storage, like a key-value store.

### Cloud elasticity

- The ability to scale up and down as needed. 
- Props:
  - saves money
  - apps can have high availability. Even if one server node fails, another one can server the users

### How to chose a scalability approach

If the app is not expecting high traffic or high fluctuations in trafic, vertial scalability may be sufficient. For example, an internal tool, a utility app, etc.

If the app is expected to receive high traffic and/or is public-facing, like a social media app, then horizontal scalability will be important.

## Primary Bottlenetcks that hurt the scalability of our application 

- Single database for a bunch of servers
  - Make use of partitioning, sharding, multiple database servers
- Application architecture
  - failing to use asynchonous processes and modules. For example, notifications and messagingis don't need to be dealt with synchronously. They can be processed by messaging servers asynchronously.
- Not using caching in the application wisely
  - can be used in several layers
  - example, in front of a database or a server
- Inefficient configuration and setup of load balancers
  - Too many or too few will have a negative impact
- Adding business logic to the database
  - adds an extra load on the database
  - just don't do it
- Not pickung the right database
  - Relational database: transactions and strong consistency
  - NoSQL: horizontal scalability on the fly, no strong consistency
- Code level
  - tightly coupled code
  - unecessary work
  - not paying attention to Big-O

## How to improve and test the scalability of our application?

- Profilling
  - How to profile client-side React/JS apps?
- Caching
  - Cache all static content
  - Hit the database only when required
  - try to serve all requests from the cache
  - use a write-through cache (???)
- Data compression
  - Store data in the compressed form
  - compressed data travels faster
- Avoid unnecessary client server requests

### Testing the scalability of our application

- Stress and load tests are performed and different paramters can be used to measure the system:
  - CPU usage
  - network bandwidth consumption
  - throughput
  - number of requests processed within a certain time
  - latency
  - memory usage
  - End-user experience when the system is under heavy load



## What is high availability (HA) ?

It's the ability of a service to be online despite of infrastructure failures.

Mission-critical systems need to be online all the time, for example: aircraft systems, hospital servers, spacecrafts, etc.

To be highly available a system needs to be fault-tolerant and its components are made redundant.

### What is fault tolerant?

It's the ability of a system to stay up despite taking hits.

It means that parts of a system may go down but the whole application will still be online and working (fail soft)

### Designing a highly available fault-tolerant service - architeture

Break down the whole services into micro services that talk to each other, with the user interface, and each has its own database.

Each micro service owns different features of the app

Pros of micro services:

- easier management
- easier development
- ease of adding new features
- ease of maintenance
- high availability

## Redundancy

### Redundancy - Active-passive HA mode

There're duplicated components and extras ones that are ready to be put in use in case some active instance goes down. It's the fail-safe backup mechanism.

### Getting rid of single points of failture

Distributed systems got rid of the single point of failure in monolitc applications. The nodes work together to build and keep a synchronous application state.

On the application level, bottlenecks are the single point of failure. It's important to identify them with performance tests and get rid of them.

## Replication

### Replication - Active-active HA mode

All nodes are available and taking the load of the system. if some node goes down, the load is re-distributed to the remaining active nodes.

### Geographical distribution of workloaad

Pros:

- low latency for users
- less susceptible to natural disasters, regional power outages, big-scale failures
- it avoids the single point of failture of a data center

User multi-platform cloud providers make business even more available because if one cloud provider goes down, there's another one to use. 

## High Availability Clustering (or fail-over cluster)

It's a set of nodes running together anr coordinated by a central node. They're connected by a private network called heatbeat network, that monitors their health. There's a coodination service, like Zookeeper, that ensures there's a single state shared across all nodes.

Techniques to ensure HA:

- Disk mirroring / Redundant Array of Independent Disks (RAID)
- redundant network connections
- Redundant electrical power

## DNS

DNS is a system that converts domain names to IP addresses, so we don't have to remember the IP addresses of websites and machines on the internet.

Accessing a website using an URL is called DNS querying.

DNS is made of 4 things:

- DNS Recursive nameserver (DNS Resolver)
- Root nameserver
- Top-Level Domain nameserver
- Autoritative nameserver

User enters URL in the browser -> browser sends request to the DNS Resolver -> DNS resolver sends a request to the Root nameserver to get the address of the Top-Level domain nameserver (e.g. ".com"). -> DNS resolver sends a request to the Top-Level domain nameserver to get details of the domain name -> the top-level domain name server returns the IP address of the domain name server requested (e.g., amazon.com domain name server) -> the DNS resolver sends a query to the Authoritative nameserver, which returns the IP address of the website -> the DNS resolver caches the data and replies to the client -> the browser gets the IP address of the webite and make a call to it to get its content

DNS resolver is managed by ISPs

### Limitations of DNS load balancing

- It does not take into account the load on the servers to which the request will be routed to
- the IP addresses are cached by the client's machine, so there's a chance that the user may hit a machine that is not online
- Pros: easy and less expensive way of setting up load balancing on services



## Microservices



## Monolitic Architecture

Cons

- as the team grows, it becomes hard for all developers to use the same codebase
- as the app grows, the compile and test runtime increases
- Changes in one part of the app, may affect other unrelated parts. More regression test is needed
- During release, everyone has to stop until the code is deployed
- Code written by a team, may need approval from another team before going to production

## Microservices Architecture 

### Pros of microservice architecture

- No single points of failure
- Use different technologies
- Independent and continuous deployments
- Faul isolation
  - when something breaks, it's easy to identify and isolate the problem

### Cons of microservice architecture

- Complex management 
  - It needs dedicated resources (software and people) for monitoring and management 
- No strong consistency

### When to use a microservice architecture

When the use cases are complex and traffic is expected to grow exponentialy.

- Keep things simple
- Thoroughly understand the requirements
- build only when needed. Evolve iteratively. 



## Message Queue

- FIFO
- it's a priority queue
- facilitates asynchronous behavior
  - Allows modules to communicate with each other without disturbing their primary tasks
  - facilitate cross-module communication
    - this is important in services-oriented architecture and microservices
    - it allows communication in an environment with different software in different languages
  - temporaty storage for messages to be processed
  - helps to run background processes, tasks, batch jobs
- use cases:
  - notification systems
  - user confirmation after sign up. For example, user signs up for a service and service has to send an email with confirmation to the user. 
- entities: queue, producer, consumer
- as the message goes through the queue, we can add business rules to process it: message acknowledgment, retry failed messages, etc

### Pub/Sub Model

- Multiple consumers receive the same message sent from a single or multiple producers
- Exchanges
  - steps that a message go through in the queue
  - have type, for example: direct, topic, headers, fanout
  - messages can have different exchange types
  - fanout exchange is the same as broadcasting the message
  - Binding: the relationship between the exchange and the queue

### Point-to-point model

- The message from one producer is consumed by one consumer

### Messaging Protocols

- AMQP Advanced Message Queue Protocol
- STOMP Simple or Streaming Text Oriented Message Protocol
- What is used to implement these protocols: RabbitMQ, ActiveMQ, Apache Kafta

### Notification Systems and Real-Time feeds with Message Queues

- Pull-based approach: a user creates a post that is persisted in the db. When a friend(s) of this user goes online, query data from db for all new updates from every friend connection. And keep doing this. 
  - Cons: lots of bandwidth and resources are required
  - Pros: simpler?
- Push-based approach: a user creates a post. The post handled with a distributed transaction, i.e., one transaction persist the post in the db and another one sends the post to a message queue. The message  queue will send the post to all subscribers of this users.
  - Pros: less resource consumption
  - Cons: more complex setup?







