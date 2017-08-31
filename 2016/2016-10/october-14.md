## October 14 ([discuss](https://github.com/babel/notes/pull/7))

## :tomato: Ketchup (what's happened)

> Excited that https://github.com/yarnpkg/yarn was released by [Sebastian, @kittens](https://github.com/kittens) and co (if you've been wondering what he's been up to)!

### :earth_asia: 3 new collaborators!

Like a lot of OSS community projects, Babel has a few volunteers that work on it in their free time.
We review PRs, triage issues, answer questions on stack overflow/slack/twitter, make releases, write changelogs, etc.

Were happy to have added [Moti Zilberman, @motiz88](https://github.com/motiz88) and [Dan Harper, @danharper](https://github.com/danharper) as collaborators after their awesome work in both babel/babylon. They've already done a lot to fix bugs and close old issues.

And we just invited [Kai Cataldo, @kaicataldo](https://github.com/kaicataldo) today!

Anyone can make contributions (it doesn't have to be a code change either). We know who is commenting on issues/PRs and submitting PRs (I also use an extension I've made https://github.com/hzoo/contributors-on-github)!

We should probably just make a simple team page at some point... 😄

### :octocat: Phabricator -> Github

If you didn't know already, old phabricator links will now auto redirect to the corresponding github issue: https://phabricator.babeljs.io/T2168 -> https://github.com/babel/babel/issues/2168 (sometimes the # isn't the same).

### :birthday: v6.16 (on Babel's Birthday: 2016-09-28)

You can finally pass down [parser options](https://github.com/babel/babylon#options)/[generator options](https://github.com/babel/babel/tree/master/packages/babel-generator#options):

Some of these options are actually top-level options that fit better under their respective keys and will probably be removed in the next major version.

```js
// .babelrc
{
  "parserOpts": {
      "allowImportExportEverywhere": true,
      "allowReturnOutsideFunction": true,
      "sourceType": "module",
      "plugins": ["flow"]
    }
  },
  "generatorOpts": {
    "retainLines": false,
    "comments": false,
    "quotes": "double"
  }
}
```

### :earth_americas: 0.0.6 of [`babel-preset-env`](https://github.com/babel/babel-preset-env) (autoprefixer for Babel)

> There's still a lot to be done here and this preset will always require updating.

This was first mentioned/released (0.0.1) in the last [Sept post](/2016-09/september-19.md).

```js
$ npm install --save-dev babel-preset-env
```

Interesting issues:

- [#9](https://github.com/babel/babel-preset-env/issues/9): support a `"node": "process` to auto detect the version of node (with `parseInt(process.versions.node)`). Basically what is done in [create-react-app#878, @shubheksha](https://github.com/facebookincubator/create-react-app/pull/878) to make tests run faster in each node version during CI.
- [#20, @keyanzhang](https://github.com/babel/babel-preset-env/issues/20): Apply the autoprefixer concept to polyfills as well. Their might be multiple solutions to this but one is to transform the polyfill call!

```js
require('babel-polyfill');
// gets transformed to

require('babel-polyfill/array-from');
require('babel-polyfill/array-of');
require('babel-polyfill/object-assign');
require('babel-polyfill/regenerator-runtime');
/* ... other polyfills that IE 11 needs */
```

With https://github.com/babel/babel-preset-env/pull/19, `env` now supports a `browsers` option which allows an autoprefixer-like query.

```
{
  presets: [
    ["env", {
      "targets": {
        "chrome": 52,
        "browsers": ["safari > 7"] // array or string query
      },
      "loose": true
    }]
  ]
}
```

There's also a `debug` option to print out the plugins being used (so you can verify for issues)

```bash
Using targets: {
  "node": 6.5
}

Using plugins:

module: false
transform-exponentiation-operator {}
transform-async-to-generator {}
syntax-trailing-function-commas {}
```

---

### :memo: Possible TODOs?

- [ ] Make the REPL amazing again

[#92](https://github.com/babel/babel.github.io/issues/92) [#858](https://github.com/babel/babel.github.io/issues/858) The current REPL has no options and only lets you check specific presets. We should allow choosing specific plugins and supporting all options. Even better would be to allow pasting in a .babelrc and being able to use any plugin on npm in the repl.

- [ ] Website updates
 - [ ] Make sure all plugins have an example + REPL example like [arrow-functions](http://babeljs.io/docs/plugins/transform-es2015-arrow-functions/)
 - [ ] [#4590](https://github.com/babel/babel/issues/4590) Make the contributing guide better
 - [ ] [#27](https://github.com/babel/babel.github.io/issues/27) Add resources page
 - [ ] explain slack channels
 - [ ] [#930](https://github.com/babel/babel.github.io/issues/930) menu/page revamp?

- [ ] Update proposals (decorators, etc): https://github.com/babel/babel/issues/2645. Not sure anyone has capacity for this though.
- [ ] `babel-init`: either just a website interface to create a config or a CLI command.
- [ ] Running the offcial [tc39/test262](https://github.com/tc39/test262) test against Babel: Made an issue over at the node version https://github.com/bterlson/test262-harness/issues/58
- [ ] Smoke tests: Find the top projects using Babel (what are they?) and run the master version on the last release. Would be nice to have a reverse greenkeeper service (when updating PR every repo to run tests).

Please feel free to discuss these notes in the [corresponding pull request](https://github.com/babel/notes/pull/6) or join in on our discussions in [#development](https://babeljs.slack.com/messages/development). (Sign up at [slack.babeljs.io](https://slack.babeljs.io/)).
