Babel Weekly Notes - 2017-12-15

> Haven't done a post in a while so will try to add things in the last month.

## News

- I [posted](https://twitter.com/left_pad/status/938041651452416004) I was going to step back from working on Babel as much, so going to do more of a PM role and focus on my health.
  - We're always looking for more maintainers/collaborators so hopefully as I step down others will step up 🤗
- I did AMA on [dev.to](https://twitter.com/ThePracticalDev/status/941007481987268609), still answering some of the questions!
- Also did a podcast on [The Web Platform Podcast](https://twitter.com/TheWebPlatform/status/940855461229793280)
- [Regenerator](https://github.com/facebook/regenerator) was released under the [MIT license](https://twitter.com/left_pad/status/938825429955125248), and we released a beta.35 for that.
  - So for everyone who had issues with the React license, everyone has the same issue if you are using Babel + regenerator.
- There was a TC39 meeting this past month, and we documented some proposal changes [here](https://github.com/babel/proposals/issues/34)
- TC39 has a comprehensive [contributing guide](https://twitter.com/bterlson/status/931586519592087552)
- The [repl](https://babeljs.io/repl/build/master) supports Flow/TS again

> Instead of these meetings, some of us played some Mario Kart instead (#mariokart room in Slack) 🙂
> I found out there is an event called [FieriCon](http://www.fiericon.com/) and it was this past Nov 18.
> [No one wants to contribute to Babel 😛](https://twitter.com/AdamRackis/status/931195056479965185)

## Team Changes

- Added @angus-c as a team member. He just wrote our [song](https://twitter.com/left_pad/status/938956634361094146).

## Notable PRs

### Add support for extending builtins: [#7020](https://github.com/babel/babel/pull/7020) by [@nicolo-ribaudo](https://github.com/nicolo-ribaudo)

> https://twitter.com/left_pad/status/940723982638157829

This fixes one of our [oldest "caveats"](https://babeljs.io/docs/usage/caveats/#classes) and [issues](https://github.com/babel/babel/issues/4480).

Babel hasn't ever supported this in a main plugin but there have been many previous workarounds and efforts.

### "lazy" option to modules-commonjs [#6952](https://github.com/babel/babel/pull/6952)

Logan has a WIP PR to add a "lazy" option to the commonjs transform. This is inspired by the work @zertosh did on [transform-inline-imports-commonjs](https://github.com/zertosh/babel-plugin-transform-inline-imports-commonjs) which is also used in Yarn.

Basically it rewrites the module to only run the imported file when it's needed.

### https://github.com/babel/babel/issues/4480

### We [aren't deprecating the `env` option](https://twitter.com/left_pad/status/936687774098444288) anymore and just fixing/standardizing the merging behavior instead.

### https://github.com/babel/babel/pull/6834

### WIP 7.0 blog post [babel/website#1453](https://github.com/babel/website/pull/1453)

Still need to finish this up, but this will explain some of the other changes we are making in v7

## Notable Issues

### [Switch to a website/blog framework? babel/website#1485](https://github.com/babel/website/issues/1485)

We really want to update the website to add: translation + versioned documentation (v6 and v7). I made an issue to discuss switching to Docusaurus if it's simple enough, or Gatsby?

### https://github.com/MatAtBread/fast-async/issues/46

### https://github.com/babel/notes/issues/44

### https://github.com/v8/web-tooling-benchmark/issues/27
