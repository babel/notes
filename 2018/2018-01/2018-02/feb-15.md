## Babel Weekly Notes - 2018-02-15

## Participant

- Logan Smyth
- Nicolò Ribaudo
- Sven Sauleau
- Henry Zhu
- Brian Ng

## gsoc/rgsoc

- We didn’t get into the Gsoc
- We are accepted at Rails summer of code (https://teams.railsgirlssummerofcode.org/projects/224-babel)

## Slack inviter

- Turn it back on
- We can change the hosting (Netifly?)

## Add community plugin

https://github.com/babel/website/pull/1518

- We can land it
- Also merge it into the old website (old branch)

## New REPL

https://github.com/babel/notes/issues/57

- Code that we don’t maintain
- New page until we have all existing features

## Babel 7

- Website with v7 documentation is almost done
- Add documentation versioning (for v6 and v7)
- Centralize our READMEs on the website and just have stub readmes to point to the website for GitHub and npm (or minimal doc).
- What should we do with the change of proposal plugin to a transformation plugin?
- What should we do with changelogs? The doc should track more changes in Babel.
  - Version selector (http://new.babeljs.io/versions.html)
  - Tag or add a checkbox for each PR about updating the doc (could be a beginner-friendly)
- Clean up some pages on the new website (https://github.com/babel/website/issues/1577)
- Some features that we need to explain more (use cases), like for overrides and .babelrc lookup.
- Add babel.config.js?
  - We should disallow multiple configs (.babelrc and babel.config.js)

## Babel 7 upgrade

- For each breaking change we could impact the upgrade tool.
- Blog post: http://new.babeljs.io/docs/en/next/v7-migration.html (should we split for plugin author and users?).
