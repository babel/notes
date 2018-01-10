# Babel Team Meeting - 2017-08-30

## Attendees

- Peeyush
- Brian
- Logan
- Henry

> We skipped the last meeting since no big changes, Henry went to speak at [React Rally](http://www.reactrally.com/).

## Priority: Babel 7 Beta

- Remember to label things as breaking so we can document them in the blog post. https://github.com/babel/babel/issues?q=label%3A%22tag%3A+breaking+change%22+is%3Aclosed
- Not much to talk about here! Because it's taking so long, we will just publish a new alpha ([alpha.20](https://github.com/babel/babel/releases/tag/v7.0.0-alpha.20)), and then beta soon after assuming no issues to get the ball rolling.
 
## PRs to look at
- https://github.com/babel/babel/pull/5710
- https://github.com/babel/babel/pull/4935
- Private methods parser PR: https://github.com/babel/babylon/pull/703 by Karl
- Decorators transform PR: https://github.com/babel/babel/pull/6107 by Peeyush
- Private class props PR: https://github.com/babel/babel/pull/6120 by Justin

## Discussion (mostly maintainence related)
- [x] Need to move the `7.0` branch to become `master`, and make `master` into `6.x` (same with babel-preset-env). Done in https://github.com/babel/babel/commit/0189b387026c35472dccf45d14d58312d249f799 in Babel.
  - Lesson learned: don't many longstanding branches (already knew this), and just make `master` what everyone is working on and make separate branches for backports `6.x`, etc. Also don't do backports: time to cherry pick, deploy, backport bug fixes!?, maintain, etc.
- [ ] We should move babylon back into the monorepo? Looks like @danez is looking into this.
  - Reasons: easier release cycle, less chance of breaking stuff (have to have a script in this repo just for the smoke test against babel itself which is unnecessary), easier to write code to transform what is newly parsed (this is forgotten a lot actually), no need to redirect issues to another repo, duplicate issues/labels.
  - It's true the parser is very separate from the rest, but in the end it's specific to Babel else someone can else acorn/esprima/etc. Why have a one-off package; if it's hard to release then it's reason to fix/not use Lerna to release
  - Issue: may want to transfer the git history, and will need to merge the issue labels and issues and prs eventually.
  - Will need to merge the testing frameworks since babylon uses ava, babel uses mocha, and some wanted to use jest (but there was previously issues of it being slow/hard to debug)
  - Need to move the issues over, PRs eventually, and also issue label consolidation (rethink that possibly)
- We should move [babel-preset-env](https://github.com/babel/babel-preset-env) in as well: we weren't sure since it was an experiment but now it makes sense as it's stable now.
- `babel-standalone` build is slow, may be a combination of having to use webpack on it + duplicate packages somewhere.
- Discussion about having an async traversal/visitor: to do this would need to make a breaking change since supporting both sync/async would be hard to maintain. Goes back to Logan's older plan to separate plugins from traversal: https://github.com/babel/notes/blob/master/2016-08/august-01.md#proposed-resolution. Having an async mode would also mean it wouldn't work with `babel-register` either.
- How do we help the community itself come up with syntax proposals rather than wait for a TC39 Champion?
  - Links on current status: we currently only accept Stage 0 proposals (something a champion will propose) https://github.com/babel/babylon/#will-babylon-support-a-plugin-system, https://github.com/babel/proposals#when-does-babel-implement-new-features
  - But don't think we want to be a blocker to others trying out their own ideas: don't want to just open the plugin system so they everyone makes their own syntax and soon a bunch of libraries/repos all have this weird syntax.
  - At the same time, maybe be limiting for proposals only to come from TC39 (big companies, larger barrier to entry). Shouldn't innovation also come from the community itself, not just feedback on existing proposals? Need to balance the two.
  - Idea: just document better how you can fork babylon and pass a different version of it into babel (`parserOpts`).
  - Idea: allow the repl to have a pluggable parser similar to what we are doing with babel-standalone/PRs, so at least people can test a syntax easily on our website to share ideas/concepts (without having to publish on npm).
