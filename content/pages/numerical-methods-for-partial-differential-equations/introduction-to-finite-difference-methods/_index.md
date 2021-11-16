---
content_type: page
parent_title: 'Unit 2: Numerical Methods for Partial Differential Equations'
parent_uid: 125c58ac-6a34-5a7c-bba8-de2d3160cb8b
title: 2.3 Introduction to Finite Difference Methods
uid: 02467893-75dd-44cc-fcac-58f1a4ee9702
---

*   [<Linear Elasticity]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-linear-elasticity)
*   [2.3.1Finite Difference Approximations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods)
*   [2.3.2Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-methods)
*   [2.3.3Finite Difference Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-method-applied-to-1-d-convection)
*   [2.3.4Forward Time-Backward Space FTBS]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-forward-time-backward-space--ftbs-)
*   [\>Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-methods)

2.3.1 Finite Difference Approximations
--------------------------------------

[Measurable Outcome 2.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO23), [Measurable Outcome 2.6]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO26)

Recall how the multi-step methods we developed for ODEs are based on a truncated Taylor series approximation for \\(\\frac{\\partial U}{\\partial t}\\). Specifically, we can consider each multi-step method as computing \\(U\\) at discrete instances in time \\((t^0, t^1, \\ldots , t^ n, \\ldots )\\) where the derivative \\(\\left. \\frac{\\partial U}{\\partial t}\\right|\_ n = U\_ t^ n\\) is approximated using a combination of \\(\\left(U^{n+1}, U^ n, U^{n-1}, \\ldots \\right)\\).

Finite difference methods for PDEs are essentially built on the same idea, but approximating spatial derivatives instead of time derivatives. Namely, the solution \\(U\\) is approximated at discrete instances in space \\(\\left(x\_0, x\_1, \\ldots , x\_{i-1}, x\_ i, x\_{i+1}, \\ldots , x\_{N\_ x-1}, x\_{N\_ x}\\right)\\) where the spatial derivatives \\(\\left( \\left.\\frac{\\partial U}{\\partial x} \\right|\_ i = U\_{x\_ i}, \\left. \\frac{\\partial ^2 U}{\\partial x^2} \\right|\_ i = U\_{xx\_ i} \\right)\\) are approximated using a combination of \\((U\_ i, U\_{i \\pm 1}, U\_{i \\pm 2}, \\ldots )\\).

![The figure shows a line of discrete instances in space with the span between each instance labeled as Δr.](BASEURL_PLACEHOLDER/resources/onedfdmesh)

**Figure 2.8**: One-dimensional structured mesh for finite difference approximations.

In the following we derive a finite difference approximation of \\(\\frac{\\partial U}{\\partial x}\\) at node \\(x\_ i\\). For a differentiable function \\(U\\), the derivative at the point \\(x\_ i\\) is given by:

| \\\[\\left. \\frac{\\partial U}{\\partial x} \\right&#124;\_{x\_ i} = \\lim \_{\\Delta x \\to 0} \\frac{U(x\_ i+\\Delta x) - U(x\_ i - \\Delta x)}{2\\Delta x}.\\\] | (2.45) 

The finite difference approximation is obtained by eliminating the limiting process:

| \\\[{U\_ x}\_ i \\approx \\frac{U(x\_ i+\\Delta x) - U(x\_ i-\\Delta x)}{2 \\Delta x} = \\frac{U\_{i+1} - U\_{i-1}}{2 \\Delta x} \\equiv \\delta \_{2x} U\_ i.\\\] | (2.46) 

The finite difference operator \\(\\delta \_{2x}\\) is called a central difference operator. Finite difference approximations can also be one-sided. For example, a backward difference approximation is,

| \\\[\\left.\\frac{\\partial U}{\\partial x}\\right&#124;\_{i,j} \\approx \\delta \_{x}^{-} U\_{i,j} \\equiv \\frac{1}{{\\scriptstyle \\Delta } x}\\left(U\_{i,j} - U\_{i-1,j}\\right), \\label{equ:ux\_ backwarddiff}\\\] | (2.47) 

and a forward difference approximation is,

| \\\[\\left.\\frac{\\partial U}{\\partial x}\\right&#124;\_{i,j} \\approx \\delta \_{x}^{+} U\_{i,j} \\equiv \\frac{1}{{\\scriptstyle \\Delta } x}\\left(U\_{i+1,j} - U\_{i,j}\\right), \\label{equ:ux\_ forwarddiff}\\\] | (2.48) 

We can also derive finite difference approximations for higher-order derivatives. For example, consider the following definition for the second derivative,

| &nbsp; | \\(\\displaystyle \\frac{\\partial ^2 U}{\\partial x^2}(x)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\lim \_{{\\scriptstyle \\Delta } x\\rightarrow 0} \\frac{{\\partial U}/{\\partial x}(x+{\\scriptstyle \\Delta } x/2) - {\\partial U}/{\\partial x}(x-{\\scriptstyle \\Delta } x/2)}{{\\scriptstyle \\Delta } x}\\) | &nbsp; | (2.49) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\lim \_{{\\scriptstyle \\Delta } x\\rightarrow 0} \\frac{1}{{\\scriptstyle \\Delta } x}\\left\[ \\frac{U(x+{\\scriptstyle \\Delta } x)-U(x)}{{\\scriptstyle \\Delta } x} - \\frac{U(x)-U(x-{\\scriptstyle \\Delta } x)}{{\\scriptstyle \\Delta } x}\\right\]\\) | &nbsp; | (2.50) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\lim \_{{\\scriptstyle \\Delta } x\\rightarrow 0} \\frac{1}{{\\scriptstyle \\Delta } x^2}\\left\[ U(x+{\\scriptstyle \\Delta } x)-2U(x) + U(x-{\\scriptstyle \\Delta } x) \\right\].\\) | &nbsp; | (2.51) 

The finite difference approximation for the second order derivative is obtained eliminating the limiting process.

| \\\[\\left.\\frac{\\partial ^2 U}{\\partial x^2}\\right&#124;\_{i,j} \\approx \\delta \_{x}^2 U\_{i,j} \\equiv \\frac{1}{{\\scriptstyle \\Delta } x^2}\\left(U\_{i+1,j} - 2 U\_{i,j} + U\_{i-1,j}\\right). \\label{equ:uxx\_ centraldiff}\\\] | (2.52) 

Finite Difference Approximations in 2D
--------------------------------------

We can easily extend the concept of finite difference approximations to multiple spatial dimensions. In this case we represent the solution on a structured spatial mesh as shown in Figure [2.9]({{< baseurl >}}/resources/finitedifference_twod_mesh).

![The figure shows a grid with the first and second dimensions (perpendicular to each other), labeled similarly to Fig 2.8, with nodes at every intersection of the 2 dimensions.](BASEURL_PLACEHOLDER/resources/finitedifference_twod_mesh)

**Figure 2.9**: Two-dimensional structured mesh for finite difference approximations.

Using \\(U\_{i,j}\\) to denote the value of \\(U\\) at node \\((i,j)\\) our central derivative approximations for the first derivatives are:

| &nbsp; | \\(\\displaystyle \\left.\\dfrac {\\partial U}{\\partial x}\\right&#124;\_{i,j}\\) | \\(\\displaystyle \\approx\\) | \\(\\displaystyle \\frac{U\_{i+1,j} - U\_{i-1,j}}{2 \\Delta x} \\equiv \\delta \_{2x} U\_{i,j}.\\) | &nbsp; | (2.53) |
| &nbsp; | \\(\\displaystyle \\left.\\dfrac {\\partial U}{\\partial y}\\right&#124;\_{i,j}\\) | \\(\\displaystyle \\approx\\) | \\(\\displaystyle \\frac{U\_{i,j+1} - U\_{i,j-1}}{2 \\Delta y} \\equiv \\delta \_{2y} U\_{i,j}.\\) | &nbsp; | (2.54) 

In general, finite difference approximations will involve a set of points surrounding \\(U\_{i,j}\\).

BackLinear Elasticity ContinueFinite Difference Methods