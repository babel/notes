# 11/19 Meeting

## Attending

- Sven
- Nicolò
- James DiGioia
- Daniel
- Logan

## Agenda

### Debugging story

- Would be cool to have a flag to show what config is loaded 
- Better error are important
- Especially in the monorepo case
- We have names for plugin now
- We have time travel in the REPL which could help but are people aware of that?
- Could be a good fit for studients?
- Maybe clarify all that in a document

### Smart Pipeline

- https://github.com/babel/babel/pull/8289
- We've assigned a couple of people
- We have a blog post and we have some documentation on the plugin

## Minor output optimizations

- Doesn't seem practical to implement it in babel/minify
- Do we want to maintain the readability of the output?
- What are the real benefits? does it solve current issues we have?
- Noone is strongly in favor of merging it

### Merge class features plugins

- We had concern about it; we haven't really have a precendence
- Not user fancy, but maintability concern
- Only merge @babel/plugin-class-features, decide what to do with the @babel/plugin-proposal-decorators and @babel/plugin-proposal-class-properties plugins later before the next release 

### Add support for initializers

https://github.com/babel/babel/pull/9008

- Let's wait for the meeting

### JSX fix JSXAttributeValue

https://github.com/babel/babel/pull/8787

- See status https://github.com/babel/babel/pull/8787#issuecomment-439726230
- We could emit a warning until Babel 8, and then BC
- Maybe a more general question about BC
- This is pretty much Babel's core since it's the parser
