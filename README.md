E-IG
====

E-IG is a non-profit organization, focused on providing standards and interfaces for common e-commerce related
problems. We discuss about PHP, OpenSource, about E-commerce and about how current implementations can be solved in
a better way, sharing ideas, acknowledge and expertise.

Standards
=========

We have not discussed any standard yet, but we have some ideas in the pipeline, in which we will start working as
soon as possible. You will see that all ideas are really far from the specific business logic, so the idea is to 
solve the less specific implementations of these projects

* Money - There are some Money implementations in the PHP ecosystem, all of them different and incompatible between
them. The implementation behind this idea should cover common methods in all implementations in order to be able to
switch between them easily and softly.
* Locations - Each E-commerce implementation implements all Location architecture in a very different way. The main focus here should be finding a common way to define how these locations can be fetched, so each project can expose
their implementation as a simple service. This means that we can share these implementations or even unify them 
all.
* Currencies - Maybe we can find a way of sharing this concept. In fact, currencies will always be currencies, no
matter the project, no matter the technology. Let's discuss how can we meet here.

Proposing a Standard Recommendation
===================================

To propose a PHP Standard Recommendation (PSR):

* fork this repo, create a branch, checkout that branch, add the PSR in proposed/, push the branch to Github, and
send a pull request; or,
* create a ticket to start a discussion on Github; or,
* start a conversation on the [mailing list](http://groups.google.com/group/e-ig/).

Requesting Membership
=====================

We aim to create a small group, composed by one representant from each E-commerce project.

> You don't need to be a voting member of this group for adding your feedback, opening new proposals, and discuss
> them.

If you are representant of an E-commerce project, start a conversation on the [mailing list](http://groups.google.com/group/e-ig/) proposing your candidature.
