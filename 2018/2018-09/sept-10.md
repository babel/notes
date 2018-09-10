# 09/10 meeting

We [did it](https://twitter.com/left_pad/status/1034204330352500736), 🎉! 7.0 is out.

And now back to regular releases.

## Better Mono-repo Support

We assumed a single config at the root running Babel from the current working directory

https://github.com/babel/babel/pull/8660, https://github.com/babel/babel/pull/8636

- Adding a new option `autoRoot: true` or specifying a `root` folder
- Should we search for a config in every parent directory?
- We are defaulting to the current working directory currently, but nothing guarantees that it's the root dir
- Brian: I prefer autoRoot but like Logan's idea to make it an enum (for future evolution)
- Does it make sense to combine both options (`root`: "root" instead of `autoRoot: true`)? PR https://github.com/babel/babel/pull/8636.
- We already ignore Babel configuration in `node_modules`.
- `autoRoot: true` is probably a better UX

## New Class Proposals (decorators, private fields, etc)

https://github.com/babel/babel/pull/8130: it is helpful, and in some cases necessary to have certain proposals in the same "plugin". Proposal is to make a new "internal package" that combines all the class proposals into 1 and then just refer to turning on those plugins in the other plugins (decorators, class properties, etc).

- Nothing noticeable from the user point view, only an internal plugin.
- What happens when a proposal reaches stage 4? Should we split it out again? (No if it's not user facing because it should be included in preset-env?)
- After stage 4 `proposal-*` isn't a good name anymore, but renaming it is a "breaking change". (Although we shouldn't have to rename it to "transform" because we don't intend people to be using plugins individually if they are Stage 4; just use preset-env in that case).
- General question: do we want to continue to use Lerna's fixed publishing? (ideally we would at least want the proposal plugins to be independently versioned and even maybe at `0.x` to show that they are inherently unstable and subject to change.
- However, we could publish a new package for each breaking change instead (naming convention TBD)? Or just introduce a new plugin option (and then make it the default in the next major, such as with decorators (e.g. legacy)).
  - Expose the common options for now (public, private, decorators) and expose more if needed (not sure at the moment if a whole grid of options is necessary at all).
- Regarding versioning: maybe fork `@babel/parser`, develop one feature (like decorators) and specify `parser: fork` option from the transform plugin? (How that would work with any other new parser plugins, although that is an incentive to switch. If we regard those as legacy/fixed then it's not an issue?)

## Patch Release: 7.0.1

https://github.com/babel/babel/pull/8659

- Make a new [7.0.1 release](https://github.com/babel/babel/pull/8659#issuecomment-420050000), for only bug fixes/regressions so far? There is a versioning issue we'd like to fix before we introduce any more helpers (and we already landed a lot in master), so we should release a patch.
