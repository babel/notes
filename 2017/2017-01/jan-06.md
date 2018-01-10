## January 6/7 ([discuss](https://github.com/babel/notes/pull/11))

> The first "real" meeting! (previous ones were just my notes/ideas)

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

I figured if we were ever going to do a meeting it would make sense for a discussion on what Babel 7 should be! I'm sure glad we did and hope to do more soon!

### Meeting Schedule
- Frequency: once/twice a week/as necessary?
- How: Google Hangouts (maybe try another one if audio delay)
- Need to figure out timezones!
- Should we broadcast it? Would be cool to invite the community in for certain topics/issues to discuss!

### Open Collective
- Got the ok from the team! (I also talked with [Xavier](https://twitter.com/xdamman) 2x in person about Open Collective/Babel/etc).
- Set up Teespring link (Planning on donating the profits back into open collective account so it creates a cycle)
  - Shirts: both christmas one + regular logo?
- Sync the open collective blog post + tshirts link + tweet, etc
- Blogpost: make it clear what the money will be used for: community, etc

### Babel 7

Have minimal user changes while letting us drop Node 0.10/0.12 + cleanup.

- Wiki: https://github.com/babel/babel/wiki/Babel-7
   - https://github.com/babel/babel/milestone/9 (would like help turning ideas into issues and then some PRs).
   - Not sure how much time we want to spend reading through the existing 400+ issues for other changes.
   - Drop Node 0.10/0.12 (everything related to that: loader, gulp, grunt, babelify, lerna).
   - Babel Plugin Versioning/Babylon Versioning.
   - For experimental plugins create internal “plugins” like jsx/flow currently are.
   - Make a 7.x branch and push to that, once ready to publish rebase and make that the new master branch.
   - Use lerna independent mode but sync non-experimental pkgs together (experimental plugins are independent). This is an alternative to making a whole new repo.

### TC39

Thought it would be awesome if we could fund people to go to TC39 via open collective and also have meetings there.

- Be an non-profit (nope!)
- Join a foundation (not sure yet)
- Work at company that is on ECMA (James/Kent, I'm (Henry) at Adobe)

### Getting Contributors

- Put a lot more focus on `beginner-friendly` labeled issues! (in all repos)
 - Example: https://github.com/babel/babel-preset-env/issues/129
- Provide better onboarding experience for contributors as well as collaborators.
  - Updating our docs with labeled issues: https://github.com/babel/babel.github.io/pull/1126
  - Node has awesome docs: https://github.com/nodejs/node/blob/master/doc/onboarding.md
- Talk to schools/teachers/students, partner with orgs like Google Summer of Code?
 - https://twitter.com/left_pad/status/810662070454722560

### Working On

- Andrew: Getting proposals through TC39 (decorators with @wycats), learning the spec/grammar, babel-bot
- Daniel: Make babylon output estree (Issue [#278](https://github.com/babel/babylon/issues/278), PR [#277](https://github.com/babel/babylon/pull/277))
- Logan: Future of Babel (minimal babel-core, fix plugin ordering, perf, debugging)
- Henry: babel-preset-env + babili, Babel 7 release
- Diogo: ES modules, bunch of spec PRs

### Issues/PR Discussions

- After we added Discourse (Community Discussion) in https://github.com/babel/babel.github.io/pull/875 we’ve been getting generic support questions rather than a discussion about that specific page - we should add a message to use slack/github issues for help.
- https://github.com/babel/babel/pull/5057 (mention-bot -> OK)
- https://github.com/babel/babel.github.io/pull/1047 (community resources page website -> No for now)
  - Hard to maintain ourselves; maybe just add to https://github.com/dustinspecker/awesome-babel?
- https://github.com/babel/babel-preset-env/issues/26 (autoprefixer and babel -> config lookup)
- https://github.com/babel/babel/pull/4892 (.babelrc.js -> determine config lookup implications)
  - More error prone, less help from Babel, opt out of babel-init/config manipulation tool.

### Babel-bot

Initial Discussion: https://github.com/babel/notes/issues/8
Repo: https://github.com/babel/babel-bot

Lots of awesome ideas here and should serve as a good base for a generic bot tool for many other oss projects!

---

Please feel free to discuss these notes in the [corresponding pull request](https://github.com/babel/notes/pull/11) or join in on our discussions in [#development](https://babeljs.slack.com/messages/development). (Sign up at [slack.babeljs.io](https://slack.babeljs.io/)).
