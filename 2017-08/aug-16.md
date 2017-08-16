# Babel Team Meeting - 2017-08-16

## Attendees

- Peeyush
- Emma
- Kara
- Logan
- Henry

## Discussion

- Peeyush: Decorators PR helpers use ES6 so it fails on Node 4.
  - Ideally we would compile the helpers separately to ES5 or do it based on preset-env/babelrc
  - Logan: Constant issue of what should we do right now for 7.x vs. later?
  - Logan: had earlier PR https://github.com/babel/babel/pull/5706, brought up the issues we had with compiling `typeof` helper on itself recursively.
  - Conclusion: may need to write in ES5 (or always compile down to ES5) for the moment.
- Henry: been busy and giving a talk at [React Rally](https://reactrally.com) next week 
- Emma: working on codemod for let/const
  - Henry: Brian had a suggestion for a codemod for decorators: `@foo export default class {}`
- Henry: Logan/someone should switch all the repos from `7.0` to `master` and `master` back to `6.x`. (Let's use `master` in the future, and `x.y` for any backports).
- Will post Karl's post. Done: https://twitter.com/left_pad/status/897890141171101696

### Focus: Babel 7 Beta

Just need to review 1 PR: https://github.com/babel/babel/milestone/9. Everyone is having fun getting distracted by other things 🙂

---

## Project Updates

### Team
- Added @bvaughn to the Website team, @Daniel15 as admin for website
- Added @nicolo-ribaudo to team last week

### Misc Updates
- Renamed repo: `babel/babel.github.io` to `babel/website`: https://github.com/babel/website
- Renamed repo: `babel/babili` to `babel/minify` (and package from `babili` to `babel-minify` https://twitter.com/_vigneshh/status/897074585891479554: https://github.com/babel/minify
- Merged the React rewrite of the REPL (https://github.com/babel/website/pull/1297) but have the `New Repl` milestone to work on: https://github.com/babel/website/pull/1297, test out the new repl at: http://babeljs.io/repl2
- `babel-standalone` is in the monorepo https://github.com/babel/babel/pull/6029, https://github.com/babel/babel.github.io/pull/1284 https://twitter.com/left_pad/status/896361066543947776 with support for npm/circle ci builds. Soon @babel-bot will post a link to the REPL for each PR.
- Published @peey's post https://twitter.com/left_pad/status/896036669631102976
- Updates to Stages: https://github.com/babel/babel/pull/6071 @rwaldron, https://github.com/babel/babel/pull/6076 @kedromelon, https://github.com/babel/babel/pull/6080 @echo304
- Made a 6.26.0 release: https://github.com/babel/babel/releases/tag/v6.26.0
- @drewml gave a Babel talk on 8/15: https://twitter.com/drewml/status/896803907267170305
- @hzoo did a talk about Babel/OSS at Spotify 8/11: https://twitter.com/SpotifyEng/status/896118410899148801

### Summer of Code
- https://twitter.com/left_pad/status/897470712277028864: @peey submitted a PR for decorators: https://github.com/babel/babel/pull/6107

### Other PRs to review

- Milestone PR: https://github.com/babel/babel/milestone/9
- Revitalized the syntax error PR https://github.com/babel/babylon/pull/658
- Simpler import syntax output https://github.com/babel/babel/pull/6039
- `babel-eslint` refactor for ESLint changes by @JamesHenry: https://github.com/babel/babel-eslint/pull/509

---

Help
