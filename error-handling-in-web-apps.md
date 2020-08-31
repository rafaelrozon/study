# Error Handling in Web Apps

* Use correct HTTP error codes
* Error responses should have enough information for the client app to decide what do to. For example \(modified\):

```text
{
    "status_code": 400,
    "error_code": E123,
    "message": "error.upload.file-type",
    "context": {
        "accepts": ["jpg", "png"],
        "received": "svg"
    }
}
```

* The API client should be able to handle error responses
* Create the API client and error handling before than anything else, so other parts of the app can be integrated with it. For example: error notifications, error tracking, logging, etc
* Proxy the console log to not leave log messages in production
* every time we had exception handling to a function we are adding extra paths through the code that need to be tested
* Don't swallow exceptions. At least log them.
* Use an error tracking service. 
* Have explicit returns especially in catch blocks
* Create specific routes for specific errors and have one controller to handle them. In the case of MVC apps. But the same could be applied on SPA.  

### Flow

user input &gt; run logic &gt; make API call &gt; API call fails &gt; update the state &gt; display error message &gt; user acknowledges error message &gt; clear the error state

The user acknoledgement is key, because we can use it to clear the state and avoid having a stale error state

### Strategies

* global error handling

### Breaking points

* network calls
* third-party libraries
* user input
* parsing of dynamic or external data



### Form Validation

* don't rely on strings to assert that validation has passed, but throw an error and catch it: 

{% embed url="https://gist.github.com/hypeJunction/81ef20612bd325ec38ccb71b2052f99d\#file-validator-js" %}

### Resources

Web Apps

{% embed url="https://itnext.io/graceful-error-handling-in-rest-driven-web-applications-d4209b4937aa" %}

{% embed url="https://alexandrempsantos.com/sane-error-handling-react-redux/" %}

{% embed url="https://itnext.io/centralizing-api-error-handling-in-react-apps-810b2be1d39d" %}

{% embed url="https://code.tutsplus.com/articles/writing-robust-web-applications-the-lost-art-of-exception-handling--net-36395" %}

{% embed url="https://dispatch.moonfarmer.com/redux-status-and-error-methodology-ec5c1f1634b7" %}



REST APIs 

[https://itnext.io/the-case-for-standardized-error-handling-in-your-web-application-6428ff60cc31](https://itnext.io/the-case-for-standardized-error-handling-in-your-web-application-6428ff60cc31)

