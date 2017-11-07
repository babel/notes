# Babel Weekly Notes - 2017-11-01

## News

- [Donation for $1k/month](https://twitter.com/left_pad/status/923696620935421953) (and many other projects) from fbOpenSource! Believe it or not, our previous highest donation was actually only $100/month!
  - [Tweet](https://twitter.com/opencollect/status/923707285674721280) from Open Collective
  - We plan on using the funds to send our core team members to TC39 (The meetings are every 2 months for the cost of hotel/flight/food).
  - Ideally we would use these funds to be able to support someone full time, but we even aren't close to that amount yet. Again, talk to us if you believe you can change that!
- Archived both [babylon](https://github.com/babel/babylon) and [babel-preset-env](https://github.com/babel/babel-preset-env) and moved both packages into the main monorepo
- Released a [7.0.0-beta.31](https://github.com/babel/babel/releases/tag/v7.0.0-beta.31) but still working on the post/changelog
  - Scoped packages: `babel-core` -> `@babel/core`
  - Top level packages, plugins, presets have a peerDep: `@babel/core`
  - Removed `-es2015-` from packages like `@babel/plugin-transform-classes` -> `@babel/plugin-transform-es2015-classes`
  - Stage presets have `loose` and `useBuiltIns` options
  - JSX fragment support `<>`
  - [`babel-template`](https://github.com/babel/babel/blob/master/packages/babel-template) is faster, easier to use
  - v7.0.0-beta.31 is ~60% than v6 now: https://twitter.com/left_pad/status/927554660508028929
    - https://twitter.com/rauchg/status/924349334346276864
    - https://twitter.com/bmeurer/status/924724880263798784
    - https://twitter.com/bmeurer/status/927224716674428928
    - https://twitter.com/bmeurer/status/927500214436589568
    - https://twitter.com/v8js/status/927572065598824448

## Todos (via Logan)

> Please contact/comment if you have opinions/suggestions for these efforts below!

- Caching API? https://github.com/babel/babel/issues/5372
- Get decorators working properly: https://github.com/babel/babel/pull/6107
- Do we just make `"sourceType" :"ambiguous"` the default for now?: https://github.com/babel/babel/issues/6242
- Do we resolve `.babelrc` files in node_modules, or use the cwd or something? https://github.com/babel/babel/issues/6766
- How to deal with polyfilling (core-js v3, etc)
  - Is it even worth having the name `babel-polyfill` if it currently is just `core-js` + `regenerator-runtime`?
  - Ideally preset-env would allow you to substitute any polyfill in, not hardcoded to `core-js` itself either
  - How long do we wait on the [regenerator](https://github.com/facebook/regenerator) re-license, do we just make it opt-in?
