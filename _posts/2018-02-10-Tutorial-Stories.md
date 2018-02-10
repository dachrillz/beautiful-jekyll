---
layout: post
title: Stories
subtitle: How to break down something complex into manegable units
tags: [softwaretutorial]
---

To make sense of a software project is a daunting task. A lot of times one does not really know how the final product should look, and even less how the code should look. There are a million ways to design a solution and a million libraries still that can help you implement this solution. This is a short tutorial on how to break down a complex project into simpler tasks.

One way to handle a project is to follow the [waterfall](https://www.tutorialspoint.com/sdlc/sdlc_waterfall_model.htm) model. The waterfall model is quite simple in it's concepts. We set up requirements, we design the product, we code it, we deploy it and finally we maintain the final product. This method is reasonable if we know exactly what kind of product we want. But it relies on that the requirements and the design are stable. If we learn something new about the problem that we try to solve in the coding phase. We risk having to go back and redo the design, and as a consequence, redo a lot of work on the coding phase. 

![Waterfall](https://www.tutorialspoint.com/sdlc/images/sdlc_waterfall_model.jpg)

Since the whole point of working on side projects with friends is to explore new domains and technology the waterfall approach will work poorly. More often than not we will be in a state where we don't understand the problem we try to solve, or even how we want the final product to look. One solution to this problem is to work [Agile](https://en.wikipedia.org/wiki/Agile_software_development).

Instead of trying to make sense of all of the project at once. We simply work with what we know now. One way to translate the features and ideas that we have in our head to something we can use to design the product is to simply use [stories](http://www.agilemodeling.com/artifacts/userStory.htm)

A story is simply a informal description of a feature that you want the program to have. Instead of making a complete, and complex specification of the whole project we can break down the features we want into these much simpler units.

A story can look like following:

| Story 1  |
| :------  |
| Feature: The user should be able to load files into the program|
| Depends on: Story 2						 |
| Example: Some example that elaborates the story.		 |
| Priority: Medium						 |

As one can see, a story does not have to be complicated, neither should it be. It is often tempting to try to start with implementation details. To start with elaborate design patterns, libraries and state of the art apis. That comes later, we can spend weeks learning a particular library just to learn that we don't really need it. Stories is an excellent first step in making sense of what we want the product to look like.

Stories can also be about things not directly related to the user. This can look like following:

| Story 3  |
| :------  |
| Feature: The program should have a sin(x) function		 |
| Depends on: -							 |
| Example: The function should work like the mathematical sin(x) |
| Test cases: sin(0)=0, sin(2pi)=0, ...				 |
| Priority: low							 |

