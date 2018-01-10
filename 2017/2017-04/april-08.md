## April 8 ([discuss](https://github.com/babel/notes/pull/19))

> Members who were at this past meeting: Boopathi, Logan, Sven, Henry

### Getting Contributors

- [Rails Girls Summer of Code](https://teams.railsgirlssummerofcode.org/projects/177-babel) submissions are in. Next on the timeline is waiting for acceptance letters on May 1.
- [Google Summer of Code](https://summerofcode.withgoogle.com/organizations/5842528113786880/): We're reviewing applications at the moment.
- How can we reach out to companies that are using Babel for help? We Had some fun with a small little April Fools joke that sparked more serious discussion about OSS and funding. We'll be talking to some interested companies/teams that want to contribute dev time to the project (keep reading to check our proposed roadmap below).
- We're on [Open Collective](https://opencollective.com/babel) now! Better than funding, we'd encourage you to ask your employee to donate, or for them to donate dev time to the project to help us out.

If you have any suggestions on how we can do more, please reach out by commenting here, on [Slack](https://slack.babeljs.io/), or on [Twitter](https://twitter.com/babeljs).

### Team Additions

Some TC39 folks are joining us as collaborators! They've either been awesome in making issues for spec compliancy, helping out in slack, and/or implementing parser/plugin proposals.

- [Jordan Harband, @ljharb (Airbnb)](https://github.com/ljharb)
- [Sathya, @gsathya (Google/v8)](https://github.com/gsathya)
- [Kevin Gibbons, @bakkot (Shape Security)](https://github.com/bakkot)

### Proposed Team Structure/Governance
* Who is on the team?
    * Add them to the team page - [babel/babel](https://github.com/babel/babel#team)
    * We should designate area/project leads (putting the current people below)
    * [Overall](https://github.com/babel) - Henry
    * [Core](https://github.com/babel/babel) - Logan
    * [Parser](https://github.com/babel/babylon) - Daniel
    * [Minify](https://github.com/babel/babili) - Boopathi
    * Stage/Experimental Plugins (TC39) - Preferably someone involved with TC39 a lot, maybe Jordan?
    * [Docs](https://github.com/babel/babel.github.io) - Henry (Maybe Brian/Sven)
    * [Webpack Integration](https://github.com/babel/babel-loader) - Daniel
    * [ESLint](https://github.com/babel/babel-eslint) - Henry (Preferably Kai since on the ESLint also)
    * [Social/Evangelism](https://twitter.com/babeljs) - Henry
    * Releases - Henry (via Lerna)
    * Probably specific leads for Flow/TypeScript/React?
    * (this is just the current state of things, can change)

> Sidenote: Would moving babel-eslint to its respective organization be better? What about babel-loader?

* What does it mean to be a core member/lead? NPM publishing rights 
* What does it mean to be a member? GitHub commit bit
* How does that evolve? Write documentation for a promotion strategy (Contributor -> Member -> Core Member)
* How do people become inactive?
    * Keep members in the org, but move them to a separate team without commit rights
    * Move them to the "inactive" section on our team page

> Sidenote: Move to an npm org so we can easily add/remove people!
> Need to email npm support to get around a current bug with transferring a package to an org

## Team meetings!

* Frequency: Once a month, at least
* Time: Need to schedule this out since we have members in many different timezones
* Content: Agenda proposals + "What are we doing", "What's missing", "What are our priorities"

## Proposed Babel Roadmap

> What we should be working on (at a high level) to move the project forward?

* Fix plugin ordering and/via capabilities discovery (made [#5623](https://github.com/babel/babel/issues/5623))
    * Plugins provide a function to state the capabilities it provides and which it needs
    * This includes both syntax and built-ins
    * This is important to fix plugin ordering automatically in Babel itself. If the `classes` plugin transpiles classes and `decorators` run over classes, then with this information Babel will know to make decorators run first.
    * This would also provide better error messages: "your native environment doesn't support this syntax and you haven't added the correct plugin to transform it: here are some options and how to install"
    * Another test can be to randomly sort the plugins in preset-env/es2015 and check if the output is the same.
    * Minify can also take advantage of this by having multiple outputs based on the target environment (output arrow functions (ES6) if available)

> Ref [babel-plugin-transform-decorators-legacy](https://github.com/loganfsmyth/babel-plugin-transform-decorators-legacy#note-order-of-plugins-matters), [#256](https://github.com/babel/babel-preset-env/issues/256), [RFC Explicit Plugin Ordering](https://github.com/babel/babel/issues/4488), [#4882](https://github.com/babel/babel/issues/4882), [#4117](https://github.com/babel/babel/issues/4117), [Lossy Visitor](https://github.com/babel/babel/pull/3335), [passPerPreset](https://github.com/babel/babel/pull/3281)

* [Babel-Minify 1.0](https://github.com/babel/babili/milestone/4)
    * With the amount of interest in preset-env, there should be an equal if not greater amount of want for an ES2015+ minifier
    * Setup smoke tests, test on major OSS repos using ES6
    * Fix scoping in Babel or visitor traversal if necessary to make this happen.
* How should Babel deal with compiling `node_modules` and handling `.babelrc` files in libraries
    * Babel wasn't designed to run over node_modules but this is becoming more common as npm package authors are targeting Node 4, etc.
* Move babel-preset-env into core (or a package (like `babel`) that includes it by default)
    * If we bake in capabilities discovery, it makes sense to be able to just install babel and it to work without env (no reason not to)
* User workflow improvements (babel-init, default safe preset-env, etc.)
    * Fix first time setup, upgrades, good defaults

### Babel 7 Updates

- [Upgrade to Babel 7](https://github.com/babel/babel.github.io/pull/1146): We posted this for the alpha versions already (currently v7.0.0-alpha.7). We don't make any guarantees about not breaking things between those versions (we are using it at Behance though).

---

Please feel free to discuss these notes in the [corresponding pull request](https://github.com/babel/notes/pull/19) or join in on our discussions in [#development](https://babeljs.slack.com/messages/development). (Sign up at [slack.babeljs.io](https://slack.babeljs.io/)).
