---
layout: post
title: Demonstrating how a Neural Network Solves the XOR function, and why it has to have at least two inner nodes.
subtitle: A post on fundamental mathematics
tags: [Machine-Learning]
---
It was some time ago since I last wrote anything. I would like to start writing here again as it is a very nice way to actually delve deeper into subjects that I find interesting. One has to be pretty meticulous when doing these blog posts, since people might actually read what I have done.

This time around we are having a look at machine learning. I remember reading an awesome blog post some time ago that discussed the limitations of neural networks. I can't exactly remember what the author wrote, but it was along the lines of that feed forward neural networks only can solve problems that can be linearly separated in some transformation.

What does this mean? It means that when we add hidden layers to a neural network we have to consider how many hidden nodes we add. As this increases the number of linear separators that the network can use to solve a specific problem. 

A note, I'm not entirerly clear how this relates to regression, since I only looked at classification, so any conclusions drawn here might not immediately translate to regression.
# The XOR function 
In order to demonstrate what I mean by *number of linear separators* we are going to have a look at the XOR function. The XOR function is simply defined as:
\begin{equation}
1. XOR(0,0) = 0
2. XOR(0,1) = 1
3. XOR(1,0) = 1
4. XOR(1,1) = 1
\end{equation}
That is it is a function that is exclusively only $1$ if exactly one of its inputs are equal to $1$. This function is interesting as it is the pretty much the [simplest function that can not be solved by a linear classifier.](http://www.ece.utep.edu/research/webfuzzy/docs/kk-thesis/kk-thesis-html/node19.html) This function demonstrates one of the reasons why deep neural networks are fascinating and useful. Because we can solve this problem using the back propagation algorithm. Before neural networks one had to use non linear classification methods. There is nothing wrong with these, but what makes neural networks great is that we can, as long as we have enough data, in a very generic way search for solutions to these class of problems. Very powerful indeed.

# The Neural Network
In order to show how a Feed Forward Neural Network solves this problem I wrote a small python program that is referenced at the bottom of this blog post. This Neural network consists of two inputs, two hidden nodes and one output node. 

Mathematically this neural network is defined as following:
\begin{equation}
1. y(z_1,z_2) = w_{1}^{(2)} * z_1 + w_{2}^{(2)} * z_2 + b^{(2)}
2. z_1(x_1,x_2) = w_{12}^{(1)} * x_1 + w_{12}^{(1)} * x_2 + b_1^{(1)}
3. z_2(x_1,x_2) = w_{22}^{(1)} * x_1 + w_{22}^{(1)} * x_2 + b_2^{(1)}
\end{equation}
$x_1$ and $x_2$ are $1$-dimensional scalars.

# Explaining the axioms:
Now I will step through the axioms one by one and explain how they actually bring about the natural numbers.

## 1. zero is a number:
This axiom simply states that there exists an element in the set $\mathbb{N}$ that is a number. It may seem circular to call this element zero, as zero is a very "natural numbers" concept. We would like to avoid the natural numbers when we construct natural numbers, as we don't want circular logic. However the name zero is simply what we call it. In one of the [videos](https://www.youtube.com/watch?v=3gBoP8jZ1Is&t=151s) that watched to research this, they called the zero element "zelda" in order to make the distinction clearer. We don't have anything that resembles the natural numbers yet, simply a set with an element that we happen to call zero.

## 2. if $a$ is a number, the successor of $a$ is a number:
Here we introduce the concept of a *successor* The successor is simply a map that takes one element from the set we are constructing and outputs another element in the same set. The assumption we make through the axiom here is that if the input of the successor is a natural number, then the output is as well. This axiom provides closure under the $\mathbb{N}$ as we can never leave the natural numbers using the map $S$. However it does not give us much more. It almost gives us some notion of orderness, which is essential for the natural numbers, but only almost. Given the two axioms we have now we can have that the successor of $0$ is $0$, $S(0) = 0$, which is not at all how we think about the natural numbers. This brings us to axiom 3...

## 3. zero is not the successor of *any* number:
This axiom states that $S(0) = 0$ is not allowed. This still does not bring order to the set, as we can still have $S(S(0)) = S(0)$, which is akin to saying that the successor of $2$ is $1$. Which is not very natural number-like.

## 4. Two numbers where the successors are equal, are also equal:
This axiom finally brings the notion of orderness to the set. Because if $S(x) = S(y), then x=y$. This implies that $S(S(0)) = S(0)$ is not allowed, since $S(0) \neq 0$ from axiom $3$. This also holds inductively since: $S(S(S(0))) = S(S(0)) \rightarrow S(S(0)) = S(0) $, which was not allowed. 

If we now combine the axioms we can construct an infinite chain of successors as following:
1. $zero \in \mathbb{N}$ (axiom 1)
2. $S(zero) \in \mathbb{N}$ (axiom 2)
3. $S(zero) \neq zero$ (axiom 3)
4. $S(S(zero)) \in \mathbb{N}$ (axiom 2)
5. $S(S(zero)) \neq zero$ (axiom 3)
6. $S(S(zero)) \neq S(zero)$ (axiom 4)
7. $S(S(S(zero) \neq zero$ (axiom 3)
8. $S(S(S(zero))) \neq S(S(zero))$ (axiom 4)
9. and so on...

By using axiom 2,3 and 4 repetively we can construct an infinite chain that has very natural number-like characteristics. Simply by giving the different successors different names we have something that we can call the natural numbers! If you have not figured it out by yourself the names are:
$zero = 0, \\ 
S(zero) = 1, \\
S(S(zero)) = 2, \\
S(S(S(zero))) = 3 \\ $
and so on... 

# If a set $S$ of numbers contain zero and every successor of every number in $S$, then every number is in $S$:

We almost have a set that satisfies how we think of natural numbers. However one final axiom has to be added. We only said that there exists an element $zero$ in $\mathbb{N}$ and then we constructed the numbers from it using the successor map. However we have not said anything about elements that are not allowed in the set. What if there exists two elements in $\mathbb{N}$ called $a$ and $b$ that have the following properties $S(a) = S(b)$? This does not violate any of the previous four axioms as we can not reduce this succession application down to anything simpler in order to invoke axiom 4. This is weird as we have two different element whose successors are equal. This totally breaks the order of the set. 

Therefore a final axiom is introduced: *If a set $S$ of numbers contain zero and every successor of every number in $S$, then every number is in $S$*. This axiom basically says is that if we have a set $S$ that satisfies the first four axioms, that is it contains our countably infinite chain of successors and the zero element, then this set is the set $\mathbb{N}$. If we add anything else to it then it is not something we call the natural numbers. An other way to state this axiom is to say that $\mathbb{N}$ is the smallest set that satisfies the first four Peano Axioms. This way we avoid the weirdness that happens when we introduce the elements $a$ and $b$, or any other non natural like elements we can think of.

References:
1. [Infinite series](https://www.youtube.com/watch?v=3gBoP8jZ1Is&t=151s)
2. [Wikipedia](https://en.wikipedia.org/wiki/Peano_axioms)
3. [Wolfram Alpha](http://mathworld.wolfram.com/PeanosAxioms.html) 

