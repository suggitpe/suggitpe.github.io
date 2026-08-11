# Continuous Integration

## The Practice

Continuous Integration (CI) is a software development practice.  It is not a technique, nor is it a tool.  There are CI tools out there but just having them installed does not mean you are practising CI.  Continuous Integration is about applying a very basic principle: Integrate your code often and early.  Gerard Meszaros describes the principle really well in his [article](http://programmer.97things.oreilly.com/wiki/index.php/Integrate_Early_and_Often) on the subject.

So what is it?  My favourite definition of CI is from Martin Fowler's blog on [Continuous Integration](http://www.martinfowler.com/articles/continuousIntegration.html):

> Continuous Integration is a software development practice where members of a team integrate their work frequently, usually each person integrates at least daily - leading to multiple integrations per day. Each integration is verified by an automated build (including test) to detect integration errors as quickly as possible. Many teams find that this approach leads to significantly reduced integration problems and allows a team to develop cohesive software more rapidly

This is a great definition but worth exploring a little.  In the olden days (and I do go back bit so bear with me), very few development teams worked in a truly collaborative manner.  Specifications were handed to them, they wrote some code over a many week period, the build/environments team would build it and then ship it off to a test team (the only analogy I can picture here is literally throwing it over a wall to the testing team, who were kept at arms length).  Limited amounts of communication and no actual collaboration.  Sometimes even today we find teams that operate in this way.  What's worse is that the developers would work in isolation of each other over that many week period.  No surprise to any observer that the time to get the product into a workable state could be weeks of costly integration effort.  What's really embarrassing is that I remember at the time thinking that this was great: I was left to just write some code in peace (pat myself on the back).  Needless to say, as I look back at my approach I blush a little.

One of the (many) things that are wrong in my story, is the lack of code integration.  It could be many weeks before developers merge their code together and verify it's working.  Alistair Cockburn's [article](http://alistair.cockburn.us/Disciplined+Learning) on Disciplined Learning exemplifies the problem well.  

![Growth of Knowledge](http://alistair.cockburn.us/get/3364)

When we say integrate early and often, we really mean this.  All the code for the whole application should be merged often.  To my mind this is many times a day: some teams I have heard of have a 15 minute integration rule.  In a modern day version control system (we use Git, I think everyone should, with a collaboration platform like Github or Bitbucket) the act of integration should be a trivial thing (a pull - merge - commit - push cycle) and so we should do it often with small changes to the common code line.  A small change has the benefit that it can be easily backed out and thrown away if it is found to do damage (interestingly this is the same, equally valid, argument for smaller more frequent releases to the production environment).

We are missing an efficiency point in the basic principle though.  Integrating often makes the act of integration easier: smaller changes are simpler to merge when the code clashes with other changes (the effort required is small because the number of clashes is low with trivial clash resolutions).  It's also easier to verify the result of the merge: to fix any issues caused from it (as long as you can find them quickly enough through fast feedback).  Conversely, it is exponentially more expensive to integrate late in the development process.

The Continuous Integration process starts with an act of integration and ends with verification that the resulting code-base is valid.

So far we have talked about the practice.  To do the above in a team of five co-located developers is a relatively straight forward task to do manually.  Imagine a 'team' of 150 developers working on a common code-base, all integrating often: manually.  As this scales it stops working. A manual option here is out of the question.  Problems spiral out of control very quickly.  Even with automation, a large development function can quickly slip into chaos.

## The Automation
The act of Continuous Integration is a manual process, triggered from an assessment from a developer:

> _"This code is ready to integrate"_

The integration process is a publishing process by the developer.  The automation comes from the verification of the result of the integration.  Now that we have integrated how do we know that the composite result is good.  This is where "Continuous Integration tools", like TeamCity or Jenkins, play a part in the process.  I think "Continuous Integration tools" are really badly named, really the only Continuous Integration tool I use is Git and Github for merging my code to the mainline.  What "Continuous Integration tools" really do is to verify mainline (or a branch) after the merge in an automated way.  They are test and verification tools more accurately.  For now let's forget this nuance and focus on the big picture.

Typically a Continuous Integration tool is bound to a code-base and asked to periodically _'do verification stuff'_ on it.  Usually this is triggered from a change in the code, but equally it can be time based.  The most common use case is to watch for a change on the mainline; and when observed enter into a build and test cycle using the build tool of choice.  Once the build and test cycle is complete, the tool will update a status page (often referred to as a Build radiator).  Good practice would have this Build Radiator shown prominently so that failures alert everyone quickly and they can exercise a ['stop & fix'](https://wiki.umn.edu/pub/CarlsonToyotaWayReaders/WebHome/Chapter_8.doc) style response (ideally this is on a very large screen high up so everyone can see it).  If the radiator is not in a permanently prominent position, broken builds are ignored: conversely, when they are out in the open everyone cares about the builds.

## The paradox: feature branches
For any team, the practice of Continuous Integration gives the team assurance that they have built, and continue to build, a valid system (or part of one).  After every merge to mainline and verification (the integration) the Continuous Integration tool radiates the state of the build, giving a sense of well-being and satisfaction to the team, this is the teams safety net.

When the size of the contributing development community reaches a large enough size, and the length of time it takes to feedback success is too long; the Continuous Integration process breaks down.  If there are too many concurrent changes on mainline before the Continuous Integration verification process can complete; the original 'build breaker' is lost in the mists of time (versions).  A valid ('green') mainline is impossible to retain and a blame culture emerges as teams look at each other to resolve issues (irrespective of where the issue stemmed from).  The teams safety net has failed, gone too is the sense of well-being and satisfaction.

At this point we should probably to alter our definition of Continuous Integration to be something like:

> "integration of **verified** code early and often"

How do we ensure that we are only integrating verified code?  We need a mechanism that allows us to cherry pick changes that we know are good and exclude those that are unverified.  Here the use of either Github forks or branches allows us to segregate our changes from mainline until verified.  This is where the paradox stems from: on the one hand we want to integrate early and often; yet on the other hand we want to defer integrating until we trust the changes a little more.

Most Continuous Integration  tools have capabilities to verify branches alongside the mainline, so developing and pushing to branches can be automatically verified.  Once verified we can merge to the mainline knowing that the changes are valid.  Once we have merged to the mainline, other teams also know that our changes are good and so pull them onto their own branches.  In effect we continuously and eagerly integrate our changes with the changes on mainline, yet remain segregated from the 'suspicious' changes on other branches.  Teams should 'pull' from the mainline many times a day.

## Supporting a culture of quality first
So far we have talked about the practices and tools, but not the 'why'.  In our teams we should care about what we do, we should care that the thing we make is of good quality.  We should be proud of our products and services.  Indeed we should care that they excel at what they do.  We want to build software like Germany builds cars: quality cars.  When we chose to employ XP practices (such as CI) we chose quality as a primary output from what we do.  We care about the quality of what we produce, so we are eager to know when it fails to be a quality product.  When a CI radiator tells us the quality is not good enough, we stop in our tracks (aghast) and we fix it so it meets our quality standards.  Quality over all else is the thing we care about most.  

### Broken Windows
In 1969 Philip Zimbardo undertook an experiment where a pristine car was left in a reasonable neighbourhood in California for a week: no one touched it.  A week later, Zimbardo smashed one of the windows of the car.  Shortly, others joined in with the destruction.  The sumation of the work was that a successful strategy for preventing vandalism is to fix problems when they are small.  The principle we take away from this is:
> Don't live with broken windows

In the context of software engineering examples of broken windows are: poor design, unreadable code, bad decsions, an intermitently failing unit test.  When we work alongside broken windows, there is a propensity to think:
> The rest of the code is crap, I'll just follow suit.

The stop and fix mentality is primarily borne from this theory.  Quality is not something that is added as an after effect, it's either baked in or it does not exist.  Quality is not a factor of the outcome (i.e. what we produce), it's a factor of what we put in.  Unless we bake quality into our processes, we cannot hope to expect quality in the thing we produce.  A stop and fix mentality, is all about baking quality in.  The quality response to a failing build: is to immediately "stop the line" and fix the problem: repair the broken window before another one gets broken.

### Levels of maturity for CI usage
I see the following as criteria for a CI Maturity Model.  Every change committed to Version Control ...

1. is compiled
1. is tested with unit tests
1. is tested using different types of automated tests
1. is performed on a short lived feature branch, where it is tested using different types of automated tests.

Key thing to note here is that there is no mention of CI tooling, it is the practice that we are after and that _could_ be done manually.  Clearly we would choose to automate this ...

While mine is a very simple maturity model, a more expansive one is presented below factoring in a number of additional factors beyond the verification model:
![](http://www.infoq.com/resource/articles/Continuous-Delivery-Maturity-Model/en/resources/fig1large.jpg)

## Proposal for a Maturity Model
The following is a proposed additive maturity model (i.e. each stage extends the previous).  It is worth noting at this point that the whole purpose of Continuous Integration is to find problems fast.  Therefore it is really important to treat a failing CI build as a positive thing: we found a problem automatically (no man hours were spent finding out that there was a problem).

### Level 1: Compile
We often forget that statically compiled languages go through a number of phases in the compilation phase, the first is a parse and verification of the syntax.  This is a verification of the code, albeit a rather shallow one.  My first experience with CI (using Cruise Control some ten years ago) was just that, the compilation and linking phases of a large C++ application.  At the time this was progress, going from nothing to nightly builds was a huge step forward.  Even today, any team that has no CI implementation will benefit from a triggered code compilation: the compiler is a test tool of sorts.  If all the code compiles (I include linking here too) then the overall CI build also passes; if not, it fails. 

### Level 2: Unit tested
Modern development practices advocate the adoption of Test Driven Development techniques, where (at the most basic implementation) unit tests are written to _guide_ the development process.  A by-product of this technique is an amassing of unit tests that are tested alongside the compilation process.  Upon any committed change, the CI tooling should run the unit tests in addition to the compilation of the source code.  Any failing test will cause "the build" to fail, prompting the development teams to resolve the cause of the failing test immediately.

### Level 3: Tested using progressive automated test types
There are many different types of automated tests ranging from unit tests through to full system tests.  Unit tests tend to run quickly (if they do not they probably fail Michael Feathers [definition of a unit test](http://www.artima.com/weblogs/viewpost.jsp?thread=126923)), whereas full system tests tend to run more slowly.  The most important aspect of a CI process is feedback.  You want to now as soon as possible that there is an issue, or that its good to ship.  By organising your build into the following progressive phases you can expect an increasing level of confidence as the build progresses, yet also getting fast feedback throughout (there is little point in executing longer running tests if the unit tests are failing).

* Build and Unit Test
* Integration and sub-component testing
* Full system deployment and migration
* Full system verification
* Release

This is often regarded as a Build Pipeline as most famously described by Jez Humble and Dave Farley in their book [Continuous Delivery](http://martinfowler.com/books/continuousDelivery.html).

A fundamental principle to make this approach work is: build once, test many times.  Here we say for each of the phases we use the same artefact: after all, from a testing perspective it's the artefacts that we are interested in, not the code from which they were created.

### Level 4: Segregated away from mainline with a feature branch
Development teams when working efficiently tend to commit changes to the central code-base often (especially when working in TDD cycles).  In the most common case, teams commit these changes to the mainline directly (this is known as the unstable mainline branching strategy), which is fine until you want to release a discrete set of completed features (spanning many commits) to a formal environment (such as production).  Most teams will resolve this by simply shipping at defined times and getting all the customers to agree to the release.  What happens if one of the customers does not agree to the release?  It is usually very hard to remove the interleaved commits.

Different strategies can be employed to address this problem, for example feature toggles.  In a highly regulated environment this approach could be called into question: the credibility of releasing change under the guise of a feature toggle is questionable.

Segregating the functional change to a branch is a cleaner mechanism.  In this model we would expect that all of the changes of the feature (and to my mind a feature is distinguished by having value to our customers) to be developed on a branch and only merged when the feature is fully developed: from the mainline this would appear to be a single logical commit, albeit a large one.  In this model it is very important to ensure that all the branches are verified through the exact same continuous integration mechanism as for the mainline.  The build tells you that the branch is ready to merge.

## Conclusion
Continuous Integration is not a one size fits all practice. For some teams working of the mainline makes sense.  In the perfect state, all code is merged to the mainline many times a day.  We work in a highly regulated environment, where we need to discretely approve all requirements: we can't half release a requirement/story.   I have seen teams work with the mainline integration model, it can work.  However, my overriding observation is that this approach is hard and requires huge amounts of customer negotiation and co-ordination.  In a model where we focus on an evolving code-base driven by discrete functional requirements that need approval before releasing, I think our development processes evolve into the feature branch layer of the maturity model.

As a parting comment please remember that Continuous Integration is a practice: the tooling just makes following this practice a little easier.
