# JavaScript

### Dev Lessons

1. Never check for `typeof variable === “object”` when checking for null
2. Only use async/await in a function if additional code is used after the async calls, i.e., if the last thing in the function is an async call, then the whole function doesn’t need to be async. This is good:

```text
public someFunction() {
    try {
        this.service.doStuffAsync();
    } catch (error) {
        this.logger(error);
    }
}
```

This is not

```text
public async someFunction() {
    try {
        await this.service.doStuffAsync();
    } catch (error) {
        this.logger(error);
    }
}
```

