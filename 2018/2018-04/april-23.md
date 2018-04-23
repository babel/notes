## 4/23

> Logan, Brian, Henry

## RC

What do we what to gurantee in the RC: that there are no more intentional breaking changes.

> The config/decorators PRs landed in beta.46 already

### Removing Stage presets

- Throw an error? (too aggressive)

Decision: `npm deprecate` the beta version and not publish a final version. Add to upgrade docs, and add support in `babel-upgrade`.

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
