# 04/06 Meeting

## Participants

- Nicolò Ribaudo
- Brian Ng
- Henry Zhu
- Sven Sauleau

## Notes

### Moving Docs to Website Repo

- [x] Sven started initial PRs to merge: https://github.com/babel/website/pull/1677, https://github.com/babel/babel/pull/8108, https://github.com/babel/website/pull/1678
- [x] Review a usage guide PR: https://github.com/babel/website/pull/1588
- [ ] `babel-types` docs are generated automatically so need to figure how to document types.
- [ ] New config guide https://github.com/babel/website/pull/1679

- READMEs in individual packages will just contain install instructions and a link to the website. Sven created a script to handle this.
  - Action item: Add a link to the corresponding package/area label (https://github.com/babel/babel/pull/8112)
  - Idea: babel-bot could auto label based on folder changed (need hueristic)?

- Consider adding individual package CHANGELOGs and aggregate/summarize them up on main Babel's CHANGELOG?
  - Action item: n/a

- Don't block landing PRs with trying to figure out what to do with `babel-types` docs. We may want to re-think what a better solution to it anyway (instead of one giant long markdown file).
  - Action item: Sven will create a new issue (https://github.com/babel/website/issues/1680)

- How do we want to handle `next`/`master` on the website? Maybe one option is to make https://babeljs.io only have tagged versioned docs and https://new.babeljs.io always represent `next`?
  - Action item: discuss further/later

## Future

### Improve documentation around polyfill/environment requirements (Reflect, etc.)
- Babel support for environments
  - https://github.com/babel/babel/blob/master/doc/design/compiler-environment-support.md, merge with caveats page?
  - preset-env maybe include helpers (Reflect) in debug output
- Need to explain common plugin options: loose, useBuiltIns

- Have consistent "caveat" section in package READMEs that roll-up into a Babel-wide caveats/requirements page that links out to each individual package.

### How to keep the docs repo in sync

Babel-bot improvement: Open an issue on the website repo when a PR is tagged with `doc needed`.

### What can you do with a Babel plugin?

- Good for workshops but also to document possibilities and inspiration

## RC

- Finish out docs
- Separate out helpers/core-js/runtime
- Possibly merge class proposal transforms (doesn't have to be in RC)
