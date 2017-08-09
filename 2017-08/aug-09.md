Babel Team Meeting - 2017-08-09
 
## Attendees

- Henry
- Peeyush
- Karl
- Brian
- Kara
- Emma

> TODO

- Henry: last 2 issues in the milestone by justin: babel-types refactor, object-rest-spread refactor.
- Peeyush: have a branch for decorators, https://github.com/peey/babel/blob/decorators-2-transform-wip/packages/babel-plugin-transform-decorators-2/src/index.js
- Karl: Wanted to see how private methods should work. It is a separate proposal though so can make a new package for that. We should schedule a meeting with littledan to talk about private properties and where were at with that. (Should probably do this for decorators too actually)
- Kara: question about codmods (sven brought up a standalone executable). We can just use npx + babel-codemod: `npx babel-codemod --plugin ./plugin.js src/`.
- Brian: need to release all the other packages: preset-env 2.0, other integrations. We already released compatible versions for webpack, gulp, rollup, grunt.
- Brian: make sure the documentation is ready for 7.0
- Henry: learned that more well defined issues -> quick contributions!
- Henry: will finish the Summer of Code post today and make a PR, then post Peeyush's after. Karl will make a PR for his own post too!
