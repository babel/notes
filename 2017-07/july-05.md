# Babel Team Meeting - 2017-07-05

## Attendees
- Nathan Hammond
- Emma Deacon
- Kara de la Marck
- Logan Smyth
- Sven Sauleau

## Discussion

### TypeScript Support in Babylon!

> Landed the PR this week: https://github.com/babel/babylon/pull/523

Three outstanding PRs to finish the effort of nominal TypeScript support in Babel.

- https://github.com/babel/babel/pull/5856
  - Adds definitions for all of the TypeScript nodes to Babel itself.
  - Makes it so that you can add visitors.

- https://github.com/babel/babel/pull/5896
  - Being able to pass TypeScript through the entire Babel system.
  - Allows it to be processed later, eliminating the need to immediately transpile TypeScript to JavaScript.
  - Can be passed through to future plugins.

- https://github.com/babel/babel/pull/5899
  - Builds off the previous two to output TypeScript as JavaScript.
  - Doesn't do type checking.
  - Has limitations because it doesn't have type information (no `namespace` or `const enum`).

There are additional maintenance costs but we expect that we will continue to see contributions from Microsoft. In original discussion with Microsoft the goal was to keep the surface area minimal as TypeScript doesn't add a lot of syntax. Precedent as well for adopting these things with Flow.

Bonus: if others wish to develop plugins that do things with the information that we have in our AST they are able to do so at this point.

### Optional Chaining Landed

> https://github.com/babel/babel/pull/5813

- Has documentation about the actual proposal: https://github.com/babel/babel/tree/7.0/packages/babel-plugin-transform-optional-chaining
- TC39 Stage 1 proposal.
