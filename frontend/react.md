# React

## Dev Lessons

* When refactoring class-based components to functional components make a copy and work on the copy in order to have a reference.

## How To's

### **Reset component local state when props change.** 

Example: a React component that has a local state, receives its initial props from the Redux store, and should be reset when an API call fails. 

Solution: dynamically create a key for the component and updated it when an error happens. An error count can be used to dynamically create the key



