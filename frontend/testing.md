# Testing

## Dev Lessons

1. Separate app initialization from the code that runs it. It can be useful when writing tests

## How to test a server stops on SIGTERM

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

### How to test an async function that throws an error

```text
it('should test async errors', async () =>  {        
    await expect(failingAsyncTest())
    .rejects
    .toThrow('I should fail');
});
```

Source: [https://stackoverflow.com/questions/47144187/can-you-write-async-tests-that-expect-tothrow](https://stackoverflow.com/questions/47144187/can-you-write-async-tests-that-expect-tothrow)

### How to change a mocked implementation on a per-test basis

Sources:

* [https://stackoverflow.com/questions/48790927/how-to-change-mock-implementation-on-a-per-single-test-basis-jestjs](https://stackoverflow.com/questions/48790927/how-to-change-mock-implementation-on-a-per-single-test-basis-jestjs)

### How to prepare a Node server for testing \(Express, Hapi, etc\)

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
