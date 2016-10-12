---
layout: post
title:  "Mutation testing using PITest"
date:   2016-08-05 16:20:00 +0200
categories: software tools testing
author: David
comments: true
---

The concept of mutation testing is actually quite simple:

Your code is mutated in certain places and then you test suite is run against it. 
If your tests fail, that means that your tests are good at detecting bugs. 
If your tests pass, they have allowed a bug through and so the mutant lives on.

Doing this for all your code means that you can rate the quality of your test suite.
when mutations live it might mean an issue with your test suite as it would be possible for a developer to change the code at that place without the tests noticing.

For java there is a very good library called PITest, it is fairly easy to run using the intellij plugin but you can also use the gradle plugin if that is your thing.