# General

* setup of projects:
  * git clone
  * check if the environment is properly setup
  * install dependencies
  * run tests, build, and lint to make sure everything is working
* Component Styling
  * the consumer of the component doesn't really care about the implementation details of how styling is done. The consumer specifies some props and options. The component figures out how to do it. 
* Ref
  * it's created with React.useRef
  * ref attribute is a React specific attributed. It takes an object and React will set the DOM element to a property in this object
* Lifting state
  * when data needs to be used in siblings components, move it to the first common ancestors \(parent component\). Then the parent component holds the current value and passes callback functions to the child components update the state.
* Colocating state
  * State should be as close as possible to where it's used. If a piece of state is only needed in one component, it should be local. It helps with maintenance and performance. 

