# Babel Team Meeting - 2017-06-14
 
## Attendees
- Brian Ng
- Daniel Tschinder
- Henry Zhu
- Kara de la Marck
- Karl Cheng
- Nathan Hammond
- Nick Cantelmi
- Peeyush
- Sarup Banskota
- Sergey Rubanov
 
## Actions
 
- [X] (Nathan) Publish meeting notes.
- [ ] (Henry) Document the 0.X plugin stage policy.
 
## Discussion

### Plugin Ordering Updates

- Moving to `before`/`after`.
- James Kyle wrote a blog post about Plugin Ordering: http://thejameskyle.com/babel-plugin-ordering.html
- Open issue for further discussion: https://github.com/babel/babel/issues/5854
- Explore tradeoffs between explicit package name vs. "capabilities". (hardcoded or semantic string)
- Open question: how does this work with the host environment?

### Class Fields Updates

> Karl/Diego

- Open questions on the spec.
  - How are things are going to interact with decorators?
  - Keep the `#x` shorthand vs `this.#x` ? If we add it and people actually use it then it becomes a reason for TC39 to keep it.
- Need a way to search GitHub to determine if people are using particular syntax. (Is a project in and of itself. Possibly using BigQuery + AST search.)
- Haven't implemented comma separated fields and some other restrictions.

### Decorators Updates

> Peey/Diego

- Build the thing which is currently specified.
- Plan for no interop with private/public fields as that is unspecified.
- Keep current syntax plugin and then also create decorators-stage-2 syntax plugin.
- JavaScript logic for it already exists, should be straightforward.
  - Need to take care of invalid cases.
  - Coming out of this process we're aiming to have a guide for how Babylon's code is structured.
  - Allow both old and new syntax and transform plugins to exist, specifically the transformer so people can start experimenting with the new syntax.

### SemVer

- Parsers: every change is kind of a "breaking change".
- We already have a decorators plugin and if the spec changes what the syntax _is_ we are breaking things.
- Aim to allow for backwards-compatible syntax plugins. This will be more work for us, but is probably the right tradeoff. This will hopefully allow us to bump only minor version.
- Only update the transform to be a major version as opposed to back-compat minor versions for the syntaxes.
- Will there be confusion about having two separate plugins if we decide to retain an older syntax?
  - Yes, but plan to address via documentation.
  - Deprecate the old version with messaging.
- Rejected a proposal for using 0.1 to map to stage 1, 0.2 to map to stage 2 on account that the TC39 process is not linear.
- Should we use scoped packages? Postponed from a few months ago.

#### Conclusion

- Minor updates for syntax plugins (if possible).
- Major updates for transform plugins (as they make back-compat breaking changes).
- Start at 0.X for stages 0-3. (Meaning that the minor is acting as major, and 0 indicates instability.)
  - Continually increment 0.X minor every time there is a breaking change.
  - Move to 1.X upon reaching Stage 4.
  - We'll need to use Lerna independent mode to publish (supported already but haven't used before in Babel).
  - For existing plugins we'll continue to bump major versions.

### Optional Chaining

> Justin

PR is open, ready for review but there are some open spec questions: https://github.com/babel/babel/pull/5813

### Priority Topics

- Last week's topics as people had limited bandwidth.
- Typescript Support in Babylon for review (by [Andy on the TypeScript team](https://github.com/andy-ms)): https://github.com/babel/babylon/pull/523, https://github.com/babel/babel/pull/5856
  - HUGE PR, needs lots of work to review.
  - Should figure out how to review just the parser.
  - Ideally continually land changes in our pre-releases for everyone to test.
