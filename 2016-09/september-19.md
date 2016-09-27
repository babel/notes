## September 19 ([discuss](https://github.com/babel/notes/pull/6))

### [Babili post](http://babeljs.io/blog/2016/08/30/babili)

### Moving back to [Github Issues](https://github.com/babel/babel/issues)!!!

[@danez](https://github.com/danez) basically did all the work for this so a HUGE shoutout to him.

It's probably not a big surprise that it's happening but for those who don't know: Phabricator is great and helps a lot dealing with issues/triage but in the end not what we want.

A lot of people still report issues on our [website repo](https://github.com/babel/babel.github.io), in commits, or report instead using the `@babeljs` twitter. Others have told us that they were too intimidated to report on a different site or weren't going to login/make an account. Not seeing the issue tab on the project prevented a lot of newcomers from contributing as well.

At the same time, we have very few consistent contributors and like most projects a few maintainers.

If were going to grow our contributors, we should at least lower the barriers and try to work within Github.

> I'l make an issue real soon to discuss how we are going to manage issues and grow the project.

### Released a 0.0.1 of [`babel-preset-env`](https://github.com/babel/babel-preset-env) (autoprefixer for babel)

> Ref https://github.com/babel/babel/pull/3476

> This will be an ongoing project since this preset will have to be updated very often for all environment updates (browsers, node, etc).

Currently the data is just some stuff I looked up from tables, other repos, etc; it's probably wrong. I'm sure this is probably one of the most helpful things we can be working on right now so having more eyes on the data/users helps a lot.

We'll try reaching out to the authors/maintainers of current presets that do similar things.

Off the top of my head:
https://github.com/sdkennedy/babel-preset-target
https://github.com/jakepusateri/auto-babel
https://github.com/michaelcontento/babel-preset-modern-node
https://github.com/askmatey/babel-preset-modern

Hopefully, we can standardize on this and make it an official preset so we don't need to have a preset for each version (chrome 51, chrome 52, etc) similar to the loose/modules presets.

This way we can get rid of stuff like:

> These are all actual packages, so I think this is a good idea.

- babel-preset-node5
- babel-preset-node6
- babel-preset-es2015-node
- babel-preset-es2015-node4
- babel-preset-es2015-node5
- babel-preset-es2015-node6

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

Please feel free to discuss these notes in the [corresponding pull request](https://github.com/babel/notes/pull/6) or join in on our discussions in [#development](https://babeljs.slack.com/messages/development). (Sign up at [slack.babeljs.io](https://slack.babeljs.io/)).
