## August 28 ([discuss](https://github.com/babel/notes/pull/5))

### [x] Moving back to [Github Issues](https://github.com/babel/babel/issues)!!!

[@danez](https://github.com/danez) basically did all the work for this so a HUGE shoutout to him.

It's probably not a big surprise that it's happening but for those who don't know: Phabricator is great and helps a lot dealing with issues/triage but in the end not what we want.

A lot of people still report issues on our [website repo](https://github.com/babel/babel.github.io), in commits, or report instead using the `@babeljs` twitter. Others have told us that they were too intimidated to report on a different site or weren't going to login/make an account. Not seeing the issue tab on the project prevented a lot of newcomers from contributing as well.

At the same time, we have very few consistent contributors and like most projects few maintainers.

- [x] We released the [Babili post](http://babeljs.io/blog/2016/08/30/babili)
- [x] Released a 0.0.1 of [`babel-preset-env`](https://github.com/babel/babel-preset-env) (autoprefixer for babel)

```js
$ npm install --save-dev babel-preset-env
```

```js
// src
export class A {}
```

```js
// default is to run all transforms
{
  "presets": [
    ["env", {}]
  ]
}

// ...

var A = exports.A = function A() {
  _classCallCheck(this, A);
};
```

```js
// target chrome 52
{
  "presets": [
    ["env", {
      "targets": {
        "chrome": 52
      }
    }]
  ]
}

// ...

class A {}
exports.A = A;
```

```js
// target chrome 52 with webpack 2/rollup
{
  "presets": [
    ["env", {
      "targets": {
        "chrome": 52
      },
      "modules": false
    }]
  ]
}

// ...

export class A {}
```

---

Please feel free to discuss these notes in the [corresponding pull request](https://github.com/babel/notes/pull/1) or join in on our discussions in [#development](https://babeljs.slack.com/messages/development). (Sign up at [slack.babeljs.io](https://slack.babeljs.io/)).
