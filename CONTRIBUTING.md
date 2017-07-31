# Design Decision

The purpose of this section is to introduce contributors to the philosophy and thinking behind the architecture and API design of this library.

### Client Initialization

As an alternative we could have used `const gateway = new EventGateway({ options })`. I suggest we avoid using the `new` keyword at all as if the user leaves it out this would be an issue hard to discover. In addition I suggest to go agains `import FDK from 'fdk'; const fdk = new FDK()` as this doesn't mention anywhere in the code that this instantiates a Event Gateway client nor does it remove the ability to extend the FDK module going forward by another client or utils.

### Function Arguments

All public functions accept exactly one config argument. There are 3 major reasons why:
1. having one object with properties allows us to extend the API easily in the future
2. being explicit about the keys e.g. `functionId` or `event` helps developers to parse the code more easily
3. having one argument makes it easier for functional programming in JavaScript since currying is not needed