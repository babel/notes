# Babel Weekly Notes - 2017-10-25

## News

- Logan/Henry were at Chrome Dev Summit! (https://twitter.com/left_pad/status/922507305874104320)  
- Sven at ReactiveConf (https://twitter.com/svensauleau/status/923210175011590146)  
- Added [@azz](https://github.com/azz), [@keithamus](https://github.com/keithamus), [@Andarist](https://github.com/Andarist) to the team  
- Also added [@bmeurer](https://github.com/bmeurer) (other v8 members are already collaborators) since already made like 5 perf PRs (https://github.com/babel/babel/pull/6581)
- Probably last betas, then do RCs for regressions (and ask for wider use) and release?
  - Need to think about the codemods for upgrading in the meantime.. (also an opportunity to help)
  - Don't ask for a backport, no time/resources/etc 🙂.
  
## Done

- [x] Move to scoped packages https://github.com/babel/babel/pull/6495

`babel-cli` -> `@babel/cli`
`babel-preset-env` -> `@babel/preset-env`: shorthand in `.babelrc` is: `@babel/env`
`babel-plugin-xyz` -> `@babel/plugin-xyz`: shorthand in `.babelrc` is: `@babel/xyz`

- [x] Move to peerDeps on babel-core https://github.com/babel/babel/pull/6549 https://github.com/babel/babel/pull/6569

All plugins/presets/top level user pkgs will have a peerDep on `babel-core`.
This is the same behavior as `babel-loader` currently, but it will apply for `gulp-babel`, `babel-cli`, etc

- [x] Rename proposal plugins to `-proposal` instead of `-transform` https://github.com/babel/babel/pull/6570

Example: `@babel/plugin-transform-class-properties` -> `@babel/proposal-transform-class-properties`

When a proposal becomes Stage 4, we will signify the change by renaming it back to `transform`.

- [x] Renamed all plugins to not need have a year prefix like `-es2015-`, `-es3-`: https://github.com/babel/babel/pull/6575

## Doing

- [ ] Still need to move babel-preset-env issues/PRs over to the main repo
- [ ] Move babylon into the monorepo https://github.com/babel/babel/pull/6484

## Waiting On

- [ ] Use new MIT Licensed `regenerator` (@zpao asked already)
  - [ ] Need to update `babel-types` in `regenerator` as well
