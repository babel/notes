# 09-10 meeting

We [did it](https://twitter.com/left_pad/status/1034204330352500736).

## Better Monorepo support

We assumed a single config at the root running Babel from the current working directory

https://github.com/babel/babel/pull/8660, https://github.com/babel/babel/pull/8636

- Adding a new option `autoRoot: true` or specifying a `root` folder
- Should we search for a config in every parent directory?
- We are defaulting to the current working directory currently, but nothing guarantees that it's the root dir
- Brian: I prefer autoRoot but like Logan's idea to make it an enum (for future evolution)
- Does it make sense to combine both options (`root`: "root" instead of `autoRoot: true`)? PR https://github.com/babel/babel/pull/8636.
- We already ignore Babel configuration in `node_modules`.
- `autoRoot: true` is probably a better UX

## class features

https://github.com/babel/babel/pull/8130

- Nothing noticeable from the user point view, only an internal plugin
- What happens when a proposal reaches stage 4? Should we split it out again?
- After stage 4 `proposal-*` isn't a good name anymore, but renaming it is a breaking change.
- General question: do we want to continue to use Lerna's fixed publishing?
- We could publish a new package for each breaking change? Or introduce a new option (and then make it the default in the next major)
- Expose the common options for now (public, private, decorators) and expose more if needed

## extending the parser

- Fork babel-parser, develop one feature (like decorator) and specify `parser: fork` option from the transform plugin

## Babel 7.0.1

https://github.com/babel/babel/pull/8659

- Make a new 7.0.1 branch, for only bug fixes/regressions
- it's a one-off
