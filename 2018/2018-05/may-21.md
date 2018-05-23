# 05/21 Meeting

## Participants

- Brian Ng
- Logan Smyth
- Sven Sauleau
- Nicolò Ribaudo
- Henry Zhu

## Notes

### Babylon plugin (options)

- Decorators and flow parser plugin added options (because of multiple implementations)
- Logan raised an issue about potential issues with ordering (https://github.com/babel/babel/issues/7984).
- I think we agree options will be necessary in the future, but we should really determine the correct behavior regarding options/infra
- Stage 0-2 proposals are inherently unstable and may have multiple implementations so we should figure out how to handle that in Babel
- Merging Babel/Babylon configurations might be too hard and lead to unexpected results, overriding behavior is easier to understand and works currently.

---

Conclusion: Ignore any following plugins that already exists; also consider adding validation and possibly a `skipValidation` flag that Babel sets to true (not a blocker).

PR: https://github.com/babel/babel/pull/7994

## TypeScript extension detection

PR: https://github.com/babel/babel/pull/7955

- Logan: Making TS aware of file extensions
- Idea: do the same for Flow, based on existance of .flowconfig?
- Philosophy: Make transforms dumb + options, presets should have own logic to decide the options (like babel-loader/preset-env with `modules: false`)

---

Conclusion: moving forward with the PR

## Shared data between plugins?

PR: https://github.com/babel/babel/pull/7878

- `jsxPragma` in TS/React presets? Maybe it's just an issue of plugin ordering as well. It's the same value for different purposes so it's probably ok.
- Babel/core could expose the configuration and plugins could configure itself based on the config
- Use a shared helper? Like the JSX transform
- We can use https://github.com/babel/babel/blob/c558dedd7b5ffacf4d462177857cc031e7f4efe0/packages/babel-core/src/transformation/file/file.js#L51-L61
- Idea: Run a phase before presets/plugins which order/clean/configure Babel itself based on the configuration/context/etc. Just thoughts.
- 
---

Conclusion: Move JSX comment logic from "Program" into "pre" step for other plugins, TS preset can read from the shared global Map

## TC39 Meeting This Week

- Henry and Justin should be there! [Agenda](https://github.com/tc39/agendas/blob/master/2018/05.md)

## "sourceType: script" as default and auto generated file extension

PR Closed: https://github.com/babel/babel/pull/7501

Conclusion: Delay decision since v6 didn't have massive issues and v7 has workarounds for the issue. Also talking with Node, modules group, TS it seems best to wait for decisions instead of changing our default behavior.

## `fileExtensions` as a first-class citizen

- Originally for TS, move to core
- Can use in `@babel/node` and `@babel/register`
- We can know what files to compile beforehand
  - Future: idea of a "project" aka multi-file awareness, maybe async pre-compile plugins?

## Moving most logic into helpers?

- Better sharing between plugins
- How do you let community plugins use/create helpers?
- Easier to optimize a helper vs. inlined (think of extracting out JS functions).

Conclusion: Just ongoing work

---

Conclusion: good to have, we can do it in the future.

## Other PRs
- Consistent relative pathing: https://github.com/babel/babel/pull/7956
- Interpreter AST Node: https://github.com/babel/babel/pull/7928

## Etc
- Regular Release Schedule? Need to figure out project requirements vs. arbitrary schedule?
- Roadmap? Move to babel/notes
- Maintainer Docs?
- RGSoC in July
