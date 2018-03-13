## Babel Weekly Notes - 2018-03-13

## Participants

- Logan
- Sven
- Brian
- Diogo

## sourceType for parsing modules

https://github.com/babel/babel/issues/6242

- Peoples will transpile more and more node_modules
- Can we detect based on the file? Is that future proof?
- The spec doesn't define which source type to apply
- Avoid shifting from the Node community and behavior
- Babel-loader could have its own default for Webpack
    - defaults on amgigious?
- Webpack does unambiguous for parsing
- Brian and Sven are ok for the PR
- What happends with parsing TypeScript? What source type?
    - We can change for the .ts extension
    - It has it own source types
    - babel parser is written with isolated module (`--isolatedModules` on tsc) in mind
    - you could have the syntax plugin turned on but now the transformation
    - If the typescript transform is turned on but the source type is something else we can skip
- In general we need a better file extension system to determine that kind of stuff
- Babel-register has some issue with compiling node_modules but it's ok when you target explicitly
    - it can end up circularly compiling things; such as compiling core-js, or a plugin/preset that was given as a string

## Lazy dependecies

- We can make Babel lazy soon
- Babel-cli requires babel-core which take a few ms
- When you depend on one Babel's exported function you don't want to wait for all dependecies to load

## Babel-register

- Depending on people's local setup they want to explicity compile node_modules
- It runs when the user calls require so it needs to be fully synchronous
    - We can't use dynamic import() (or a transpiled version)
    - Lazy requires have to be sync requires
- Maybe with `node --require babel-register`?
- Custom ESM loader? https://nodejs.org/dist/latest-v9.x/docs/api/esm.html#esm_loader_hooks
    - The resolve hook only allows you to change what URL is resolved for the internal loader, but not the contents. `data: URLs` are not supported, or at least weren't when I investigated back during early 9.x releases.
    - This meant that the only way to preprocess files would be to write the result to some temp file and return its path from the resolve hook.    
- We should encourage people to not rely on babel-register 

## TypeScript

- New field in the config, an object with extensions name with true and false, for example typescript could say `ts: true` and `tsx: true`, which pushes into the extension whitelist.
- We can ignore the `.d.ts` files since it's just type definition
