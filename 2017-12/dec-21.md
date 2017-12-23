## Babel Weekly Notes - 2017-12-21

> Last weeks notes: https://github.com/babel/notes/blob/master/2017-12/dec-15.md

## News

- [Sven](https://twitter.com/svensauleau) is going to [speak at ReactEurope](https://twitter.com/ReactEurope/status/943792622753247232)
- [Landed the PR to extend built-ins: `class A extends Array {}`](https://github.com/babel/babel/pull/7020)
- [Landed `lazy` option for modules-commonjs](https://github.com/babel/babel/pull/6952)
- [Landed PR for better error messages with syntax errors](https://twitter.com/left_pad/status/942859244759666691)
- Released [7.0-beta.35](https://github.com/babel/babel/releases/tag/v7.0.0-beta.35)

## Before the v7 Final

We want to fix/plan before release.

1. Caching and invalidation logic in `babel-core`.
2. Better story around external helpers.
3. Either implement or have plan in place for versioning and handling polyfills independently from helpers, so we aren't explicitly tied to `core-js` 2 or 3, since people may have things that depend on one or the other and won't want to load both a lot of the time.
4. Either a working decorator implementation, or functional legacy implementation, with clear path to land current spec behavior during 7.x's lifetime. (Need [independent + versioned publishing in Lerna](https://github.com/lerna/lerna/issues/1121))

## Notable Issues

### [`overrides` behavior](https://github.com/babel/babel/issues/5451)

Be able to compile different globs with a separate config (similar to ESLint [overrides](https://eslint.org/docs/user-guide/configuring#configuration-based-on-glob-patterns))

### [Future of `.babelrc` lookup](https://github.com/babel/babel/issues/6766#issuecomment-352225586)

Probably the only real blocker before a RC version.

### [Switch Website framework](https://github.com/babel/website/issues/1485)

I really want translated docs + versioned docs (this is a big issue since the docs are on v6 and yet everyone still wants to use v7). Getting overwhelmed by the people have a lot of trouble using v7 since docs aren't clear or we are in the process of changing things.

### [Upgrade tool](https://github.com/babel/notes/issues/44)

This should also help with ^.

## Notable PRs

### [Merging `fast-async` into Babel](https://github.com/babel/babel/pull/7076)

- Planning on merging a version of a `async-to-promise` transform into Babel,
provided we can add exec tests from Regenerator and from [kneden](https://github.com/babel/kneden)

## Todos

- Will finally post another blog post before the end of the year: https://github.com/babel/website/pull/1453
- Explain what we think should be done before an RC release and final
- Have a better plan for upgrading the ecosystem
- Also end of the year, so probably don't expect too much if everyone is on break!
