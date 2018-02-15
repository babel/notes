## Babel Weekly Notes - 2018-02-15

## Participants

- Logan Smyth
- Nicolò Ribaudo
- Sven Sauleau
- Henry Zhu
- Brian Ng
- Mateusz

Thanks to Sven for setting this up; we havent been doing meetings that often!

## GSoC/RGSoC

- We didn’t get into the [Google Summer of Code](https://twitter.com/gsoc/status/963096136184512512), but it's all good!
  - If you wanted to participate with us this year, I would suggest you apply to [webpack](https://twitter.com/TheLarkInn/status/963115975640887296)!
- We've been accepted into Rails Girls Summer of Code though 🙌 https://teams.railsgirlssummerofcode.org/projects/224-babel!
  - We can always just wait for applications (it's due on 2/28 for students), but I'll set some time to meetup with teams that would like to contact us for more information.
  - The decision for the team/projects will be April 17th.
- Henry: I'll try reach out to some univerities/bootcamps in the upcoming months about partnering for a separate kind of mentorship (it doesn't have to be in the summer, and I don't mean it be an internship/paid given the logistical issues unless it's a class/extra credit/curriculum).

## Slack Inviter

- Current way: the issue is huge with comments, sucks as a user experience, people complain about e-mails, etc. It definetely sucks.
- So let's turn it back on! If the spammers come back we can revert.
- We can change the hosting (Netlify?).

## REPL: Add Community Plugins (import any plugins from npm)

PR: https://github.com/babel/website/pull/1518

- We can land it! http://new.babeljs.io/repl
- Also merge it into the old website (old branch), https://github.com/babel/website/pull/1578

Example: https://twitter.com/left_pad/status/955928494432808960

## New REPL

Discussion: https://github.com/babel/notes/issues/57

- It's code that we may not want to necessarily maintain. I think we are all on board with using at least some part of CodeSandbox.
  - Talked to Brian Vaughn who is cool with rewriting what we need from it, and talked to Ives about partnering to make the REPL better.
  - We will move forward with doing so: just need to determine exactly what we should be switching out. At the moment it makes sense to substitute most of it with codesandbox except our specific UI which we want to keep to make the REPL easy to use.
- We should just create a new page until we have feature parity (/codesandbox, /repl2)? That way we can develop in parallel and just swap it out when it is ready (and let people test it out)
- Aside: we can collect stats about plugin usage and add analytics to the REPL itself!
  - Henry: my idea here is that given we can't add analytics to the tool itself, the REPL can be a good proxy of usage.
  - This can also help shape proposals - which ones are people using? If we implement multiple implementations of a proposal we can learn from usage. Ref https://twitter.com/left_pad/status/960874812385226752 + @littledan

## Babel 7

- [Website](https://github.com/babel/website) with v7 documentation is almost done: other tasks at https://github.com/babel/website/issues/1568
  - Redone in using https://docusaurus.io/
  - Setup 3 urls: https://babeljs.io, https://old.babeljs.io, https://new.babeljs.io
  - Current the `old-site` branch is targeting https://babeljs.io and https://old.babeljs.io, and `master` is targeting https://new.babeljs.io
  - When we are ready for the switch, we will move `master` to also target https://new.babeljs.io
  - Added documentation versioning (for v6 and v7): http://new.babeljs.io/versions.html (will change the url `/next`)
- We should centralize our READMEs on the website and just have stub readmes to point to the website for GitHub and npm (or minimal doc).
  - This is always going to be an issue, we had a lot of hacks (https://github.com/babel/website/blob/master/scripts/download-readmes.js) to download readmes and sync them to the website. We will only lose having users have to click on the link to the real source of truth
- What should we do with the change of proposal plugin to a transformation plugin?
  - Currently we are just going to rename the package. Ex: `@babel/plugin-proposal-class-properties` to `@babel/plugin-transform-class-properties`. This is important to signal that the proposal is actually a proposal and not JavaScript.
- What should we do with PRs/changelogs?
  - We need to make sure everyone is better about documenting changes, whether or not it will go into the readme or somewhere else.
  - It's easy to just land new features/changes but if no one knows how to use them, does it matter that it works that way?
  - The new site as has a version selector (http://new.babeljs.io/versions.html)
  - Tag or add a checkbox for each PR about updating the doc (could be a `good first issue`). When we move all docs to the website, maybe just create an issue to track what still needs to be updated, and we can soft block a release if there isn't docs?
- Clean up some pages on the new website (https://github.com/babel/website/issues/1577)
- Some features that we need to explain more (use cases), like for `overrides` and `.babelrc` lookup.
  - It's not enough to just explain it in words (that's hard enough), but also add the common use cases.
- Different config formats: `babel.config.js`?
  - Having a lot of formats shouldn't be that confusing.
  - We already disallow multiple configs (`.babelrc` and `.babelrc.js`) so users only opt into one of them.
  - It does feel like `babel.config.js` would replace the regular `.babelrc` files though.
- Transpiling `node_modules` with `@babel/register`
  - Merging configs is currently confusing
  - Henry: have an experimentatal `@babel/register2`?
    - Greater point: we should be free to test out different implementations as separate packages/options and if it has traction merge them into the main package. Don't be scared to change it especially under a new namespace.
- Should land the decorators transformation
  - Add the `legacy` flag that runs the old transformation in `@babel/plugin-proposal-decorators` so when the Stage 2 implementation is complete it will work without breaking changes.
- Plugin ordering
  - Having presets can fix plugin ordering for users
  - This can land in a minor version
- What are we doing with the stage presets?
  - We want to remove them, it's a difficult decision though.
  - It's better to use proposal-* plugin, maybe just better documentation around that.

## Babel 7 upgrade

- For each breaking change, we should think about how that could affect the upgrade tool.
  - We should make sure the guide itself is correct before attempting to work on the upgrade tool (more work).
  - Do the low hanging fruit (package.json, .babelrc) changes first.
- Blog post: http://new.babeljs.io/docs/en/next/v7-migration.html (should we split for plugin author and users?).
  - Logan: we need a guide about best practices for integration (meteor, gatsby, jest/ava, etc).

For further comments check: https://github.com/babel/notes/pull/56
