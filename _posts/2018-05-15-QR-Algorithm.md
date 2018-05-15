---
layout: post
title: The QR Algorithm
subtitle: The first algorithm that really blew my mind
tags: [numerical-analysis]
---

# Eigenvalues

One very important concept of mathematics is eigenvalues and eigenvectors. An eigenvector is the vector that when multiplied by a certain matrix, produces the same vector, possibly with a different length. Mathematically speaking this is defined as:

$Av = \lambda v$

Where A is some $n \times n$ matrix, $v$ is the eigenvector of length $n$ and $\lambda$ is the eigenvalue, a scalar.

Eigenvalues emerge everywhere in pure mathematics and in practical applications meaning that it is often of great interest to calculate them. This can be done by solving the so called characteristic equation of the matrix $A$. That is one has to solve

$det(A - \lambda I) = 0$

Where $det$ is the determinant and $I$ is the identity matrix.

This produces a polynomial of degree $n$, where the eigenvalues for the matrix are the roots of this polynomial. This is the way one usually calculates eigenvalues in a course in linear algebra. This works fine when $n$ is small. However, what happens if we want to calculate eigenvalues for large $n$? This quickly becomes cumbersome as we have to find roots to a polynomial of high degree.

One solution to this problem is to turn to numerical analysis.

# QR algorithm

Numerical analysis is all about taking shortcuts. This is probably the coolest short cut I have seen so far. Most numerical algorithms are very sophisticated and more or less hard to implement. This algorithm however, is dead simple. It can be stated as following:

Initialize: $A^{(0)}$

$for k = 1,2,\dots \\

\ \ Q^{(k)}R^{(k)} = A^{(k-1)} \\

\ \ A^{(k)} = R^{(k)}Q^{(k)} \\

end$

Some things need to be explained here. First of all what does the variables mean. $A^{(0)}$ is the matrix whose eigenvalues we want to find. Imediately after the for loop $Q$ and $R$ are introduced. This is the so called QR-decomposition of the matrix $A^{(k-1)}$. This decomposition will be described shortly, and why we use it. In the final line of the for loop the two matrices $R^{(k)}$ and $Q^{(k)}$ are multiplied together in the opposite order. The result is what we call $A^{(k-1)}$ for the next iteration.

# The QR decomposition

As previously stated the algorithm decomposes $A$ into the two matrices $Q$ and $R$. What is interesting about this composition is that the matrix $Q$ is and orthogonal matrix, that is $QQ^T = Q^TQ = I$ and $R$ is an upper diagonal matrix. This is essential for work, because if we combine it with yet another theorem we get an incredible result.

## definition: Similar matrices
Two matrices $C$ and $D$ are called $\textit{similar}$ if the following holds:

$C = P^{(-1)}DP$

where $P$ is some invertible matrix.





References:
1. [Infinite series](https://www.youtube.com/watch?v=3gBoP8jZ1Is&t=151s)
2. [Wikipedia](https://en.wikipedia.org/wiki/Peano_axioms)
3. [Wolfram Alpha](http://mathworld.wolfram.com/PeanosAxioms.html) 
