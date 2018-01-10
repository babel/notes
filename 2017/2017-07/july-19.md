# Babel Team Meeting - 2017-07-19
 
## Attendees

- Brian
- Emma
- Henry Zhu
- Kai
- Kara
- Logan
- Sven Sauleau

## Questions

- Babel 7 Release?
  - When to do a beta and actively ask projects to switch, and actual release.
  - How do we handle the changelog, and codemods for all breaking changes? We want to make the transition simple for everyone.
  - Was thinking about the flow from proposal -> in browsers and how Babel fits in.
      - Example: When the proposal spec changes, Babel needs to make the changes in a major version bump, update stage presets, deprecate the old package, create a codemod to automate the move, update docs + recommendations so that everyone is on the latest spec.
- Plugin options: loose/spec/normal - how to make this better? How do options get used in presets? 
  - Normal is just what is "reasonable" (performant/mostly spec). If something is too slow we can move it to spec, and if we want to remove some runtime checks we can make it "loose"?
- How can we make workflow easier? We should take advantage of tools like astexplorer/runkit/codesandbox/unpkg/wzrdin/etc. This would make our docs examples/REPL/reproducing bugs less painless and more helpful.
  - Let's get a champion for this? Would love to be able to import any npm module into the REPL/ASTExplorer, and provide a new REPL build per PR to test.
- Backporting? Lots of requests: we should have a policy, also a guide on how to workaround release schedule: fork, pin, etc?
  - Only an issue during a long major release (we should avoid this in the future) - mostly up to our discretion since releasing/backporting takes time.

## Discussion

- Nail down the scope of Babel 7, not really about time but scope creep (easy to do in OSS).
- Update [milestone](https://github.com/babel/babel/milestone/9) to reflect actual tasks for Babel 7, and move the rest to post launch/7.x
- Beta: make one of these ASAP, can use this to determine the upgrade guide/codemods required for majority of users. We can ask plugin authors to update during this time (make their own beta release).
  - Aside: would be amazing if we could release the plugins at the same time as Babel itself is released so that the transition is seamless. It would be better if plugins could just support both versions for a period (maybe no changes are necessary for most).
- RC: Once we have released the beta for a few weeks we can do an RC and then after a week or two do the actual release if nothing major comes up.

## Old stuff

- Plugin ordering?
- babel-preset-stage-*? https://github.com/babel/babel/issues/4955
- deprecating "env" still? https://github.com/babel/babel/issues/5276

## Potential TODOs

- [https://github.com/babel/babel/issues/5632](https://github.com/babel/babel/issues/5632): Annotation for minifiers (/* @class */ or /*#__PURE__*/)

## Proposal Updates

- Pattern Matching (Stage -1): https://github.com/babel/proposals/issues/6 with Babylon PR
- Optional Catch Binding (Stage -1): https://github.com/babel/proposals/issues/7 with Babylon/Babel PR
