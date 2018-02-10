---
layout: post
title: A short tutorial on software development
subtitle: Introduction
tags: [softwaretutorial]
---

Recently a couple of my friends and I wanted to start working on some software projects together. Altough talented, my friends don't have much experience developing software collaboratively. Developing software with other people can be a bit strange, frustrating even, if one is not serious about the development practices. It is quite easy to do more harm than good. It is possible to completely wipe the code that others' have written with a single 'git push' command. A single line of code can break an entire project. A lot of things can go wrong if one simply starts writing code without thinking about what one is doing.

Therefore I decided to write a very concise tutorial on how to do small software projects with a few collaborators, so that me and my friends can collaborate on whatever projects we want to. If anyone else wants to join in we can simply refer to this tutorial.

There are few things that induces so much frustration as when the team aspect of coding goes awry. Luckily most of the problems mentioned above can be avoided if the people writing the code follows a few software development practices. There are many different software development practices, and it is still heavily debated which ones are the best in which situations. In this tutorial I have chosen to follow a few of the practices from [Extreme Programming](https://www.agilealliance.org/glossary/xp/#q=~(filters~(postType~(~'post~'aa_book~'aa_event_session~'aa_experience_report~'aa_glossary~'aa_research_paper~'aa_video)~tags~(~'xp))~searchTerm~'~sort~false~sortDirection~'asc~page~1)). 

The topics discussed in this tutorial will be the following:
* Stories - How to break down something complex into manegable units
* Test Driven Development - Increasing the likelihood that the code works
* Git Workflow - How to not ruin others' code while working in parallell
* Code simply first and Refactoring - How to evolve the code and not get overburdened by features
* Continous Integration - How to make merge conflicts and diverging branches bareable
