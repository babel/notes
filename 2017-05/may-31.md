Babel Team Meeting - 2017-05-31
 
## Attendees
- Andrew Levine
- Boopathi Rajaa
- Brian Ng
- Daniel Tschinder
- Diogo Franco
- Henry Zhu
- Kara de la Marck
- Karl Cheng
- Nathan Hammond
- Peeyush Kushwaha
- Sven Sauleau
- Vignesh Shanmugam
 
## Actions
 
- [X] (Nathan) Publish meeting notes.
- [ ] (Henry) Specify the complete list of outstanding tasks on the plugin ordering PR.
 
## Discussion
 
### Weekly Meetings! (Wednesday)
 
- Introductions!
- We have them now. Coming up with a time was hard. I'm sorry if we failed to accommodate your time zone.
- Most people seem comfortable with [our selected time](https://www.timeanddate.com/worldclock/meetingdetails.html?year=2017&month=5&day=31&hour=13&min=0&sec=0&p1=283&p2=136&p3=54&p4=240&p5=179&p6=37&p7=104&p8=248), shown below.

|Location | Local Time | Time Zone | UTC Offset|
|---------|------------|-----------|-----------|
|San Jose (USA - California) | 6:00:00 am | PDT | UTC-7 hours|
|Houston (USA - Texas) | 8:00:00 am | CDT | UTC-5 hours| 
|New York (USA - New York) | 9:00:00 am | EDT | UTC-4 hours| 
|London (United Kingdom - England) | 2:00:00 pm | BST | UTC+1 hour|
|France/Germany |  3:00:00 pm | CEST | UTC+2 hours|
|Kolkata (India - West Bengal) | 6:30:00 pm | IST | UTC+5:30 hours|
|Tokyo (Japan) | 10:00:00 pm | JST | UTC+9 hours|
|Sydney (Australia - New South Wales) | 11:00:00 pm | AEST | UTC+10 hours|
|Corresponding UTC (GMT) |  13:00:00|
 
### Summer of Code!
 
- We have four new people on the team!
  - [GSoC](https://twitter.com/gsoc): Peeyush Kushwaha, :octocat: [@peey](https://github.com/peey), :bird: [@peeyFTW](https://twitter.com/peeyFTW)
  - [GSoC](https://twitter.com/gsoc): Karl Cheng, :octocat: [@Qantas94Heavy](https://github.com/Qantas94Heavy), :bird: [@qantas94heavy](https://twitter.com/qantas94heavy)
  - [RGSoC](https://twitter.com/RailsGirlsSoC): Kara de la Marck, :octocat: [@MarckK](https://github.com/MarckK), :bird: [@KaraMarck](https://twitter.com/KaraMarck)
  - [RGSoC](https://twitter.com/RailsGirlsSoC): Emma Deacon, :octocat: [@EmmaDeacon](https://github.com/EmmaDeacon), :bird: [@EmmaMDeacon](https://twitter.com/EmmaMDeacon)
- Y'all are the only four people who are being paid to work on Babel full time!
 
### Growing Maintainership
 
> https://github.com/babel/notes/blob/master/2017-04/april-08.md#proposed-babel-roadmap
 
- One or two clear priorities at all times from the project's perspective.
- Use each priority as a teaching opportunity for that section of the Babel code base.
- Will be slower than having one person just write the code, but pay dividends later.
 
### Priority Topic: Plugin Ordering
 
Issue: https://github.com/babel/babel/issues/5623
PR: https://github.com/babel/babel/pull/5735

#### Problem

- Babel doesn’t do anything at all by default. You must specify the plugins which are run.
- Once you specify the plugins you end up with ordering issues.
- Plugin A depends on Plugin B, if you do something in the "wrong" order you can get different output or an error.
- Primary example: class properties and decorators specified in the wrong order.
- Unit test: running babel twice, sort plugins A-Z and Z-A.
- Unblocks a number of things that we want to do, Boopathi: specifically in the minification space.

#### Strategy

- Champion: Henry, participate by opening pull requests targeting his branch. Has time during work for coding.
- If we have a dependency graph of all of the plugins we can check for duplicates and do better config validation.
- DAG (directed acyclic graph) resolution.
- Could provide us an opportunity for better error messages.
- Each plugin provides a certain capability or feature. (This is "before" and "after" in DAG terminology.)
- This is part of the core of Babel, we have to do some sort of plugin loading sorting.
 
### [Open Collective](https://opencollective.com/babel)
 
- How do you want this to work and what do you want this to do for Babel?
- Would like to have enough money to:
  - Meet in person and fly out people.
  - Support sending a person to TC39.
- Don't want to spend it on buying things as much as supporting efforts of maintainership.
- Money is important, but the number of people working on the project is actually the biggest limiting factor.
- Sven: Mailing t-shirts to contributors may be a worthwhile thing to do.
 
### [TC39](https://github.com/tc39)
 
- Group of people who work together to help specify JavaScript.
  - Implementers: write JavaScript interpreters and implement the features (but don't necessarily write JS)
  - Language designers: People who have been working in language design and desire features.
  - Developers: Users of the JavaScript language.
- Representatives from major companies.
- Logan was able to attend in [March](https://github.com/rwaldron/tc39-notes/blob/master/es8/2017-03/mar-21.md) in Portland.
- Last month it was in NYC so Henry was able to attend.
- Gave [a presentation](https://twitter.com/kosamari/status/867443846698987520) on how to use Babel to help specify JavaScript ([slides](https://github.com/hzoo/role-of-babel-in-js)).
- Two goals for Babel:
  - Backwards compatibility for all browsers with current language features.
  - Help TC39 in getting early feedback for the proposals that they come up with.
- Hope to get Babel plugins as an early indicator for feature gating.
- Now have some PRs from the proposals from last week coming from the proposal authors! (Ex: https://twitter.com/rwaldron/status/868207910580613120)
