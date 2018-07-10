# 07/09 Notes

> No meeting but tracking down progress.

## RC

> Mostly ready, need to review/merge.

- [ ] Logan has a PR to separate out helpers/core-js/runtime: https://github.com/babel/babel/pull/8266 that is ready for review.
- [x] Blocker: [Ignore/Only support on Windows](https://github.com/babel/babel/issues/8184), I made a temporary workaround to revert the upgrade https://github.com/babel/babel/pull/8281.
  - [ ] Final change: Removing pattern matching in `ignore/only/test/include/exclude`, new recommendation is to use a regex in a `.js` config.
- Henry: Remove Stage and yearly presets https://github.com/babel/babel/issues/7770
    1. [x] Publish new releases of yearly and stage presets (no changes), and ensure that they have deprecation warnings on npm.
    2. [ ] Remove code from presets and have them throw helpful errors telling people what packages they _would_ have been using, and publish and move yearly/stage presets directly into babel-standalone. Merged https://github.com/babel/babel/pull/8274, Can review https://github.com/babel/babel/pull/8293
    3. Non-essential: change bundling standalone to only on "production" build. 

## Proposal Updates

- [ ] Pipeline parser flag: https://github.com/babel/babel/pull/8291
- [ ] Pipeline smart pipeline proposal: https://github.com/babel/babel/pull/8289
- [ ] Decorators is mostly ready and has been reviewed by Daniel (TC39 Champion) https://github.com/babel/babel/pull/7976
- [ ] Private Static Fields: https://github.com/babel/babel/pull/8205
