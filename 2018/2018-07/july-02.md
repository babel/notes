# 07/02 Meeting

## Participants

- Henry
- Logan
- Nicolò
- Brian

## RC

- [ ] Logan: Separate out helpers/core-js/runtime: https://github.com/babel/babel/issues/8155
  - `babel-runtime` (default) and `babel-runtime-corejs2` both have helpers, but only `core-js` one has `core-js` included. Also add a `babel-runtime-corejs3`
  - Logan: almost done, need to update test files.
- [ ] Blocker: Ignore/Only support on Windows https://github.com/babel/babel/issues/8184
  - Remove pattern matching in `ignore/only/test/include/exclude`, new recommendation is to use a regex in a `.js` config.
  - Short term: revert the upgrade PR 
- [ ] Henry: Remove Stage and yearly presets https://github.com/babel/babel/issues/7770
  - Update stage presets with a warning/deprecation message "here are the plugins you will want to include" and possibly mention (and add) babel-upgrade support?
    - [x] Publish new releases of yearly and stage presets (no changes), and ensure that they have deprecation warnings on npm. [beta.52](https://github.com/babel/babel/releases/tag/v7.0.0-beta.52)
    - [ ] Remove code from presets and have them throw helpful errors telling people what packages they _would_ have been using, and publish (maybe as RC release).
    - [ ] Move yearly/stage presets directly into `babel-standalone` or update website to allow selecting a "stage", which would enable plugins.

## Misc

- [ ] Team: do a run through of existing PRs if anything was missed
  - TODO: Schedule a time for the team to run through everything, shoot for next Monday since holidays.
- [ ] Change bundling standalone to only on "production" build (saves on local/CI build time since it only needs to happen per release).
- [ ] Henry: Outlined the release post
- RGSoC kickoff/starting today!
