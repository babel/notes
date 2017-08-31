
## August 1st ([discuss](https://github.com/babel/notes/pull/3))

#### In Slack (at the time)

* [Henry](https://twitter.com/left_pad)
* [Logan](https://twitter.com/loganfsmyth)

### Potential API changes for traversal

Editor: This a combination of notes of Slack and a general elaboration on the current experimentation Logan is doing.

Building on previous conversations in:

* https://phabricator.babeljs.io/T7154#75322
* https://github.com/babel/babel/pull/3281
* https://phabricator.babeljs.io/T6730

and continuing somewhat from [yesterday's discussion on versioning](https://github.com/babel/notes/blob/master/2016-07/july-31.md#future-of-babels-release-process-and-its-ecosystem), Babel's current approach to plugins, e.g.

```
export default function(babel) {
  return {
    visitor: {
      Identifier(path, state) { },
    },
  };
}
```

with Babel's simplified core algorithm being:

```
const visitors = plugins.map(plugin => plugin.visitor);
const mergedVisitors = merge(visitors);
traverse(ast, mergedVisitors);
```

This has a few primary issues that make things difficult for us:

1. The `visitor` approach to AST mutation is baked directly into the core of our plugin system. This prevents us from iterating on the core transformation system because it is tied to the version of `babel-core`, it requires plugins to run overtop of eachother, because plugins all run in the same traversal pass (usually anyway).
2. We pass in the `babel` param, which our internal plugins at least, rely on for access to things like `babel-types` and `babel-traverse`. This also prevents us from modifying those easily, unless we want to lock `babel-core` to an old version of `babel-traverse`, with plugins using some new major version.
3. Plugin ordering is user-defined based on their Babel configuration, which most don't realize, and makes it hard to reason about what could be affected by any given change to a plugin.
4. Because transforms run overtop of eachother, it is hard to provide useful debug feedback, since anything could be mutating the AST at any time.


#### Proposed resolution

To address both of these, Logan's proposed approach would be to trim down Babel's core plugin architecture to expose the AST root directly, allowing plugins to mutate the AST however they may like, with a full lock on the data structure, with plugins running based on their priority ordering. The primary issue that this does not address is that transformation is not a linear process. Our existing infrastructure causes sections of the tree to be "requeued" so that all plugins have the opportunity to react to changes made by all plugins, whatever the ordering.

With that in mind, a slightly more complex approach would be required, along the lines of:

```
import traverse from "babel-traverse";

export default function(ast, options) {
  traverse(ast, {
      Identifier(path, state) { },
    },
  });

  // return 'true' to indicate that a change was made, or 'false' otherwise
  return true;
}
```

which allows plugins to be run

```
for (let i = 0; i < plugins; i++) {
  if (plugins[i](ast)) i = -1;
}
```

This would allow each plugin to have full control over the AST, while allowing plugins with higher priority to re-execute whenever something is changed in the AST.

#### Concerns

This API in its simplest for would require many more traversals over the AST, which will be a performance issue. This is likely to mean that the traversal API itself should be trimmed down to make drammatically it faster.

Potentially we'd want to remove or implement elsewhere:

1. Automatic re-queuing of replaces nodes. Since you have a full lock on the AST, plugins can always explicitly re-traverse if they need to modify newly-added nodes.
2. The "smarts" in the current API around what nodes are allowed to go where.
3. Scope tracking (in it's current implementation)


#### Possible futures

While `babel-traverse` is actually a quite simple core implementation with the above items stripped out, the next question from this is, does generic traversal fit the overall goal of transformation best? The vast majority of traversals performed in our plugins perform one of a few actions:

1. Find items to transform.
2. Calculate scoping information.
3. Answer transform-specific questions about a subtree of the AST (does this container `super()`).

With these primary goals, they all kind of boil down to the question

> Given an AST node, what is the result of X by processing its children?

which begs the question, how can we make this type of operation as fast as possible.

With a recursive, memoized process, you could imagine each subtree of the AST memoising its results in a WeakMap, so that answering questions about the AST would only require a lookup in the general case. The question we face on this would then be how to handle cache invalidation. Two approaches come to mind:

1. Treat the AST as an immutable tree, with actions discarding mutated nodes and replacing them.
2. Expose an AST manipulation API to tracking which nodes were mutated so they can be explicitly invalidated.

Both have their upsides and downsides, and without active implementations, it's not obvious that one would have dramatically better performance when used. An API designed to wrap the AST to track changed could conceivably be written to wrap either approach, either by cloning the node and all parent nodes whenever a node was mutated, or by invalidating the cache for the node and all parents.

* Pro immutable:
  * It's likely that freezing the whole AST would make it harder for the average user to throw together a transform themselves. That could be avoided by not actually freezing it, and performing a diff unless the plugin has explicitly opted in to immutability. A good wrapper mutation API could fix this concern though.
  * Avoids the concept of one central channel for invalidation, because object identity provides this.

* Pro invalidation
  * Potentially less GC overhead since only cached data is recreated, not AST nodes themselves. This could maybe be avoided if reallocation was delayed until absolutely necessary.
  * Possibly easier for users to understand.

Logan is currently thinking of an API along the lines of:

```
import root from "babel-query"

export default function(ast, options){
  return root(ast, (program) => {
    // process each class declaration in it's own context to avoid having to adjust other stuff.
    program.queryContext("ClassDeclaration").forEach(declar => {
      const props = declar.child().children();

      props.forEach(prop => {
        if (prop.child("key").get("name") === "newKey") return;

        prop.setChild("key", t.identifier("newKey"));
      });
    });
  });
}
```

which again, could be backed by either approach above.

Who knows how well this will all work out, but it's where we're at at the moment.
