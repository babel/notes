# Babel Team Meeting - 2017-06-21 ([discuss](https://github.com/babel/notes/pull/23))
   
## Attendees
- Henry Zhu
- Karl Cheng
- Nathan Hammond
- Sarup Banskota
- Daniel Tschinder
- Kara de la Marck
- Peeyush
- Brian Ng
 
## Actions
 
- [x] (Nathan/Henry) Publish meeting notes.
 
## Discussion

### Plugin Ordering

- Need reviewers.
- https://github.com/babel/babel/pull/5842/

### Inline Parameters (PR)

- https://github.com/babel/babel/pull/5751 by @peey
- Moves the parameters into the function body so that the normal rest spread can be reused.
- Not a separate visitor, instead it's a method on the path object `fnPath.inlineParameters()`
- Object Rest Spread had bugs because logic was duplicated in paramters transform.
- Counts as a refactor of Henry's code.
- Request of additional documentation.
- Handles default parameters (including spread), rest, ObjectPattern and ArrayPattern

### TypeScript in Babylon

- Andy's PRs: https://github.com/babel/babylon/pull/523, https://github.com/babel/babel/pull/5856
- Lots and lots of code, it's kind of a patch bomb.
- Doesn't appear to be many changes to core Babylon.
- Most of the code is in the plugin.
- If the core changes make sense, and are reasonable, we can defer to Microsoft for maintenance of anything they've upstreamed.
- Is there any particular reason for us to include the plugin in core?
- Overwriting methods is a bit sketchy in terms of maintenance. Tradeoff is in plugin code complexity vs. core complexity.
- Who owns maintainership? How do we ensure ongoing partnership?
- Will rely on community to push this forward.

### babel-eslint

- Merged a [PR](https://github.com/babel/babel-eslint/pull/489) from Daniel that lets us remove a lot of code from `babel-eslint` by using Babylon's ESTree plugin.
- ESLint has a [PR](https://github.com/eslint/eslint/pull/8755) to make parser integration easier by exposing an API for handling scope analysis and AST traversal. This should let us remove even more code out of `babel-eslint`.
  - Currently, `babel-eslint` changes the default config and sometimes assumes script vs. module sourceType. We should figure out if we can avoid this.
  - Possibly add another Babylon plugin for ESLint so that we don't have to mutate the AST afterward, effectively making `babel-eslint` a minimal wrapper.
- We should set up additional conversations with the ESLint team.

### Meeting Times

- We should try another time or switch?
- 9am Eastern half time
- 12pm Eastern other half

### Proposals

> TC39 May notes posted: https://github.com/rwaldron/tc39-notes/blob/master/es8/2017-05/summary.md

#### Dashboard: Babel Status on Proposals

> https://twitter.com/left_pad/status/876881456517263360

- We should to have one place to show the progress of Babel on TC39 proposals.
- https://github.com/babel/proposals: (just copy-pasted at the moment).
- Make it easier to track (make an meta-issue for each proposal instead of one in babylon/babel?)
- Sergey, making something that is more like compat-table 2.0 (at some point)
  - Link to test262 tests https://twitter.com/left_pad/status/876910325815287809
  - Leo Balter, Brian Terlson are interested.

### Updates

- BigInt: @wdhorton has a [Babylon PR](https://github.com/babel/babylon/pull/588) open.
- Class Fields Updates: Karl as a branch with some initial work on it (not a PR yet) and a new [parser PR](https://github.com/babel/babylon/pull/589).
- Decorators: Peeyush has a [Babylon PR](https://github.com/babel/babylon/pull/587) ~~ready~~ merged! Follow up [PR](https://github.com/babel/babylon/pull/590).
- Optional Chaining: Justin's [PR](https://github.com/babel/babel/pull/5813) needs review.

### Priority Topics

Sounds like we need reviewers? With Summer of Code and our efforts in contributions, we have a lot more PRs which is great, but it doesn't encourage enough reviewers. There's a huge emphasis on contributing code in OSS rather than maintenance.
