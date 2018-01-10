Babel Team Meeting - 2017-08-02

## Attendees

- Henry
- Kara (RGSoC)
- Emma (RGSoC)
- Peeyush (GSoC)
- Sarup
- Daniel

> Focus for this week is to get Babel ready for a beta release, hopefully plugin authors can/will join us in making the RC/final release better!

## Releasing Babel 7

Babel 7 tasks for beta: https://github.com/babel/babel/milestone/9 (not that many)

- Made https://github.com/babel/notes/issues/30 to check meta issues for those upgrading.
- Release the beta after merging the rest of the milestone PRs (and testing in Babel itself for regressions). Henry will update the Behance apps as well and then we can broadcast.
- Reach out to plugin authors to upgrade and leave feedback, work with the well known projects to upgrade beforehand

## Other Topics

- https://github.com/babel/proposals/issues/19 July TC39 Meeting
- From last week: (test infra) test262, smoke tests, testing the "master" version of Babel on itself
- Sarup PRs: https://github.com/babel/babel/pull/5923, https://github.com/babel/babel/pull/5925
- Babel helpers issue by Peeyush: https://github.com/babel/babel/issues/6030

## Other PRs to Review
- https://github.com/babel/babylon/pull/654: Adding test262 to babylon! This will help us make it more robust (whitelist failing tests, slowly add them back and prevent more regressions).
- https://github.com/babel/babel.github.io/pull/1284 Ability for the REPL to use built versions of Babel from any PR (using CircleCI)! This is amazing!!!
  - https://github.com/babel/babel/pull/6029 depends on this PR
- https://github.com/babel/babel.github.io/pull/1279 Peeyush's blog post after I finally write the SoC one
- https://github.com/babel/babel/pull/5971 babel-types refactor/fixes
- https://github.com/babel/babylon/pull/178 - better syntax errors from Babel
