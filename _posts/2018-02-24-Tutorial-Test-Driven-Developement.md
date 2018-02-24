---
layout: post
title: Test Driven Development
subtitle: Increasing the likelihood that the code works.
tags: [softwaretutorial]
---

Out of all the topics that is touched upon in this series test driven development is arguably the most important one. Some people might argue that it takes too much time to write tests, when they could be writting the proper code instead. Some people also argue that they are confident in their coding skills and therefore don't need to write unit tests.

Even if these two points might be true for some programmers, tests should still always be used alongside code that is going into production. These are the reasons:

## Tests increases the likelihood that the code works
If a test is properly written and covers the most essential cases then it can be used to check whether the code works or not. Because if the test clear then your code behaves as the test was defined! This point is a little obvious maybe and is probably the first benefit people think about when they hear tests. There are several more reasons for why one should use tests however!

##Tests work as documentation
Tests work excellent as documentation for code as well. Because if a test clears when you run it, you know that the code behaves as the test dictates. Therefore one can look at the tests, see what goes into some code and what comes out and use that to make sense of what the code does. If the tests are named properly this gets even easier. For example what would you expect a unit test called "test_if_function_sorts_list_after_age" to do?

##Tests make sure you didn't break anything
If you have good test coverage on all the code you have written so far you can be sure that the code works as these tests are defined. If you now add a new feature or refactor the code and the tests still clear, that is an indication to that you did not break anything. Contrary if you change something in the code and some tests fail, then you know for sure that you broke something! It can't be understated how helpful this is when one does projects that are larger than hobby size. Software projects become complex almost immediately, especially when you work with other people who reason about coding differently than you do. If you have good test coverage, you can pretty safely add new code and change the old code. It should also be added that this is especially important when you develop something in an agile fashion. Since we develop the code as we learn about the domain, we are going to make design mistakes and we are going to do a lot of refactoring. If one does not have unit tests this task becomes a nightmare.

##j
