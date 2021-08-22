---
description: 'https://frontendmasters.com/courses/production-typescript/'
---

# Production-grade Typescript - FrontendMasters

* For libraries, it’s better to not use esModeInterop and skipLibCheck because consumers of the lib will very likely that to turn these configs on and we don’t want to force this decision on the users of our lib
* stripInternal tsconfig: it’ll remove anything marked as @internal. Consumers of our code won’t even see. Useful for tests,  utils, or anything we don’t want to expose
* Keep the types array empty because anything included will be part of the output of the project. If any code included in the types array changes the window object, it’ll be part of the transpired version of your app
* Don’t include jest types or dev types in the tsconfig used for production. Make a different tsconfig only for tests
* Create gitignore file from CLI:  \`\`\`  nix gitignore node  \`\`\`
* \`—preserveWatchOutput\` will keep the log in the console for TSC watch command
* Target: what is the output. What is the language level we want to support
* rootDir: it controls the folder structure inside outDir
* Add noUnusedLocals, noImplicityReturns, noUnusedParemeters
* ESLin. Add in the extends field \(order matters\): 
  * prettier/@typescript-eslint
  * plugin:@typescript-eslint/recomended 
  * plugin:@typescript-eslint/recommented-requiring-type-checking

dtslint

Stickier options

* noUnusedLocals
* noUnusedParameters
* noImplicitReturns
* stripInternal
* forceConsistentCasingFileName

[https://static.frontendmasters.com/resources/2020-10-13-production-typescript/production-typescript.pdf](https://static.frontendmasters.com/resources/2020-10-13-production-typescript/production-typescript.pdf)

[https://github.com/mike-north/professional-ts](https://github.com/mike-north/professional-ts)

