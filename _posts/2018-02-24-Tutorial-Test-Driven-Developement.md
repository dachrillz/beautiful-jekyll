---
layout: post
title: Stories
subtitle: How to break down something complex into manegable units
tags: [softwaretutorial]
---

To make sense of a software project is a daunting task. A lot of times one does not really know how the final product should look, and even less how the code should look. There are a million ways to design a solution and a million libraries still that can help you implement this solution. This is a short tutorial on how to break down a complex project into simpler tasks.

One way to handle a project is to follow the [waterfall](https://www.tutorialspoint.com/sdlc/sdlc_waterfall_model.htm) model. The waterfall model is quite simple in it's concepts. We set up requirements, we design the product, we code it, we deploy it and finally we maintain the final product. This method is reasonable if we know exactly what kind of product we want. But it relies on that the requirements and the design are stable. If we learn something new about the problem that we try to solve in the coding phase, we risk having to go back and redo the design, and as a consequence, redo a lot of work in the coding phase. 

![Waterfall](https://www.tutorialspoint.com/sdlc/images/sdlc_waterfall_model.jpg)

Since the whole point of working on side projects with friends is to explore new domains and technology the waterfall approach will work poorly. More often than not we will be in a state where we don't understand the problem we try to solve, or even how we want the final product to look. One solution to this problem is to work [Agile](https://en.wikipedia.org/wiki/Agile_software_development).

Instead of trying to make sense of all of the project at once, we simply work with what we know now. One way to translate the ideas that we have in our head into something we can use is to use [stories](http://www.agilemodeling.com/artifacts/userStory.htm)

A story is simply an informal description of a feature that you want the program to have. Instead of making a complete, and complex specification of the whole project we can break down the features we want into these much simpler units.

A story can look like following:

| Story 1  |
| :------  |
| Feature: The user should be able to load files into the program|
| Depends on: Story 2						 |
| Example: Some example that elaborates the story.		 |
| Tasks: 							 |
|	1: Add GUI						 |
|	2: Add load functionality to program			 |
| Priority: Medium						 |
 
As one can see, a story does not have to be complicated, neither should it be. It is often tempting to try to start with the implementation details. To start with elaborate design patterns, libraries and state of the art apis. That comes later. We can spend weeks learning a particular library just to realize that we don't really need it. Stories are an excellent first step in making sense of what we want the product to look like.

Stories can also be about things not directly related to the user. This can look like following:

| Story 3  |
| :------  |
| Feature: The program should have a sin(x) function		 |
| Depends on: -							 |
| Example: The function should work like the mathematical sin(x) |
| Test Cases: sin(0)=0, sin(2pi)=0, ...				 |
| Priority: low							 |

The nice thing about stories is that we can pile them up. If you realise that you want a feature, you simply write a story for it. We don't have to implemented all of the features and if we realise that we don't want a certain story we simply remove it. In later posts it will be elaborated how one can write good quality code in conjunction with using stories. (It is related to writing tests and refactoring)

*In conclusion:* 
Most likely we don't understand the domain of a project fully when we work on it. This means that we can't make a full design of the product that we develop in a given instance. Therefore we work with what we know now. We write stories which are informal descriptions of a feature that we want the product to have. We don't fret over implementation details! A story is also rarely stupid. If we realise that we don't want it later, we simply throw it away. Since it was just an informal description anyways, we didn't waste too much time on it. 

Lastly, it is always better to have too many stories than too few. This can't be stressed enough, *if we don't like a feature later we simply throw the story away*. In later posts I will elaborate how we can keep high code quality while still working in an agile fashion.

