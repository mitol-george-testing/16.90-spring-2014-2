---
content_type: page
parent_title: 3.6 Introduction to Design Optimization
parent_uid: 6f317b0d-95c1-d32c-f178-c9fdbae632d2
title: 3.6 Introduction to Design Optimization
uid: 3cde12b3-c306-b87c-973f-5af561f4875f
---

*   [<Finite Difference Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-finite-difference-methods)
*   [3.6.1Design Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization)
*   [3.6.2Gradient Based Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-gradient-based-optimization)
*   [3.6.3Unconstrained Gradient-Based Optimization Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-unconstrained-gradient-based-optimization-methods)
*   [3.6.4Finite Difference Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-finite-difference-methods)
*   [3.6.5The 1d Search]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-the-1d-search)

3.6.5 The 1D Search
-------------------

[Measurable Outcome 3.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO317)

In this section, we detail how to compute an appropriate step size for a typical optimization step. This is referred to as a 1D line search, since we are searching for the minimum along the search direction. One common approach is to use polynomial interpolation to first construct an approximation for the objective function in the search direction.

Consider that at some point, \\(x^0\\), have \\(\\nabla J = \[ 1 \\ 2\]^ T\\). The steepest descent direction is then \\(S = -\\nabla J = \[-1 \\ -2\]^ T\\). To compute \\(\\alpha\\), we sample at three points along the direction \\(S\\), i.e., we compute the objective function value \\(J(x^0+\\alpha S)\\). We find  
\\(\\alpha =0\\), \\(J=10\\)  
\\(\\alpha =1\\), \\(J=6\\)  
\\(\\alpha =2\\), \\(J=8\\)

Also, we know that for \\(\\alpha =0\\),

| \\\[\\frac{dJ}{d\\alpha } = \\nabla J^ T S = -5\\\] | (3.78) 

Using these four pieces of data, we can fit a cubic polynomial to describe \\(J(\\alpha )\\):

| \\\[J(\\alpha ) = c\_1 + c\_2\\alpha + c\_3\\alpha ^2 + c\_4\\alpha ^3\\\] | (3.79) 

We solve for the coefficients by setting up the system

| \\\[\\left\[\\begin{array}{c c c c} 1 & 0 & 0 & 0 \\\\ 0 & 1 & 0 & 0 \\\\ 1 & 1 & 1 & 1\\\\ 1 & 2 & 4 & 8\\\\ \\end{array}\\right\] \\left\[\\begin{array}{c} c\_1 \\\\ c\_2 \\\\ c\_3 \\\\ c\_4 \\end{array}\\right\] =\\left\[\\begin{array}{c} 10 \\\\ -5 \\\\ 6 \\\\ 8 \\end{array}\\right\],\\\] | (3.80) 

giving solution \\(c\_1 = 10\\), \\(c\_2 = -5\\), \\(c\_3=0\\), \\(c\_4=1\\).

So we approximate \\(J\\) as \\(J(\\alpha ) = 10-5\\alpha + \\alpha ^3\\).

Now we want to find the \\(\\alpha\\) that minimizes \\(J(\\alpha )\\), i.e., set \\(-5+3\\alpha ^2=0\\), giving \\(\\alpha =\\sqrt {\\frac{5}{3}}=1.291\\).

This is the value of \\(\\alpha\\) that minimizes \\(J(x+\\alpha S)\\) in the given direction \\(S\\).

Consider that at some point, \\(x^0\\), we have \\(\\nabla J=\[1 3\]^ T\\). The steepest descent direction is then \\(S=-\\nabla J = \[-1 -3\]^ T\\). To compute a good step size \\(\\alpha\\), we sample at three points along the direction \\(S\\), i.e., we compute the objective function value \\(J(x^0 + \\alpha S)\\) for three different values of \\(\\alpha\\). Let's say that we find:  

\\(\\alpha =0, J=8\\)  
\\(\\alpha =1, J=6\\)  
\\(\\alpha =2, J=8\\)

Fit a cubic equation to approximate \\(J(\\alpha )\\), and find the value of \\(\\alpha\\) that minimizes this cubic equation.

The resulting value of \\(\\alpha\\) (to three decimals) that approximately minimizes \\(J(x+\\alpha S)\\) in the given direction \\(S\\) is:

Exercise 1

Numerical Response

CheckShow Answer

BackFinite Difference Methods