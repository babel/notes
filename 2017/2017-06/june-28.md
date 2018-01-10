# Babel Team Meeting - 2017-06-14
 
## Attendees
- Henry Zhu
- Nathan Hammond
- Sarup Banskota
- Tobias Bieniek
 
- Omar
- Lennex Zinyando
- Nainesh

## Actions
- [ ] Guide people to help on babel/proposals
- [ ] 0.X Plugin policy documentation

## Discussion

### Plugin Ordering

- Visitor lockout is now working.
- Have a codemod which is able to add names to all plugins. 
- Things still break when running because of some weird issue in the current branch. https://github.com/babel/babel/pull/5842
- Wrote a blog post! https://sarupbanskota.com/programming/babel/2017/06/23/writing-a-babel-codemod-plugin.html
- Make it possible to run against all of the Internet.

### High Level Issues

- Make https://github.com/babel/proposals real!
- How are we going to deal with babel-core and versioning (it's confusing). Do we need to make it a peerDep   - At least for integrations like babel-loader which does it already but it's not done for gulp, grunt, babelify, etc.
  - We removed one of the API functions in babel-traverse.
  - Make the API smaller and this won't happen as frequently.
  - Plugin compatibility metadata?
  - Add more information to the package.json key we squat on.
  - Get a proposal pulled together.
- [Better error message for unexpected token that is a plugin.](https://github.com/babel/babylon/pull/178)
  - Writes own plugin, doesn't have the re-extend of the parser plugin.
  - Alternatively, plugin runs before parser plugin.
  - Webpack is approximately an "environment": https://github.com/babel/babel-loader/pull/485
