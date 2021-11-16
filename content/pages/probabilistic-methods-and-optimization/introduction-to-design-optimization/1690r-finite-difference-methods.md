---
content_type: page
parent_title: 3.6 Introduction to Design Optimization
parent_uid: 6f317b0d-95c1-d32c-f178-c9fdbae632d2
title: 3.6 Introduction to Design Optimization
uid: c0e755e7-48fd-33db-4782-88b736e0381c
---

*   [<Unconstrained Gradient-Based Optimization Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-unconstrained-gradient-based-optimization-methods)
*   [3.6.1Design Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization)
*   [3.6.2Gradient Based Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-gradient-based-optimization)
*   [3.6.3Unconstrained Gradient-Based Optimization Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-unconstrained-gradient-based-optimization-methods)
*   [3.6.4Finite Difference Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-finite-difference-methods)
*   [3.6.5The 1d Search]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-the-1d-search)
*   [\>The 1d Search]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-the-1d-search)

3.6.4 Finite Difference Method Applied to 1D Convection
-------------------------------------------------------

[Measurable Outcome 3.19]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO319)

Generally the objective function and constraints are complex, nonlinear functions of the design variables which are not known analytically. We therefore cannot compute analytic derivatives for the required gradients and Hessian information. However, it is still possible to estimate the gradient and Hessian using other methods. The simplest approach is to use finite differences.

A one-sided finite difference requires \\(n+1\\) function evaluations. The gradient is estimated as

| \\\[\\frac{\\partial J}{\\partial x\_ j} \\approx \\frac{J(x\_1,x\_2,\\ldots ,x\_ j+\\Delta x\_ j, x\_{j+1},\\ldots ,x\_ n)-J(x\_1,x\_2,\\ldots ,x\_ j,x\_{j+1},\\ldots ,x\_ n)}{\\Delta x\_ j}\\\] | (3.75) 

This approximation is first-order accurate: reducing \\(\\Delta x\_ j\\) by a factor of 2 reduces the error in the gradient by a factor of 2.

A more accurate estimate can be computed using a central difference, which requires \\(2n\\) function evaluations:

| \\\[\\frac{\\partial J}{\\partial x\_ j} \\approx \\frac{J(x\_1,x\_2,\\ldots ,x\_ j+\\Delta x\_ j, x\_{j+1},\\ldots ,x\_ n)-J(x\_1,x\_2,\\ldots ,x\_ j-\\Delta x\_ j,x\_{j+1},\\ldots ,x\_ n)}{2\\Delta x\_ j}\\\] | (3.76) 

This approximation is second-order accurate: reducing \\(\\Delta x\_ j\\) by a factor of 2 reduces the error in the gradient by a factor of 4.

The Hessian matrix can also be estimated using finite differences. A second-order central approximation of the \\((i,j)\\) entry of the Hessian matrix is given by:

| \\\[\\frac{\\partial ^2 J}{\\partial x\_ i \\partial x\_ j} \\approx \\frac{J(x\_1,x\_2,\\ldots ,x\_ i+\\Delta x\_ i,\\ldots ,x\_ j+\\Delta x\_ j, x\_{j+1},\\ldots ,x\_ n)}{4\\Delta x\_ i\\Delta x\_ j} \\\\ + \\frac{J(x\_1,x\_2,\\ldots ,x\_ i-\\Delta x\_ i,\\ldots ,x\_ j-\\Delta x\_ j, x\_{j+1},\\ldots ,x\_ n)}{4\\Delta x\_ i\\Delta x\_ j} \\\\ - \\frac{J(x\_1,x\_2,\\ldots ,x\_ i-\\Delta x\_ i,\\ldots ,x\_ j+\\Delta x\_ j, x\_{j+1},\\ldots ,x\_ n)}{4\\Delta x\_ i\\Delta x\_ j} \\\\ - \\frac{J(x\_1,x\_2,\\ldots ,x\_ i+\\Delta x\_ i,\\ldots ,x\_ j-\\Delta x\_ j, x\_{j+1},\\ldots ,x\_ n)}{4\\Delta x\_ i\\Delta x\_ j}\\\] | (3.77) 

BackUnconstrained Gradient-Based Optimization Methods ContinueThe 1d Search