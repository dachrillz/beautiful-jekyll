---
layout: post
title: Demonstrating how a Neural Network Solves the XOR function, and why it has to have at least two inner nodes.
subtitle: A post on Machine Learning
tags: [Machine-Learning]
---
It was some time ago since I last wrote anything. I would like to start writing here again as it is a very nice way to actually delve deeper into subjects that I find interesting. One has to be pretty meticulous when doing these blog posts, since people might actually read what I have done.

This time around we are having a look at machine learning. I remember reading an awesome blog post some time ago that discussed the limitations of neural networks. I can't exactly remember what the author wrote, but it was along the lines of that feed forward neural networks only can solve problems that can be linearly separated in some transformation.

What does this mean? It means that when we add hidden layers to a neural network we have to consider how many hidden nodes we add. As this increases the number of linear separators that the network can use to solve a specific problem. 

A note, I'm not entirerly clear how this relates to regression, since I only looked at classification, so any conclusions drawn here might not immediately translate to regression.
# The XOR function 
In order to demonstrate what I mean by *number of linear separators* we are going to have a look at the XOR function. The XOR function is simply defined as:
1. $XOR(0,0) = 0$
2. $XOR(0,1) = 1$
3. $XOR(1,0) = 1$
4. $XOR(1,1) = 1$

That is it is a function that is exclusively only $1$ if exactly one of its inputs are equal to $1$. This function is interesting as it is the pretty much the [simplest function that can not be solved by a linear classifier.](http://www.ece.utep.edu/research/webfuzzy/docs/kk-thesis/kk-thesis-html/node19.html) This function demonstrates one of the reasons why deep neural networks are fascinating and useful. Because we can solve this problem using the back propagation algorithm. Before neural networks one had to use non linear classification methods. There is nothing wrong with these, but what makes neural networks great is that we can, as long as we have enough data, in a very generic way search for solutions to these class of problems. Very powerful indeed.

# The Neural Network
In order to show how a Feed Forward Neural Network solves this problem I wrote a small python program that is referenced at the bottom of this blog post. This Neural network consists of two inputs, two hidden nodes and one output node. 

Mathematically this neural network is defined as following:
1. $y(z_1,z_2) = w_{1}^{(2)} * z_1 + w_{2}^{(2)} * z_2 + b^{(2)}$
2. $z_1(x_1,x_2) = w_{12}^{(1)} * x_1 + w_{12}^{(1)} * x_2 + b_1^{(1)}$
3. $z_2(x_1,x_2) = w_{22}^{(1)} * x_1 + w_{22}^{(1)} * x_2 + b_2^{(1)}$
4. $x_1$ and $x_2$ are $1$-dimensional scalars.

The weights and biases are uninteresting for this particular post and were simply set to values that solved the XOR problem.

#How the network solves the problem
If one plots the results of the inner nodes one can see why we need at least two inner nodes to solve the problem.
References:

![First Inner Node](https://raw.githubusercontent.com/dachrillz/dachrillz.github.io/master/img/xor/z1.png)

![Second Inner Node](https://raw.githubusercontent.com/dachrillz/dachrillz.github.io/master/img/xor/z2.png)


![Contour Plot](https://raw.githubusercontent.com/dachrillz/dachrillz.github.io/master/img/xor/Figure_1.png)




#References:
1. [Infinite series](https://www.youtube.com/watch?v=3gBoP8jZ1Is&t=151s)
2. [Wikipedia](https://en.wikipedia.org/wiki/Peano_axioms)
3. [Wolfram Alpha](http://mathworld.wolfram.com/PeanosAxioms.html) 

