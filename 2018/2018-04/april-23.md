# 4/23 Meeting

## Participants
- Logan
- Brian
- Henry

## RC Release

What do we what to gurantee in the RC? That there are no more intentional breaking changes.

> The two config/decorators PRs landed in `beta.46` already (what we planned on merging from last week's [meeting](https://github.com/babel/notes/blob/hzoo-patch-1/2018/2018-04/april-16.md#release-rc)).

Even though it's been such a long time since the last major version and believe me we really want to release a v7, we don't want to just rush things.

There a few things left (that we can think of atm) to fix.

### Removing Stage presets

New discussion: [babel/babel#7770](https://github.com/babel/babel/issues/7770)

- Idea: Just throw an error when using? (too aggressive)

Decision: `npm deprecate` the beta version and not publish a final version. Add to upgrade docs, and add support in `babel-upgrade`. We can do this immediately.

### sourceType/Typescript/file extensions

- Table of file extension to `sourceType`?

Decision: Logan will make another PR

### babel-runtime/core-js

- Goals: Use babel helpers without `core-js` since maybe unecessary
- Later: merge preset-env + transform-runtime logic

Decision: rename `babel-runtime` to `babel-runtime-core-js-2`. `transform-runtime`: Check package.json - make sure it's a devDep? Check that there is a `runtime` in deps since people forget.

### Merge experimental class plugins (class-properties, decorators, private properties) into one

- Setup a call/chat with Justin, Nicolo, and anyone else who would like to join to discuss strategy (ex. should we land current PRs first?)

## Website

- Move all docs to the website repo, the package readme's link to the website (make sure the url is fixed)
- Document the version something changed
