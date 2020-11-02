# React Fundamentals

JSX

* only expressions can be used in {} when in JSX because expressions get evaluated to a value and the {} are used for interpolation. So, what is inside {} becomes the assignment to a variable or the input to a function
* React.createElement creates React components but functions that return JSX don't
* Why React components need to start with upper case letter: the JSX specification says that anything that starts with angle brackets and an uppercase letter should be treat as a reference to a variable in scope. Babel, for example, will identify this specification and look for a variable in scope that matches the name of the component, otherwise, it would use the name as a string. 



Links

* [https://developer.mozilla.org/en-US/docs/Web/API/Document\_Object\_Model/Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
* [https://javascript.info/modifying-document\#insertion-methods](https://javascript.info/modifying-document#insertion-methods)
* [https://ui.dev/imperative-vs-declarative-programming/](https://ui.dev/imperative-vs-declarative-programming/)

