## Babel Weekly Notes - 2018-01-19

## Participant

- Logan Smyth
- Nicolò Ribaudo
- Sven Sauleau

## Turn on Slack inviter again

## Babelrc lookup

https://github.com/babel/babel/issues/6766

- Logan: not using the babelrc in the node_modules by default, opt-in
- Opt-in with the overide key ?
- Sven: idea about using babel-preset-env in the root configuration and transpile deps against the target

## Plugin order

- Still priority? probably not a blocker for the 7 release

## Async plugins/visitors

- Not for now
- Would expose if Babel supports async for plugins or visitor
- `babel-register` might be a blocker because it will need to support the async flow
- traversal will need to be asynchronous

## async-to-promise

https://github.com/babel/babel/pull/7076

- Would be great to have a Babel plugin
- What appends in control structures? Big output
- Can it work with TDZ?

## Pipeline operator

- Need to transform await syntax


## Decorator 2 

https://github.com/babel/babel/pull/6107

- Should we keep the two syntaxes?
- Could people opt-in into the syntax/old syntax?
- We can publish a single transformation (with `legacy: true`)
- Plugin ordering issue, we could handle oursevles

## gsoc/rgsoc

- We had probably too many people last year
- We should assign our members to specific areas and mentor studient
- Maybe 2 students and 4 of our members to actually mentors
