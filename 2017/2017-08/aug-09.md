Babel Team Meeting - 2017-08-09
 
## Attendees

- Henry
- Peeyush
- Karl
- Brian
- Kara
- Emma

## Focus: Babel 7 Beta

> Review https://github.com/babel/babel/milestone/9

- Henry: last 2 issues in the milestone by justin: babel-types refactor, object-rest-spread refactor.
- Peeyush: have a branch for decorators, https://github.com/peey/babel/blob/decorators-2-transform-wip/packages/babel-plugin-transform-decorators-2/src/index.js
- Karl: Wanted to see how private methods should work. It is a separate proposal though so can make a new package for that. We should schedule a meeting with littledan to talk about private properties and where were at with that. (Should probably do this for decorators too actually)
- Kara: question about codmods (sven brought up a standalone executable). We can just use npx + babel-codemod: `npx babel-codemod --plugin ./plugin.js src/`.
- Brian: need to release all the other packages: preset-env 2.0, other integrations. We already released compatible versions for webpack, gulp, rollup, grunt.
- Brian: make sure the documentation is ready for 7.0
- Henry: learned that more well defined issues -> quick contributions!
- Henry: will finish the Summer of Code post today and make a PR, then post Peeyush's after. Karl will make a PR for his own post too!
- Henry: now that we have like 1-2prs left, we should switch all the repos from 7.0 to master

## Issues

- Had two PRs recently about nodes being reused and having problems (not using `t.clone`) https://github.com/babel/babel/pull/6046, https://github.com/babel/babel/pull/6054 - this has been an issue for a while and comes up every once in a while. Should figure out a solution for this.

## Updates
- Merged test262 PR into babylon!
- Made a new alpha.19 release (includes typescript)! updated Behance already too!
- Made issues for the TC39 updates https://github.com/babel/proposals/issues/19
- Released major version of integrations with `gulp`, `rollup`, `grunt` that now require `babel-core` as a peerDependency
- Using yarn workspaces in babel/babili so `make bootstrap` should be faster now (requires new yarn version)

## PRs to Review

- Milestone PRs: https://github.com/babel/babel/milestone/9
- React rewrite of REPL! https://github.com/babel/babel.github.io/pull/1297
- Revitalized the syntax error PR https://github.com/babel/babylon/pull/658
- Move babel-standalone into the monorepo https://github.com/babel/babel/pull/6029
  - https://github.com/babel/babel.github.io/pull/1284
- Simpler import syntax output https://github.com/babel/babel/pull/6039
