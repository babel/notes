# 4/16 Meeting

## Subjects

- Babel 7 rc?
  - Config PR (https://github.com/babel/babel/pull/7358)
  - Decorators PR (https://github.com/babel/babel/pull/7719)
  - Make sure upgrade doc is up to par
- Release date (lets do 4/30 or 5/1?)
  - Start on blog post
    - Babel 7 website?
      - Move all docs to the website vs. the repo
      - Switch the domains
      - Rewrite most of it (can do this after)
- Anything Else?
  - Funding for specific contributors?
  - Henry: 
    - Talk goals
    - Idea of meetups/podcast/livestream
    - Want to track contributors via github api

## Participants

- Brian
- Daniel Tschinder
- Henry
- Logan
- Nicolò Ribaudo
- Sven Sauleau

## Notes

### Config PR

- `babel.config.js`: does it add more complexity/explain more?
- What are the alternatives though?
- Only other option atm: use the same file name but add a flag.
- People shoudln't have to rename their config file
- have one config that applies to everything in the repo, handles `node_modules`
    - Only applies to the root, not node_modules
- Overrides the config in node_modules if defined
- Babel-upgrade tool!
- And what about tools like CRA and parcel that do config lookup anyway? Is this not that big of an issue?
- Different users: tools/libs vs. apps
- With good communication, great docs, upgrade tool, etc what else do we need to do?

> Conclusion: merge this PR, but provide in-depth explanations + example use cases

## Decorators PR

https://github.com/babel/babel/pull/7734

- Doesn't block the RC
- The proposant might change in the future

> Conclusion: continue the work + review/merge https://github.com/babel/babel/pull/7734
> `@dec export` vs `export @dec`: let's keep syntax plugins separate
> Blocker: Question about class properties + decorators ordering (should it be 1 plugin)

## Release RC

> Land these asap

- Config: https://github.com/babel/babel/pull/7358
- Decorator: https://github.com/babel/babel/pull/7734, https://github.com/babel/babel/pull/7719
> Question about sourceType (has PR)

> File extensions w/ .ts? (?)
- Node 4 unsupported (End-of-life 2018-04-30)
> Plan: RC next Monday but we can discuss again
> Weekly meetings before release
> Final: get feedback and wait 2 weeks if ready

- Core-js 3 after the RC?


## Final Release

- New Docs
- READMEs in Babel/babel are just links to the website


## Docs

- Codesandbox still wip

## Funding for specific contributors

- Maybe we should have a general rule?
- That's a good argument for other companies to pay us
