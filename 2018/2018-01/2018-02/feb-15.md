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

- We didn’t get into the Google Summer of Code, but it's all good!
- We've been accepted into Rails Girls Summer of Code though 🙌 https://teams.railsgirlssummerofcode.org/projects/224-babel!
  - We can wait for applications (it's due on 2/28 for students), but I'll set some time to meetup with teams that would like to contact us for more information.
  - The decision for the team/projects will be April 17th.
- Henry: I'll try reach out to some univerities/bootcamps in the upcoming months about partnering for a different kind of mentorship/program (doesn't have to be in the summer, and I don't mean it be an internship)

## Slack Inviter

- Turn it back on! (Talk to Daniel about how to do that again, and if the problem occurs again to easily switch back).
- We can change the hosting (Netlify?)

## REPL: Add Community Plugins (import any plugins from npm)

https://github.com/babel/website/pull/1518

- We can land it! http://new.babeljs.io/repl
- Also merge it into the old website (old branch), https://github.com/babel/website/pull/1578

## New REPL

https://github.com/babel/notes/issues/57

- It's code that we may not want to necessarily maintain. I think we are all on board with using at least some part of CodeSandbox.
  - Talked to Brian Vaughn who is cool with rewriting what we need from it, and talked to Ives about partnering to make the REPL better.
  - We will move forward with doing so: just need to determine exactly what we should be switching out. At the moment it makes sense to substitute most of it with codesandbox except our specific UI which we want to keep to make the REPL easy to use.
- We should just create a new page until we have feature parity (/codesandbox, /repl2)? That way we can develop in parallel and just swap it out when it is ready (and let people test it out)
- We can collect stats about plugin usages, add analytics to the REPL itself!
  - Henry: my idea here is that given we can't add analytics to the tool itself, the REPL can be a good proxy of usage.

## Babel 7

- [Website](https://github.com/babel/website) with v7 documentation is almost done: other tasks at https://github.com/babel/website/issues/1568
  - Redone in docusaurus.io
  - Setup 3 urls: babeljs.io, old.babeljs.io, new.babeljs.io
  - Current the `old-site` branch is targeting babeljs.io and old.babeljs.io, and `master` is targeting new.babeljs.io
  - When we are ready for the switch, we will move `master` to also target new.babeljs.io
  - Added documentation versioning (for v6 and v7): http://new.babeljs.io/versions.html (will change the url `/next`)
- We should centralize our READMEs on the website and just have stub readmes to point to the website for GitHub and npm (or minimal doc).
  - This is always going to be an issue, we had a lot of hacks (https://github.com/babel/website/blob/master/scripts/download-readmes.js) to download readmes and sync them to the website. We will only lose having users have to click on the link to the real source of truth
- What should we do with the change of proposal plugin to a transformation plugin?
- What should we do with changelogs? The doc should track more changes in Babel.
  - Version selector (http://new.babeljs.io/versions.html)
  - Tag or add a checkbox for each PR about updating the doc (could be a beginner-friendly)
- Clean up some pages on the new website (https://github.com/babel/website/issues/1577)
- Some features that we need to explain more (use cases), like for overrides and .babelrc lookup.
- Add babel.config.js?
  - We should disallow multiple configs (.babelrc and babel.config.js)
- Transpiling node_modules with babel-registrer
  - Merging configs is currently confusing
  - Henry: have an experimentation babel-registry2?
- Should land decorators transformation
  - Add the legacy flag that runs the old transformation
- Plugin ordering
  - Having presets fix plugin ordering for users
- What are we doing with the stage presets?
  - It's better to use proposal-* plugin

## Babel 7 upgrade

- For each breaking change we could impact the upgrade tool.
- Blog post: http://new.babeljs.io/docs/en/next/v7-migration.html (should we split for plugin author and users?).
