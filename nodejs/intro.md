# Intro

### What is NodeJS?

* Server-size JavaScript
* Scripting
* Environment to run JavaScript outside a browser
* Open-source runtime
* Built on Chrome's V8 JavaScript engine
* Created by Ryan Dahl in 2009 \(follow him\)

### What is NodeJS good for?

* Tooling: build, automation, webpack, etc
* API's: REST, GraphQL, sockets, etc \(because of high concurrency\)
* CDNs
* Sharable libraries: npm, yarn, etc
* Desktop Applications: ElectronJS
* IoT

### Installation

* Use nvm \(node version manager\)

### How to evaluate NodeJS code:

* REPL: just type the word node in the terminal 
* CLI executable:  `node path/to/file.j`

### Globals

* process: info about the environment the program is running in
* require: function to find and use modules
* \_\_dirname: current directory path
* module: info about the current module and methods to make it consumable. Everything in Node is a module.
* global: don't use it. Unless extremely necessary.

### Modules

* Module is encapsulated code
* Node will wrap each file in a module
* Default is CommonJS



References:

* [https://frontendmasters.com/courses/node-js](https://frontendmasters.com/courses/node-js/what-is-node-js/)



