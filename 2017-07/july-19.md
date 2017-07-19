# Babel Team Meeting - 2017-07-19
 
## Attendees

- Brian
- Emma
- Henry Zhu
- Kai
- Kara
- Logan
- Sven Sauleau

## Discussion

- nail down the scope of Babel 7, not really about time.
- update [milestone](https://github.com/babel/babel/milestone/9) to reflect actual
- beta: asap, determine the upgrade guide/codemods
- rc:

- Babel 7 Release?
  - When to do a beta and actively ask projects to switch, and actual release.
  - How to we handle the changelog, and codemods for all breaking changes, make the transition simple for everyone.
  - Was thinking about the flow from proposal -> in browsers and how Babel fits in.
      - Example: When the proposal spec changes, Babel needs to make the changes in a major version bump, update stage presets, deprecate the old package, create a codemod to automate the move, update docs + recommendations so that everyone is on the latest spec.
- Plugin options?
  - loose/spec/normal: how to make this better? How do options get used in presets? 
- How can we make workflow easier? We should take advantage of tools like astexplorer/runkit/codesandbox/unpkg/wzrdin/etc. This would make our docs examples/REPL/reproducing bugs less painless and more helpful.
- Backporting? Lots of requests: we should have a policy, also a guide on how to workaround release schedule: fork, pin, etc?

## Old stuff

- Plugin ordering?
- babel-preset-stage-*? https://github.com/babel/babel/issues/4955
- deprecating "env" still? https://github.com/babel/babel/issues/5276

## Potential TODOs

- [https://github.com/babel/babel/issues/5632](https://github.com/babel/babel/issues/5632): annotation for minifiers (/* @class */)

## Proposal Updates

- Pattern Matching (Stage -1): https://github.com/babel/proposals/issues/6 with Babylon PR
- Optional Catch Binding (Stage -1): https://github.com/babel/proposals/issues/7 with Babylon/Babel PR
