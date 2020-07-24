# Problems & Solutions

**Team not completing tasks in the sprint**

1. Have a design session before grooming.
   1. Reason: provide better estimate by understanding better the problem or task
2. Review stories at least a couple of times
3. Break stories in decoupled sub-tasks
4. Compare the velocity from previous release and pull in the same amount

tags: \#team \#tasks \#estimation



**Remembering design decisions**

**Reset component local state when global state changes.** 

Example: a React component that has a local state, receives its initial props from the Redux store, and should be reset when an API call fails. 

Solution: dynamically create a key for the component and updated it when an error happens. An error count can be used to dynamically create the key

tags: \#stateManagement \#react





