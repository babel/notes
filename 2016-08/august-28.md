## August 28 ([discuss](https://github.com/babel/notes/pull/5))

Just adding updates since the last notes.

- [ ] Moving from [Phabricator](https://phabricator.babeljs.io) back to Github issues ([`repo`](https://github.com/babel/phabricator-to-github))

Almost ready!

Again, [@danez](https://github.com/danez) is doing an amazing job working on this (so far a solo effort). We hope of this to happen soon.

- [x] Preset Options ([PR #3331](https://github.com/babel/babel/pull/3331))

This landed in [v6.13.0](https://github.com/babel/babel/releases/tag/v6.13.0)

- [x] `es2017` preset

This landed in [v6.14.0](http://babeljs.io/blog/2016/08/24/6.14.0)

- [x] babel-minify

Released in beta as [babili](https://github.com/babel/babili). You can try it out in the [REPL](http://babeljs.io/repl/#?babili=true&evaluate=false&lineWrap=false&presets=react&experimental=false&loose=false&spec=false&code=class%20A%20%7B%0A%20%20%0A%7D%0A%0AA()%3B&playground=true).

Writing a post [here](https://github.com/babel/babel.github.io/pull/898)

### Not Finished Yet
- [ ] Codemods ([PR #3561](https://github.com/babel/babel/pull/3561))
- [ ] `babel-preset-env` (autoprefixer for babel) [PR #3476](https://github.com/babel/babel/pull/3476)

### Other ideas
- [ ] add to `babel-polyfill` to support importing specific year's polyfills: `import 'babel-polyfill/es2015'`
- [ ] add an option to preset `es2015` to remove/disable regenerator.
- [ ] ?

---

Please feel free to discuss these notes in the [corresponding pull request](https://github.com/babel/notes/pull/1) or join in on our discussions in [#development](https://babeljs.slack.com/messages/development). (Sign up at [slack.babeljs.io](https://slack.babeljs.io/)).
