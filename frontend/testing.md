---
description: Anything related to testing in Web Development
---

# Testing

## Dev Lessons

* Separate app initialization from the code that runs it. It can be useful when writing tests

## How To's

### Test a server stops on SIGTERM

```text
it("should terminate on SIGTERM", async () => {
        jest.useFakeTimers();

        const processEvents = {};

        process.on = jest.fn((signal, cb) => {
            processEvents[signal] = cb;
        });

        process.kill = jest.fn((pid, signal) => {
            processEvents[signal]();
        });

        const server = new Server();

        const stopSpy = jest.spyOn(server, "stop");
        const startSpy = jest.spyOn(server, "start");

        stopSpy.mockImplementation(() => true);
        startSpy.mockImplementation(() => true);

        await startUp.main();

        process.kill(process.pid, "SIGTERM");

        jest.runAllTimers();

        expect(stopSpy).toHaveBeenCalledTimes(1);
    });
```

Source: [https://stackoverflow.com/questions/46494297/nodejs-jest-unit-test-settimeout-in-process-on-callback](https://stackoverflow.com/questions/46494297/nodejs-jest-unit-test-settimeout-in-process-on-callback) 

### 

### Test an async function that throws an error

```text
it('should test async errors', async () =>  {        
    await expect(failingAsyncTest())
    .rejects
    .toThrow('I should fail');
});
```

Source: [https://stackoverflow.com/questions/47144187/can-you-write-async-tests-that-expect-tothrow](https://stackoverflow.com/questions/47144187/can-you-write-async-tests-that-expect-tothrow)

### 

### Change a mocked implementation on a per-test basis

Research more this.

Sources:

* [https://stackoverflow.com/questions/48790927/how-to-change-mock-implementation-on-a-per-single-test-basis-jestjs](https://stackoverflow.com/questions/48790927/how-to-change-mock-implementation-on-a-per-single-test-basis-jestjs)

### Prepare a Node server for testing \(Express, Hapi, etc\)

pseudocode:

```text
export const makeServer() => {

    const server = getServer();

    return new Promise((resolve) => {

        server.listen({ port: config.PORT }, () => {
            console.log('Server rocking on PORT', config.PORT);
            resolve(server);
        });

    });
}
```

```text
describe("server tests", () => {

    let server;

    beforeEach(async () => {
        server = await makeServer();
    });

    afterEach(async () => {
        await server.stop();
    });

    it("server should run", async () => {
        const res = await server.call({
            method: "get",
            url: "/version.json",
        });
        expect(res.statusCode).toBe(200);
    });
});

```

Got this from Kent C. Dodds: [https://frontendmasters.com/courses/testing-javascript/introducing-integration-testing/](https://frontendmasters.com/courses/testing-javascript/introducing-integration-testing/)

### How to get content set using dangerouslySetInnerHTML

```text
// TestComponent.jsx
import React from 'react';

const MyComp = ({ text }) => <p className="target" dangerouslySetInnerHTML={{ __html: text }}></p>

export default MyComp;


// TestComponent.test.js

it('can read content set using dangerouslySetInnerHTML', () => {
    const text = "Ampersand &amp;";
    const wrapper = mount(<MyComp text={text} />)
    const target = wrapper.find('.target');
    const { dangerouslySetInnerHTML: { __html } } = target.props();
    expect(__html).toEqual("Ampersand &amp;");
});
```

