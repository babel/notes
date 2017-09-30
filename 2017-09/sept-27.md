# Babel Team Meeting - 2017-09-27

> No meeting since some of us we're at TC39/busy, so writing down what we need to work on.
> If anyone wants to help out with one of these, please reach out!

### Updates

- [x] Did a beta.2
- [x] Henry/Justin at TC39 https://github.com/babel/proposals/issues/28
  - [x] Already landed "Throw Expressions"

### Priorities (mostly meta/infra)

- [ ] Move babylon into the monorepo (only issue is that it's beta.25 or something already while everything else is beta.2 so the whole fixed versioning thing doesn't work that that's my bad, workarounds would be to move that to experimental/ or publish as separate module name in the meantime)
- [ ] Move preset-env into the monorepo
- [ ] rename `babel-plugin-transform` to `babel-plugin-proposal` for certain plugins?
  * syntax- => use a proposal without transforming
  * proposal- => use a proposal with transforming
  * transform- => use a standard feature with transforming
- [ ] Run babel on itself before publish: https://github.com/babel/babel/issues/6134

### Babel 7 Work

- Fix cyclical dep warnings in Lerna: https://github.com/babel/babel/issues/6204
- Actually figure out the plan for releases/versioning (may need lerna PR, or just a better setup)
- Script/Module parsing: https://github.com/babel/babel/issues/6242
- Figure out the deal with peerDependencies on `babel-core` given people will try to install a preset on v7 and babel-core on v6 or vice-versa.
- figuring out the situation with babel-runtime/transform-runtime/helpers/polyfill
- kill "inherits" key? (possibly do plugin ordering)

### PR Review
- [ ] babel-types https://github.com/babel/babel/pull/5971
- [ ] Stage 2 decorators https://github.com/babel/babel/pull/6107
- [ ] Private props https://github.com/babel/babel/pull/6120
