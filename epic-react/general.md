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
* useEffect
  * no dependency array means "I depend on everything"
  * with empty dependency array means "I depend on nothing"
  * with dependency array filled means "I depend on this variable"
* When we create a component we are not imperatively making it render. React is the one responsible to decide when the component will be painted in the screen. Remember that writing `<MyComponent />` doesn't actually add the component to the DOM,  but invoke React.createElement.
* Lifting state
  * when data needs to be used in siblings components, move it to the first common ancestors \(parent component\). Then the parent component holds the current value and passes callback functions to the child components update the state.
* Colocating state
  * State should be as close as possible to where it's used. If a piece of state is only needed in one component, it should be local. It helps with maintenance and performance. 



Questions

1. Does useState always return a new reference of state and setState?
2. If I get an object as the state from setState and want to use it as a dependency of a useEffect hook is it going to call the useEffect every time or only when the object changes?

