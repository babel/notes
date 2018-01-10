## Babel Weekly Notes - 2017-12-15

> Haven't done a post in a while so will try to add things in the last month instead of the last week.

## News

- I [posted](https://twitter.com/left_pad/status/938041651452416004) I was going to step back from working on Babel as much, so going to do more of a PM role and focus on my health.
  - We're always looking for more maintainers/collaborators so hopefully as I step down others will step up 🤗
  - We already have a lot of amazing [people](https://babeljs.io/team) working on this project now, but we'll need to continue to grow as people step down for any reason, hopefully can build more connections with other projects/companies and continue to participate in efforts like [Summer of Code](https://babeljs.io/blog/2017/08/09/babel-and-summer-of-code).
- I did AMA on [dev.to](https://twitter.com/ThePracticalDev/status/941007481987268609), and still answering some of the questions now!
- Also did a podcast on [The Web Platform Podcast](https://twitter.com/TheWebPlatform/status/940855461229793280) about Babel.
- [Regenerator](https://github.com/facebook/regenerator) was released under the [MIT license](https://twitter.com/left_pad/status/938825429955125248)!!! And we released a beta.35 for that.
  - So for everyone who had issues with the React license; you'll have the same issue if you are using Babel + regenerator.
- There was a [TC39 meeting](https://github.com/tc39/agendas/blob/master/2017/11.md) this past month, and we documented the proposal changes [here](https://github.com/babel/proposals/issues/34)!
- TC39 now has a comprehensive [contributing guide](https://twitter.com/bterlson/status/931586519592087552)
- The [repl](https://babeljs.io/repl/build/master) supports Flow/TypeScript
- Instead of these meetings, some of us played some Mario Kart instead (#mariokart room in Slack) 🙂  
- I found out there is an event called [FieriCon](http://www.fiericon.com/) and it was this past Nov 18.  
- [No one wants to contribute to Babel 😛](https://twitter.com/AdamRackis/status/931195056479965185)

## Team Updates

- Added @angus-c as a team member. He just wrote our [song](https://twitter.com/left_pad/status/938956634361094146).

> https://medium.com/@angustweets/hallelujah-in-praise-of-babel-977020010fad

Please check it out and send us a recording, maybe we can play in on the website or something?

## Notable PRs

### Add support for extending builtins: [#7020](https://github.com/babel/babel/pull/7020) by [@nicolo-ribaudo](https://github.com/nicolo-ribaudo)

> https://twitter.com/left_pad/status/940723982638157829

This fixes one of our [oldest "caveats"](https://babeljs.io/docs/usage/caveats/#classes) and [issues](https://github.com/babel/babel/issues/4480).

Babel hasn't ever supported this in a main plugin but there have been many previous workarounds and efforts.

### "lazy" option to modules-commonjs [#6952](https://github.com/babel/babel/pull/6952)

Logan has a WIP PR to add a "lazy" option to the commonjs transform. This is inspired by the work @zertosh did on [transform-inline-imports-commonjs](https://github.com/zertosh/babel-plugin-transform-inline-imports-commonjs) which is also used in Yarn.

Basically it rewrites the module to only run the imported file when it's needed.

### [We aren't deprecating the `env` option anymore #6905](https://github.com/babel/babel/pull/6905)

Just [fixing the merging behavior](https://twitter.com/left_pad/status/936687774098444288) instead.

### [Expose `envName` as a Babel option #6834](https://github.com/babel/babel/pull/6834)

You can now use `envName: "something"` in `.babelrc` or pass via cli `babel --envName=something` instead of having to use `process.env.BABEL_ENV` or `process.env.NODE_ENV`

### WIP 7.0 blog post [babel/website#1453](https://github.com/babel/website/pull/1453)

Still need to finish this up, but this will explain some of the other changes we are making in v7

### Prep for async plugins/handlers [#6818](https://github.com/babel/babel/pull/6818)

No implementation but future proofing for later support for async plugins.

### [Port of `babel-plugin-transform-for-of-as-array`](https://github.com/babel/babel/pull/6914)

`["transform-for-of", { "assumeArray": true }]` to make all `for-of` loops output as regular arrays

Ref https://twitter.com/LeaVerou/status/936709376005607424, https://twitter.com/left_pad/status/936721918840983554

```js
for (const elm of array) {
  console.log(elm);
}
```

```js
for (let _i = 0, _array = array; _i < _array.length; _i++) {
  const elm = _array[_i];
  console.log(elm);
}
```

We already have inference for code like: `var arr = []; for (const elm of arr) {`.

### [Exclude `transform-typeof-symbol` in `loose` mode for `preset-env` #6831](https://github.com/babel/babel/pull/6831)

```
[
  "env",
  {
    "loose": true,
    "exclude": [
      "transform-es2015-typeof-symbol" // on by default now
    ],
  }
]
```

A lot of projects are already doing this, so we should just make it a default.

## Notable Issues

### [Switch to a website/blog framework? babel/website#1485](https://github.com/babel/website/issues/1485)

We really want to update the website to add: translation + versioned documentation (v6 and v7). I made an issue to discuss switching to Docusaurus if it's simple enough, or Gatsby?

### https://github.com/MatAtBread/fast-async/issues/46

Working with @matAtWork to merge the `fast-async` Babel plugin which transforms async functions into Promises into the main Babel plugin. This way you will have the option of using `regenerator`, `async-to-generator`, or `async-to-promise`. And maybe we just make them all into a plugin called like `@babel/plugin-async-functions` and then create 3 options. I would like to default to the `Promise` version if we get it robust enough.

### Babel 7 Upgrade tool [babel/notes#44](https://github.com/babel/notes/issues/44)

Want to make a tool that will upgrade your JS, your .babelrc, and your package.json for Babel 7. We can use `babel-codemod` for the JS files and [golden-fleece](https://twitter.com/Rich_Harris/status/937144688590671873) by Rich for JSON files.

### [More representative Babel flow v8/web-tooling-benchmark#27](https://github.com/v8/web-tooling-benchmark/issues/27)

Made an issue to talk about making more representative Babel benchmarks to test against. Can contribute there!

## Todos

> Old todos: https://github.com/babel/notes/blob/master/2017-11/nov-01.md

> Do we resolve .babelrc files in node_modules, or use the cwd or something? https://github.com/babel/babel/issues/6766
> How do we handle polyfills better?
