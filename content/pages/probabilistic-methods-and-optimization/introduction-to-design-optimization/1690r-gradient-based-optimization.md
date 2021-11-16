---
content_type: page
parent_title: 3.6 Introduction to Design Optimization
parent_uid: 6f317b0d-95c1-d32c-f178-c9fdbae632d2
title: 3.6 Introduction to Design Optimization
uid: 1d39506a-8ae7-400e-107d-fe048008e5c2
---

*   [<Introduction to Design Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization)
*   [3.6.1Design Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization)
*   [3.6.2Gradient Based Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-gradient-based-optimization)
*   [3.6.3Unconstrained Gradient-Based Optimization Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-unconstrained-gradient-based-optimization-methods)
*   [3.6.4Finite Difference Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-finite-difference-methods)
*   [3.6.5The 1d Search]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-the-1d-search)
*   [\>Unconstrained Gradient-Based Optimization Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-unconstrained-gradient-based-optimization-methods)

3.6.2 Gradient Based Optimization
---------------------------------

[Measurable Outcome 3.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO317)

Most optimization algorithms are iterative. We begin with an initial guess for our design variables, denoted \\(x^0\\). We then iteratively update this guess until the optimal design is achieved.

| \\\[x^ q = x^{q-1} + \\alpha ^ q S^ q, \\; q = 1,2, \\ldots\\\] | (3.67) 

where

\\(q\\)=iteration number

\\(x^ q\\) is our guess for \\(x\\) at iteration \\(q\\)

\\(S^ q \\in \\mathbb {R}^ n\\) is our vector search direction at iteration \\(q\\)

\\(\\alpha ^ q\\) is the scalar step length at iteration \\(q\\)

\\(x^0\\) is given initial guess.

At each iteration we have two decisions to make: in which direction to move (i.e., what \\(S^ q\\) to choose, and how far to move along that direction (i.e., how large should \\(\\alpha ^ q\\) be). Optimization algorithms determine the search direction \\(S^ q\\) according to some criteria. Gradient-based algorithms use gradient information to compute the search direction.

For \\(J(x)\\) a scalar objective function that depends on \\(n\\) design variables, the gradient of \\(J\\) with respect to \\(x=\[x\_1 x\_2 \\ldots x\_ n\]^ T\\) is a vector of length \\(n\\). In general, we need the gradient evaluated at some point \\(x^ k\\):

| \\\[\\nabla J(x^ k) = \[ \\frac{\\partial J}{\\partial x\_1}(x^ k) \\ \\ldots \\frac{\\partial J}{\\partial x\_ n}(x^ k) \]\\\] | (3.68) 

The second derivative of \\(J\\) with respect to \\(x\\) is a matrix, called the Hessian matrix, of dimension \\(n \\times n\\). In general, we need the Hessian evaluated at some point \\(x^ k\\):

| \\\[\\nabla ^2 J(x^ k) = \[ \\frac{\\partial ^2 J}{\\partial x\_1^2}(x^ k) \\ \\ldots \\frac{\\partial ^2 J}{\\partial x\_1 \\partial x\_ n}(x^ k) \\\\ \\frac{\\partial ^2 J}{\\partial x\_1 \\partial x\_ n}(x^ k) \\ \\ldots \\frac{\\partial ^2 J}{\\partial x\_ n^2}(x^ k)\]\\\] | (3.69) 

In other words, the \\((i,j)\\) entry of the Hessian is given by,

| \\\[\\nabla ^2 J(x^ k)\_{i,j} = \\frac{\\partial ^2 J}{\\partial x\_ i \\partial x\_ j}(x^ k)\\\] | (3.70) 

Consider the function \\(J(x)=3x\_1 + x\_1 x\_2 + x\_3^{2} + 6x\_2^{3} x\_3\\).

Enter the gradient evaluated at the point \\((x\_1,x\_2,x\_3)=(1,1,1)\\):

Exercise 1

 \\((4, 7, 9)\\)

 \\((5, 19, 3)\\)

 \\((4, 19, 8)\\)

Enter the last row of the Hessian evaluated at the point \\((x\_1,x\_2,x\_3)=(1,1,1)\\):

Exercise 2

 \\((3, 18, 2)\\)

 \\((0, 18, 2)\\)

 \\((0, 16, 2)\\)

CheckShow Answer

BackIntroduction to Design Optimization ContinueUnconstrained Gradient-Based Optimization Methods