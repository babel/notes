# Babel Team Meeting - 2017-09-13

## Attendees

- Brian
- Logan
- Sven
- Henry

## Discussions

- Actually released a beta (http://babeljs.io/blog/2017/09/12/planning-for-7.0)!
  - Work on regressions, ask people to try it!
  - Criteria for official release is vague, we have few PRs that are considered blocking other than regressions. Might just upgrade a few big packages/libraries and call it.
- Did first guest blog post in a really long time: http://babeljs.io/blog/2017/09/11/zero-config-with-babel-macros by @kentcdodds
  - Made an issue to track other ideas
- [ ] Move stuff into the monorepo: (babylon @danez was working on), (babel-preset-env @existentialism)
- babel-standalone + yarn workspaces linking was having issues so we reverted.
- [ ] docs versioning? maybe a new url for `babeljs.io/6/docs`, `babeljs.io/7/docs` and default to 7? Need to put the version number somewhere as well.
- [ ] REPL bugs/versioning - people are reporting bugs in the REPL but it has old deps so we need to fix that.
- no major breaking changes planned other than the changes @loganfsmyth / @jridgewell already were thinking of
- [ ] fix cyclical deps https://github.com/babel/babel/issues/6204
- [ ] Lerna: figure of publishing situation
- [ ] rename proposals plugins
- Logan had a concern about independent plugins/proposals - it is difficult specifically for decorators/class properties to work together. It's also the main issue we had with plugin ordering so maybe it should be combined
- runtime/transform-runtime/polyfill/regenerator situation sucks
- [ ] would be nice to land https://github.com/babel/babel/issues/6205 sometime, could be help-wanted
- for the future: https://github.com/babel/notes/issues/34

## Review/TODOs

- Move babel/babylon into babel/babel (Daniel)
- Move babel/babel-preset-env into babel/babel (Brian)
- babel-types refactor: https://github.com/babel/babel/pull/5971
- `stage3` option to preset-env: https://github.com/babel/babel-preset-env/pull/384
- Stage 2 Decorators transform: https://github.com/babel/babel/pull/6107
- Class Private Properties transform: https://github.com/babel/babel/pull/6120

## Interesting PRs merged

- `classPrivateMethods ` parser support: https://github.com/babel/babylon/pull/703
- Bundle of modules PRs by Logan: https://github.com/babel/babel/pull/6230, https://github.com/babel/babel/pull/6237, https://github.com/babel/babel/pull/6238, https://github.com/babel/babel/pull/6244

## Misc ideas (not discussed, but I was just looking back at previous notes)

- At some point: do a post on open collective since we never did, can setup t-shirts again
- Better onboarding/contributing guide
- babel-bot needs some love
- Perf metrics: https://github.com/babel/babel/issues/5340
- babel-init
- plugin ordering
- Guide on compiling/publishing ES2015+, .mjs, etc
- Better syntax errors: https://github.com/babel/babel/issues/6205
- future of `babel-core` and versioning it
- re-purpose `babel` again
- remove babel's hardcoding of traversal (async visitors, etc)
