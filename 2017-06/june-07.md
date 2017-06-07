# Babel Team Meeting - 2017-06-07
 
## Attendees
- Boopathi Rajaa
- Daniel Tschinder
- Diogo Franco
- Henry Zhu
- Jon Major Condon
- Kara de la Marck
- Karl Cheng
- Nathan Hammond
- Robert Jackson
- Peeyush Kushwaha
- Sven Sauleau
 
## Actions
 
- [X] (Nathan) Publish meeting notes.
- [ ] (Nathan) Promote priority task for this week.
 
## Discussion

> Use http://slack.babeljs.io/ to join our Slack

### Plugin Ordering Updates
- [#plugin-ordering](https://babeljs.slack.com/messages/plugin-ordering) on Slack!
- Large team! @sarupbanskota, @ncantelmi, @jonmajorc, @karadelamarck, @danez, @rwjblue, @hzoo, and more!
- @ncantelmi has a few proposals we want the core team to weigh in on: https://docs.google.com/document/d/1zO1QiaAyDxmA1OcmdOKYLFmuSXGSr4S50pE0uQFTVEE/edit?usp=sharing
  - Deprecating unnamed plugins in Babel 6.
  - Require plugins to have names in Babel 7 (better error messages).
  - Ordering based solely on plugin name, not `capabilities`.
  - Eliminate `passForPreset`.
- Deprecation guide and website updates.
- Will continue approximately one more week.

#### Thoughts
- Initial idea of capabilities was just for syntax anyway.
- We have multiple transforms for async functions, so capabilities would allow one to "win."
  - If we do a good job on the syntax plugins then we don't expect the community to implement this sort of thing and we remove duplication.
- Macro expansions ... don't really care which one is used, just run one before it.
  - In this case the author of the plugin could specify `after` for each of the plugins which are valid.
- Users will definetely have conflicting plugins, will need to provide messaging.
- Normally use plugin name and then use `capabilities` as an escape hatch?

### Class Fields

- [#proposal-class-fields](https://babeljs.slack.com/messages/proposal-class-fields) on Slack!
- Daniel Ehrenberg (@littledan) is working on the spec for TC39.
- Propose strike team for Diego and interested parties.

### Decorators

- [#proposal-decorators](https://babeljs.slack.com/messages/proposal-decorators) on Slack!
- Diego Ferreiro Val (@dval) has volunteered to participate in this effort.
- Peeyush (@peey) has begun researching what the effort would entail.
- Getting more TC39 people involved to get the proposal moving forward.

> Rob: maybe make sub-group/meetings for proposals

### Priority Topics!

- [Better error messages.](https://github.com/babel/babylon/issues/169)
- [Use Babylon ESTree plugin.](https://github.com/babel/babel-eslint/issues/440) (to unblock a future task of [ESLint failing tests](https://github.com/babel/babel-eslint/issues/62)) @kaicataldo
- Have volunteers for this week already, going to rope in people who have already volunteered to help mentor.

### Other Topics

- [#proposal-opt-chaining](https://babeljs.slack.com/messages/proposal-opt-chaining) on Slack! (a?.b?.c)
  - PR has been made ([#5813](https://github.com/babel/babel/pull/5813)), but spec is still in flux. See [tc39/proposal-optional-chaining#2](https://github.com/tc39/proposal-optional-chaining/issues/2) and [tc39/proposal-optional-chaining#3](https://github.com/tc39/proposal-optional-chaining/issues/3).
- Numeric Separator (1_000) [transform](https://github.com/babel/babel/tree/7.0/packages/babel-plugin-transform-numeric-separator) is already released in 7.0.0-alpha.12 (Rick Waldron)
  - Has open question about exponentiation.
- Boopathi will begin integration testing `babel-preset-env` + `babili` over the next week.
- Begin thinking through cross-process caching.
  - Logan has been doing a lot of caching work (for configs but wanted to apply it to files)
