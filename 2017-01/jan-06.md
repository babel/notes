## January 6/7 ([discuss](https://github.com/babel/notes/pull/11))

Attendees: 

Jan 6th

- [Brian](https://twitter.com/existentialism) ([@existentialism](https://github.com/existentialism))
- [Diogo](https://twitter.com/kovnsk) ([@kovensky](https://github.com/kovensky))
- [Henry](https://twitter.com/left_pad) ([@hzoo](https://github.com/hzoo))
- [Logan](https://twitter.com/loganfsmyth) ([@loganfsmyth](https://github.com/loganfsmyth))

Jan 7th

- [Andrew](https://twitter.com/drewml) ([@drewml](https://github.com/drewml))
- [Daniel](https://twitter.com/TschinderDaniel) ([@danez](https://github.com/danez))
- [Henry](https://twitter.com/left_pad) ([@hzoo](https://github.com/hzoo))
- [Logan](https://twitter.com/loganfsmyth) ([@loganfsmyth](https://github.com/loganfsmyth))
- [Sven](https://twitter.com/svensauleau) ([@xtuc](https://github.com/xtuc))

### Meeting Schedule
- Frequency? (once a week?)
- How: Google Hangouts (maybe try another one if audio delay)

### Open Collective
- Just got to ask Xavier to flip the switch for open collective
- Set up teespring link without guy fieri (donate profits back into open collective account)
- Sync the open collective blog post + tshirts link + tweet, etc
- Shirts: both christmas one + regular logo?
- Blogpost: make it clear what the money will be used for: community, etc

### Babel 7
 - https://github.com/babel/babel/wiki/Babel-7
   - Drop Node 0.10/0.12 (everything related to that: loader, gulp, grunt, babelify, lerna)
   - Babel Plugin Versioning/Babylon Versioning
   - For experimental plugins create internal “plugins” like jsx/flow currently are
   - Make a 7.x branch and push to that, once ready to publish rebase and make that the new master branch
   - Use lerna independent mode but sync non-experimental pkgs together (experimental plugins are independent). This is an alternative to making a whole new repo.

### TC39

Thought it would be awesome if we could fund people to go to TC39 via open collective and also have meetings there.

- Need an non-profit (nope!)
- JS foundation (not sure yet)
- or work at company that is a ECMA meber (got James/Kent, Henry is at Adobe)

### Getting Contributors

- Put a lot more focus on beginner-friendly labeled issues
- Provide better onboarding experience
- Can’t be perfectionist
- Talk to schools/teachers/students, partner with orgs like Google Summer of Code?

### Website

- After we added Discourse (Community Discussion) in https://github.com/babel/babel.github.io/pull/875 we’ve been getting generic support questions rather than a discussion about that specific page - we should indicating a message to use slack/github issue for help.
- More documentation pages on contributing/maintaining

### Working On

- Andrew: getting proposals through tc39, spec/grammar
- Daniel: make babylon output estree
- Logan: future of Babel (minimal babel-core, fix plugin ordering, perf, debugging)

### PR Discussions

- https://github.com/babel/babel/pull/5057 (mention-bot -> OK)
- https://github.com/babel/babel.github.io/pull/1047 (community resources page website -> No)
  - Hard to maintain ourselves
  - Maybe just add to https://github.com/dustinspecker/awesome-babel?
- https://github.com/babel/babel-preset-env/issues/26 (autoprefixer and babel)

- https://github.com/babel/babel/pull/4892 (.babelrc.js)
  - More error prone
  - Less help from Babel 

### Babel-bot
https://github.com/babel/notes/issues/8
https://github.com/babel/babel-bot

---

Please feel free to discuss these notes in the [corresponding pull request](https://github.com/babel/notes/pull/11) or join in on our discussions in [#development](https://babeljs.slack.com/messages/development). (Sign up at [slack.babeljs.io](https://slack.babeljs.io/)).
