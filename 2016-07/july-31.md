## July 31 ([discuss](https://github.com/babel/notes/pull/1))

#### In Slack (at the time)

* [Henry](https://twitter.com/left_pad)
* [Logan](https://twitter.com/loganfsmyth)

> And since this is the first one we're doing, I'm adding a lot of other stuff we've talked about previously.

#### Others on the team

* [Amjad](https://twitter.com/amasad)
* [Juriy](https://twitter.com/kangax)
* [James](https://twitter.com/thejameskyle)
* [Sebastian](https://twitter.com/sebmck)
* [Jesse](https://twitter.com/mccjm)
* [Daniel](https://twitter.com/tschinderdaniel)

### Moving from [Phabricator](https://phabricator.babeljs.io) back to Github issues ([`repo`](https://github.com/babel/phabricator-to-github))

> https://twitter.com/left_pad/status/747624971627806720

Back then, Sebastian was [dealing with](https://medium.com/@sebmck/2015-in-review-51ac7035e272) the issues mostly by himself before other people joined in to help. Like he mentions, it is easy to feel pressured, burned out, and discouraged by some of the negativity in the community.

At the time, github issues wasn't helping much since a lot of the issues were duplicates (after a regression), users asking for help instead of actual bugs, issues with no information, etc. It was easy to look for other services that gave maintainers more say to help solve this issue. 

This wasn't anything bad on [Phabricator's](https://www.phacility.com/) part: it provided a lot of benefits including being able to specify custom fields so users could input their Babel version, `.babelrc` config, as well as input/output code.

Many people have said that they haven't submitted issues to Babel (whether it be bugs or not) because of the unfamiliarity of phabricator. Most are expecting github issues (especially since the rest of our repo and pull requests are there). Instead what we got were more people reporting things through the [website repo](https://github.com/babel/babel.github.io) about babel itself, commenting on commits, etc. When you are trying to get new contributors when talking at meetups or open source events, it just becomes another barrier to contribution. Github has also recently added some features for maintainers.

#### Plan

Migrate updates to existing issues and create new issues for issues started on Phabricator using github's issue API.

@danez has done a great job getting this effort started:  https://github.com/babel/phabricator-to-github. There's also a [TODO issue](https://github.com/babel/phabricator-to-github/issues/2).

### Preset Options ([PR #3331](https://github.com/babel/babel/pull/3331))

[There are babel presets](https://www.npmjs.com/search?q=babel-preset-) for like every version of node, browser and different combinations for webpack, loose mode, etc.

I think it's safe to say we need something like this now? We need to decide what we want a preset to be able to do. Should it allow blacklisting (people ask about this a lot) or anything a user wants? Or just provide the common use cases as options. Many people are confused/frustrated about presets/configuration so this should help a bit.

After this change, we can modify the es2015 preset to provide options to turn off the commonjs transform and to turn on loose mode (very commonly asked). This would also be a prereq to making a preset that acts as a "autoprefixer" for babel [#3476](https://github.com/babel/babel/pull/3476).

### Codemods ([PR #3561](https://github.com/babel/babel/pull/3561))

Just have to modify the PR to resolve a module that acts as the babel parser/generator so we can use something like recast to generate code that retains formatting. Ref [mohebifar/lebab#138](https://github.com/mohebifar/lebab/issues/138)

### `babel-preset-latest`

We should probably do another [poll](https://twitter.com/left_pad/status/758429846594850816) for the name...

Given the es20xx presets only transform each year’s transforms, I think many would appreciate a way to include everything that has been standardized so far. This includes everything in stage-4 and everything es2015+. This wouldn't be difficult to add.

So instead of doing:

```js
{ "presets": ["es2015", "es2016", "es2017", ...] }
```

```js
{ "presets": ["latest"] }
```

### `babel-preset-env` (autoprefixer for babel) [PR #3476](https://github.com/babel/babel/pull/3476)

> Again the name could be changed here as well.

This would probably replace the usage of `babel-preset-latest` but would take some more work to setup. 

Ref https://twitter.com/samccone/status/722826060161617923
Ref https://gist.github.com/addyosmani/bb6e2939f943226e68e87396c4931040

The basic idea is that we write down in a config somewhere of all javascript features that each environment supports. Then the user can specify in their options what target features they want to use (es2015, etc) and a target environment[s]. We calculate the least common denominator set of features of the environments to figure out which transforms to apply.

So if you choose to write `es2015` code and target only chrome 51, then the preset would only set the `commonjs` transform to transpile modules only since chrome supports the only transforms natively. But if you also targeted a lower version of IE would turn on all transforms.

### an `es2017` preset

Given async functions and trailing function commas are [stage 4 now](https://github.com/tc39/proposals/blob/master/finished-proposals.md), we'll make another preset.

#### Future of Babel's release process and its ecosystem

[Babel 6](https://babeljs.io/blog/2015/10/29/6.0.0) was released almost a year ago. In v6, Babel was separated into many packages while moving those packages into a ["monorepo"](https://github.com/babel/babel/blob/master/doc/design/monorepo.md). The way we currently publish package is using "fixed" global version so that when we make a release, we update all changed packages to that new version and thus packages aren't completely independent (this is explained more in the [lerna readme](https://github.com/lerna/lerna#fixedlocked-mode-default)).

We would like to switch to a versioning mode such that each package is versioned independently of each other. However, there are some complications to this due to the way babel is setup (interdependencies) and other implications that effect will have on the babel ecosystem of presets/plugins. It makes publishing more difficult until we setup some better tooling in lerna to give suggestions of what version to do for each updated package. It also complicates new user's setups regarding which version of which package they should use, and how plugin/preset authors can update to the latest dependencies.

Logan:

Let's be totally clear here, a lot of people use Babel 6, like just tons. Currently their workflow is to just npm install the presets you need. That's easy. In a static world, there is nothing wrong with allowing the major versions of presets to drift ahead of the core, but only if we are confident that the transformation framework won't change.

That is the source of my fear. I think to continue being a good tool for people, that needs to be able to change over time, and the current system makes that very difficult.

I'd like to drive that change to the core transformation system. I think we need it.

Given that, if we bump the presets now, say we have babel-core@6 and babel-preset-es2015@7, that's fine, but what happens when we need to change the core, so we have babel-core@7 and babel-preset-es2015@10, how do users who are still on Babel 6 know what version of the plugins they need? The large group of users who will still definitely be on Babel 6 for a while, will feel that pain because every time they need to install something, they have to go look up the versions or won't think about it and will install the newest without thinking.

What I'm arguing for is essentially for us to trim down the "core" of Babel to the smallest possible piece that we reliably thing won't change, or can be changed backward-compatibly. Then we could 100% easily version things separately. That would include the presets, the helper utils, and everything. I'd like for `babel-core` itself to essentially have no dependencies on other babel-* packages.

So I have this vision of where we'll be, and I worry that splitting the versions too early will hurt the users that we have who will be on Babel 6 for a while, because they will have no way of easily knowing what versions of things are safe to use on Babel 6.

it's obviously not out of the question, but we'd really need to make sure our documentation and error messages are absolutely on point so users wouldn't get user confused in the future

##### Potential Solutions/Workarounds

Better tooling (with [Lerna](https://github.com/lerna/lerna) and others like greenkeeper and semantic-release).

davidpfahler on slack explains: we could take advantage of npm dist tags such that each plugin/preset is compatible with a certain tag rather than a version itself. `npm install --save-dev babel@a babel-preset-es2015@a`.

It sounds kind of crazy but it would be awesome to have a bot (maybe just an update for greenkeeper) that will codemod/suggest changes to all babel plugin/preset repos on github. So when we make a change that requires plugins to update we can do a lot of the work for them. Maybe even a "reverse greenkeeper" view where library/tool authors can have a dashboard of projects, whether a release caused regressions and to follow up, to follow repos that use the library as a dependency, etc.

### Contributions

How can we encourage more contributions from the community?

Like most open source projects, our team is small, with very few resources to look at issues let alone pull requests. And at moment, it's mostly two of us looking at phabricator on a consistent basis.

What we're doing now:

- Active on Twitter (posting releases, answering questions)
- Discussing development on Slack
- These discussion notes
- Switching back to github issues
- Trying to follow other repos (it would be cool to watch a repo/issues only for certain keywords)
- Other efforts (https://github.com/thejameskyle/babel-handbook)
  - Talks: https://www.youtube.com/playlist?list=PLUjGYjn761TW_j4HlBcq_qnJoaSMTlJOH 

What else can we do?
- Teaching (https://github.com/thejameskyle/the-super-tiny-compiler)
- More docs on APIs, how to make a plugin (https://www.sitepoint.com/understanding-asts-building-babel-plugin/)
- Easier set up in development?

### babel-minify

Some may know that we have plans to release a minifier using Babel (ES6+ aware). A lot of folks have been asking for one, especially now since many browsers implement ES6 and we want to ship ES6 code without transpiling but also minify it.

Since we're still working through some things, we just want to say that it's in development and to stay tuned for more details real soon!

------------

Please feel free to discuss these notes in the [corresponding pull request](https://github.com/babel/notes/pull/1) or join in on our discussions in [#development](https://babeljs.slack.com/messages/development). (Sign up at [slack.babeljs.io](https://slack.babeljs.io/)).
