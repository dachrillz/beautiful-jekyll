---
layout: post
title: Constructing the Natural Numbers
subtitle: A post on fundamental mathematics
tags: [foundational-mathematics]
---

Recently I have been very interested in the basic building blocks in both computer science and mathematics. Most of the time in school is spent on higher level matters, such as how to solve practical problems. For example I have taken several courses where different methods to [solve tricky integrals](https://en.wikipedia.org/wiki/Simpson%27s_rule) were discussed, or how to [find the eigenvalues of certain matrices](https://en.wikipedia.org/wiki/QR_algorithm) using numerical methods. This is reasonable, since it is in the end, more useful. However when studying computer science it is implied that one has to learn more about the fundamentals. Even though the language of choice for my computer engineering school is Java, (But they seem to flirt with the idea to switch over to Scala, which is cool) they still offer several courses were things are written in C. Because they want their students to better understand how a computer works.

This never happened in my mathematical education, which is a pity. I only took courses covering "the useful stuff". Therefore I decided to write a litte on some foundational mathematics, as I hope it depens my understanding of math in general.

With that said, which place is better to start with than the natural numbers? In many ways the natural number are the most fundamental building block in mathematics. If you have the natural numbers with their arithmetic operations, you can construct a lot of mathematics. Therefore it is really cool to see that we can actually construct the natural numbers with even more basic building blocks.

#The Peano Axioms

The most common way to construct the natural numbers is using the [Peano Axioms](http://mathworld.wolfram.com/PeanosAxioms.html) They can be stated as following:
1. zero is a number.
2. if $a$ is a number, the successor of $a$ is a number.
3. zero is no the successor of *any* number.
4. Two numbers where the successor are equal, are also equal.
5. If a set $S$ of numbers contain zero and every successor of every number in $S$, then every number is in $S$ (Induction Axiom)

Several things have to be explained here. First of which assumptions do we take when we use these axioms? 

Firstly we need the notion of sets. In particular we need the following set constructions along with the fundamental idea of sets:
1. Set Equality: if the sets $A$ and $B$ contain the same elements $\rightarrow$ A = B
2. Every set is a subset of itself, that is, $A \subseteq A$

We also need some notion of equality. The only thing we need are the following characteristics:
1. Reflexivity: $x=x$
2. Symmetry: if $x = y$ then $y = x$
3. Transitivity: if $x = y$ and $y = z$ then $x = z$
4. Equality has to be closed under the set. That is if $x\in S$ and $x=y$ then $y\in S$

Lastly we need a simple notion of a map called S. That is some construction that takes an input $x$ and outputs something $y$.

Armed with these basic tools we have basically everything we need to construct the natural numbers.

#Explaining the axioms:
Now I will step through the axioms one by one and explain how they actually bring about the natural numbers.

#$Zero is a number$:
This axiom simply states that there exists an element in the set $\mathbb{N}$ that is a number. It may seem circular to call this element zero, as zero is a very "natural numbers" concept. We would like to avoid the natural numbers when we construct natural numbers, as we don't want circular logic. However the name zero is simply what we call it. In one of the [videos](https://www.youtube.com/watch?v=3gBoP8jZ1Is&t=151s) that I refer to they called the zero element "zelda" in order to make the distinction clearer. We don't have anything that resembles the natural numbers yet, simply a set with an element that we happen to call zero.

#$a = 5$
