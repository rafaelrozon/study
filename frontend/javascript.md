# JavaScript

## Dev Lessons

* Never check for `typeof variable === “object”` when checking for null
* Only use async/await in a function if additional code is used after the async calls, i.e., if the last thing in the function is an async call, then the whole function doesn’t need to be async. 

This is good:

```javascript
public someFunction() {
    try {
        this.service.doStuffAsync();
    } catch (error) {
        this.logger(error);
    }
}
```

This is not:

```javascript
public async someFunction() {
    try {
        await this.service.doStuffAsync();
    } catch (error) {
        this.logger(error);
    }
}
```



### Circular Dependencies

* [https://railsware.com/blog/how-to-analyze-circular-dependencies-in-es6/](https://railsware.com/blog/how-to-analyze-circular-dependencies-in-es6/)
* [https://stackoverflow.com/questions/38841469/how-to-fix-this-es6-module-circular-dependency/42704874\#42704874](https://stackoverflow.com/questions/38841469/how-to-fix-this-es6-module-circular-dependency/42704874#42704874)
* [https://medium.com/content-uneditable/circular-dependencies-in-javascript-a-k-a-coding-is-not-a-rock-paper-scissors-game-9c2a9eccd4bc](https://medium.com/content-uneditable/circular-dependencies-in-javascript-a-k-a-coding-is-not-a-rock-paper-scissors-game-9c2a9eccd4bc)

