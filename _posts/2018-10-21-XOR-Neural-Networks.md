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
4. $XOR(1,1) = 0$

That is it is a function that is exclusively only $1$ if exactly one of its inputs are equal to $1$. This function is interesting as it is the pretty much the [simplest function that can not be solved by a linear classifier.](http://www.ece.utep.edu/research/webfuzzy/docs/kk-thesis/kk-thesis-html/node19.html) This function demonstrates one of the reasons why deep neural networks are fascinating and useful. Because we can solve this problem using the back propagation algorithm. Before neural networks one had to use non linear classification methods. There is nothing wrong with these, but what makes neural networks great is that we can, as long as we have enough data, in a very generic way search for solutions to these class of problems. Very powerful indeed.

# The Neural Network
In order to show how a Feed Forward Neural Network solves this problem I wrote a [small python program](https://github.com/dachrillz/BlogPostNeuralNetworks/blob/master/xorneuralnetwork.py). This Neural network consists of two inputs, two hidden nodes and one output node. 

Mathematically this neural network is defined as following:
1. $y(z_1,z_2) = g(w_{1}^{(2)} * g(z_1) + w_{2}^{(2)} * g(z_2) + b^{(2)})$
2. $z_1(x_1,x_2) = w_{12}^{(1)} * x_1 + w_{12}^{(1)} * x_2 + b_1^{(1)}$
3. $z_2(x_1,x_2) = w_{22}^{(1)} * x_1 + w_{22}^{(1)} * x_2 + b_2^{(1)}$
4. $x_1$ and $x_2$ are $1$-dimensional scalars, and the function $g(x)$ is the *tanh* function.

The weights and biases are uninteresting for this particular post and were simply set to values that solved the XOR problem.

# How the network solves the problem
If one plots the results of the inner nodes one can see why we need at least two inner nodes to solve the problem.

This is a contour plot from of $z_1$ node.
![First Inner Node](https://raw.githubusercontent.com/dachrillz/dachrillz.github.io/master/img/xor/z1.png)

This is a contour plot of the $z_2$ node.
![Second Inner Node](https://raw.githubusercontent.com/dachrillz/dachrillz.github.io/master/img/xor/z2.png)

These two nodes simply act as linear separators. That is they separate the domain into two planes using a line.
To interpret these contour plots as discrete boolean functions, simply give them the inputs, and transform the value $-1$ to $0$, keep $1$ as $1$.

![Contour Plot](https://raw.githubusercontent.com/dachrillz/dachrillz.github.io/master/img/xor/Figure_1.png)

However when we combine them as following: 
$y(z_1,z_2) = g(w_{1}^{(2)} * z_1 + w_{2}^{(2)} * z_2 + b^{(2)})$
something interesting happens. As previously said, the weights and biases are uninteresting. They simply move the lines around somewhat. What is really interesting is that by adding the two linear classifiers $z_1$ and $z_2$ together we get a non linear classifier!

# Trying the same thing with one hidden node.
To demonstrate why we really need two nodes I also tried to solve the XOR function with only one hidden node. It resulted in the following contour plot:
![Contour Plot](https://raw.githubusercontent.com/dachrillz/dachrillz.github.io/master/img/xor/zsingle.png)

As one can see. No matter which weights or biases we choose, there is no way that this linear classifier can ever classify anything that is not linearly separable in a satisfactory way. 

This thus somewhat demonstrates that certain problems require a certain depth of the neural networks. The more nodes we add to the hidden layer, the more complex decision boundary we should be able to construct.

And in fact if one add yet another layer the complexity of the separators increase even more. A second hidden layer was added and this produced the following classifier. This does not really look like XOR any more, but it is at least interesting to see that the number of nodes directly corelates with the complexity of the separators.
![Contour Plot](https://raw.githubusercontent.com/dachrillz/dachrillz.github.io/master/img/xor/three.png)

# Some conclusions

It's been a while since I last touched machine learning, so it was nice to get a refresher on the subject. Once I have more time on my hands I might delve deeper into the theory of neural networks. I remember that the blog post I mentioned earlier talked about how we might have to analyze how separable a set of data actually is (That is there any transformation that can linearly separate the data?) in order to assess how well a neural network can perform on it. That would be interesting to explore further.
