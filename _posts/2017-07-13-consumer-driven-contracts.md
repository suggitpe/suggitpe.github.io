---
layout: post
title: Consumer Driven Contracts
date: 2017-07-13
---

# Consumer Driven Contracts

In a complex system of systems, communications between these systems have become a major source of debate.  Over many years we have built patterns and idioms such as transactions, protocols and internmediaries to solve these problems.  Still today we overlook common design flaws such as implicit coupling through too strong a relationship between consumer and protocols, giving rise to fragility across the enterprise.

Postel’s law (robustness principle) observes that in general, an implementation must be conservative in its sending behaviour and liberal in its receiving behaviour (note: do not confuse liberal with ambiguous … see Robustness Principle Reconsidered).  Too often we find clients of a service (synchronous and asynchronous services) bound too tightly to the service output, for example if a client verifies the messages/events it receives with an XSD then any alteration (even additive alterations) will cause verification failure.  This would be an example of conservative receiving behaviour, thus implicit inter-system coupling.  Clients can adopt a more liberal receiveing behaviour through programatically asserting that the messages contain the things you need, not that the message conforms to the expansive consumer offering.

If we consider the relationship between client and provider as a contract, we can see two emerging sets of expectations from each side: 

1. The provider contract is the expansive set of things that a service provides to the broader set of consumers.  It will include Document Schemas, Interfaces, Conversations, Policy, etc.  They exhibit the following behaviours; closed and complete, singular and authoritative, with bounded stability and immutability.
1. The consumer contract contains all the things that a consumer of a service expects (these can be expressed as assertable statements, or tests).  Consumer contracts exhibit the following behaviours: open and incomplete, multiple and non-authoritattive with bounded stability and immutability.
    
“When a provider accepts and adopts the reasonable expectations expressed by the set of consumers, it enters into a Consumer Driven Contract” [Ian Robinson].

Assuming an adopted model of automated testing: typically an application will use a mock or a test double implementation of a service to assure correct behaviour in its application boundaries.  The trouble is that as each side mocks the others behaviour, each can misunderstand or misrepresent the actual behviour of the other side of the contract (especially as the reasonable expectations change over time).

The Consumer Driven Contract pattern (originally described by Ian Robinson, Thoughtworks, for Service Oriented Architectures) is an attempt to “create a vocabulary for describing the roles of the participants in a loosely coupled relationship”.  In this pattern the subset of the Provider Contract that the consmer is expecting (the Consumer Contract) is expressed as a collection of tests and is given to the Producer to verify at build time.  As long as the tests pass, a provider will know that its clients will not be affected by a change.  Or at the very least, release when a test fails and the provider knows they will be causing problems ...

Consider too the situation where a provider is exposing their service to the world-at-large (asynchronously or synchronously): in order to understand the impact of a breaking change in an API or protocol, through the execution of these Consumer Driven Contracts the provider can understand not only which parts of its service will constitute a breaking change, but also who is affected.  In short, through the execution of consumer contracts (tests), both the producer and consumer can change and release protocol changes safely, implicitly decoupled.


## Further reading:
* [Ian Robinson article](https://martinfowler.com/articles/consumerDrivenContracts.html)
* [Pact](https://docs.pact.io/)
* [Thoughtworks tech radar](https://www.thoughtworks.com/radar/techniques/consumer-driven-contract-testing)
* [Spring cloud contract](https://specto.io/blog/2016/11/16/spring-cloud-contract/)
* [Robustness Principle Reconsidered](http://queue.acm.org/detail.cfm?id=1999945)
