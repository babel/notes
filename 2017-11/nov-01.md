# Babel Weekly Notes - 2017-11-01

## News

- [Donation for $1k/month](https://twitter.com/left_pad/status/923696620935421953) (any many other projects) from fbOpenSource!
  - [tweet](https://twitter.com/opencollect/status/923707285674721280) from Open Collective
- Archived both [babylon](https://github.com/babel/babylon) and [babel-preset-env](https://github.com/babel/babel-preset-env) and moved both packages into the main monorepo
- Released a 7.0.0-beta.31 but still working on the post/changelog

## Todos
- Caching API? https://github.com/babel/babel/issues/5372
- Get decorators working properly: https://github.com/babel/babel/pull/6107
- Do we just make `"sourceType" :"ambiguous"` the default for now?: https://github.com/babel/babel/issues/6242
- Do we resolve `.babelrc` files in node_modules, or use the cwd or something?
- How to deal with polyfilling (core-js v3, etc)
  - Is it even worth having the name `babel-polyfill` if it currently is just `core-js` + `regenerator-runtime`?
  - Ideally preset-env would allow you to substitute any polyfill in, not hardcoded to `core-js` itself either
  - How long do we wait on the [regenerator](https://github.com/facebook/regenerator) re-license, do we just make it opt-in?
