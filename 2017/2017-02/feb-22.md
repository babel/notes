## Feb 22 ([discuss](https://github.com/babel/notes/pull/15))

Just wanted to write up some high level updates.

### Babel 7 Updates

- [Planning for Babel 7](https://github.com/babel/babel.github.io/pull/1166): What's going on so far.
- [Upgrade to Babel 7](https://github.com/babel/babel.github.io/pull/1146): Will post this soon and update as we go along for people that want to use it early.

Will do a few pre-releases to test; need to think about upgrade path for oss libraries and everyone else.

### Getting Contributors

- Big focus on creating guided [`beginner-friendly`](https://github.com/babel/babel/issues?q=is%3Aissue+label%3Abeginner-friendly+is%3Aclosed) issues for Babel 7: it's been really awesome to see the majority of the changes coming from new contributors!

[![Imgur](http://i.imgur.com/5Bndqfn.png)](https://github.com/babel/babel/issues/5184)

- We're accepted to [Rails Girls Summer of Code](https://teams.railsgirlssummerofcode.org/projects/177-babel) as well as [Google Summer of Code](https://summerofcode.withgoogle.com/organizations/5842528113786880/)! Say "Hi" in the [#summer-of-code](https://babeljs.slack.com/messages/summer-of-code) Slack channel. ([signup link](https://slack.babeljs.io/))
- How can we reach out to companies that are using Babel for contributions/maintaince help?
- Open Collective?

If you have any suggestions on how we can do more, please reach out! (comment here, join [Slack](https://slack.babeljs.io/), or [Twitter](https://twitter.com/babeljs).

### Team Additions

We've added a few folks as collaborators along the way!

| Name | Aaron Ang | Artem Yavorsky | Samuel Reed | Sergey Rubanov | 
|---|---|---|---|---|
| github | [@aaronang](https://github.com/aaronang) | [@yavorsky](https://github.com/yavorsky) | [@STRML](https://github.com/STRML) | [@chicoxyzzy](https://github.com/chicoxyzzy) |
| twitter | [@_aaronang](https://twitter.com/_aaronang) | [@yavorsky_](https://twitter.com/yavorsky_) | [@STRML_](https://twitter.com/STRML_) | [@chicoxyzzy](https://twitter.com/chicoxyzzy) |

- Aaron just joined our slack this *past week* and has been super excited about getting involved: made a few PRs and efforts to improve our site and contributing docs.
- Artem has been making a lot of great PRs to babel-preset-env and is also getting started with other stuff.
- Samuel has made most of the PRs for fixing the bugs that we've having with the react constant elements plugin as well as added discourse comments support to our docs pages.
- Sergey helps maintain compat-table and has been helping with babel-preset-env.

### Future Discussions

> babel-preset-env and its future

Should preset-env be in core? How can it be better integrated with babili/webpack?
Should Babel have a dependency system based on what syntax/built-ins each plugin transforms/supports? Babili should be able to output either arrow functions (ES6) or function expressions (ES5) without explicit options since the environment can be passed down from preset-env.

> Performance metrics

What if Babel could output the difference between the source and output code per file, e.g. difference in file size, lines of code, performance, and make users more aware of how transforms work?

---

Please feel free to discuss these notes in the [corresponding pull request](https://github.com/babel/notes/pull/15) or join in on our discussions in [#development](https://babeljs.slack.com/messages/development). (Sign up at [slack.babeljs.io](https://slack.babeljs.io/)).
