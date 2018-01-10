# Babel Team Meeting - 2017-07-12
 
## Attendees

+ Sarup
+ Peeyush
+ Henry
+ Boopathi
+ Kara
+ Emma
+ Vignesh

## Discussion

- Sarup: https://github.com/babel/babel/pull/5911
- Boopathi: still encountering issues with scoping in Babili, will look into again.
- Boopathi made: https://babel-time-travel.boopathi.in/ (this is a really cool idea that outputs the state of the AST during traversal of visitors)
- Emma and Kara: Working on codemods
  - Going to focus on writing more ES5 to ES6+ codemods (like Lebab)
  - Henry: Would be good to have a codemod which does the opposite of a proposal - so when a syntax proposal gets removed (always a possibility), you can apply the codemod instead.
- Peeyush: decorators proposal - working on the transform now.
- Karl: private fields, 2 implementations (one by Justin), need to evaluate which one is better
- New packages from community: https://github.com/kentcdodds/babel-macros, https://github.com/kentcdodds/babel-plugin-preval
- Henry: idea to repurpose `babel` package: opinionated babel tool (no config, 1 install)?
