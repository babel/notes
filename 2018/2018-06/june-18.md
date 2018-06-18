# 04/18 Meeting

## Participants

- Sven
- Henry
- Logan

## RC

> One major thing left: regarding helpers/core-js/transform-runtime. Docs are getting more updated.

- [x] Switched over the new docs (using [docusaurus](https://docusaurus.io), new pages) to main domain https://babeljs.io. (will fix as needed)
- [ ] Logan: Separate out helpers/core-js/runtime: https://github.com/babel/babel/issues/8155
  - *Problem*: We want to output less code and de-duplicate helpers, thus we want as many people as possible to use "transform-runtime".
  - Issue with current version is that people have to use `core-js` in order to use helpers. Also even if you want to use `core-js` the version is fixed.
  - Alternative: use `external-helpers` but that is a global; used with rollup? Also have to generate it yourself
  - 2 helpers: one with `core-js` and one without.
  - `babel-runtime` (default) and `babel-runtime-corejs2` both have helpers, but only `core-js` one has `core-js` included. Also add a `babel-runtime-corejs3`
  - Options: potentially remove `helpers` (check why added), `moduleName` (check CRA), `useESModules` (make `.mjs`), `polyfill/useBuiltIns` are same.
  - Future: `transform-runtime` can read the `package.json`?
  - Docs: explain the default behavior, how to get the same behavior in v6 now in v7
- [ ] Henry: removing Stage presets https://github.com/babel/babel/issues/7770
- [ ] Henry: will startup release blog post (even though wrote many of them before 😛)
- Tentatively: land these and then do the RC. 
  - We should do a run through of existing PRs together as a team to fixup any other small things we want to do during RC period.

## Misc discussions for later
- Major versions should just change our default flags, otherwise add new features under a flag during releases?
- Future: we should have independent helpers, move helpers into the transform itself?
- Move babel-standalone into separate build
- TS with `@babel/register`, still need to provide extensions but we can figure it out later
