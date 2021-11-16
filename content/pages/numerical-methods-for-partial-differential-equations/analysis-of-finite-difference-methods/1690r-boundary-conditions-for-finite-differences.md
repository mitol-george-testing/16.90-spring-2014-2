---
content_type: page
parent_title: 2.4 Analysis of Finite Difference Methods
parent_uid: c9ae23f7-07d4-0d5c-c85b-b19ebf476df0
title: 2.4 Analysis of Finite Difference Methods
uid: 7d8e6a54-9392-cde6-ff4d-914e606da194
---

*   [<General Finite Difference Approximations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-general-finite-difference-approximations)
*   [2.4.1Local Truncation Error for a Derivative Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods)
*   [2.4.2Truncation Error of Central Difference Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-of-central-difference-approximation)
*   [2.4.3Truncation Error for a PDE]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-for-a-pde)
*   [2.4.4Finite Difference Methods in Matrix Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-finite-difference-methods-in-matrix-form)
*   [2.4.5General Finite Difference Approximations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-general-finite-difference-approximations)
*   [2.4.6Boundary Conditions for Finite Differences]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-boundary-conditions-for-finite-differences)
*   [\>Introduction to Finite Volume Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods)

2.4.6 Boundary Conditions for Finite Differences
------------------------------------------------

[Measurable Outcome 2.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO23), [Measurable Outcome 2.8]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO28)

In this section, we discuss the implementation of finite difference methods at boundaries. This discussion is not meant to be comprehensive, as the issues are many and often subtle. In particular, we only focus on Dirichlet boundary conditions.

A Dirichlet boundary condition is one in which the state is specified at the boundary. For example, in a heat transfer problem, the temperature might be known at the boundary. Dirichlet boundary conditions can be implemented in a relatively straightforward manner. For example, suppose that we are solving a one-dimensional convection-diffusion problem and we want the value of \\(U\\) at \\(i=0\\), to be \\(U\_{inlet}\\),

| \\\[U\_0 = U\_{inlet}.\\\] | (2.87) 

To implement this, we fix \\(U\_0 = U\_{inlet}\\) and apply the finite difference discretization only over the interior of the computational domain accounting for the known value of \\(U\_0\\) at any place where the interior discretization depends on it. For example, at the first interior node (i.e. \\(i=1\\)), the central difference discretization of 1-D convection-diffusion gives,

| \\\[\\frac{{\\rm d}U\_1}{{\\rm d}t} + u\_{1}\\frac{U\_{2} - U\_0}{2{\\scriptstyle \\Delta } x} = \\mu \\frac{U\_2 - 2 U\_1 + U\_0}{{\\scriptstyle \\Delta } x^2}.\\\] | (2.88) 

Accounting for the known value of \\(U\_0\\), this becomes,

| \\\[\\frac{{\\rm d}U\_1}{{\\rm d}t} + u\_{1}\\frac{U\_{2} - U\_{inlet}}{2{\\scriptstyle \\Delta } x} = \\mu \\frac{U\_2 - 2 U\_1 + U\_{inlet}}{{\\scriptstyle \\Delta } x^2}. \\label{equ:dirichlet\_ example}\\\] | (2.89) 

In terms of the vector notation, when a Dirichlet boundary condition is applied we usually remove that state from the vector \\(U\\). So, in the situation where \\(U\_0\\) is known, the state vector is defined as,

| \\\[U = \\left( U\_{1}, U\_{2}, \\, \\ldots ,\\, U\_{i-1}, U\_{i}, U\_{i+1}, \\, \\ldots , \\, U\_{N\_ x-1}, U\_{N\_ x}\\right)^ T,\\\] | (2.90) 

The right-hand side \\(b\\) vector then will contain the contributions from the known boundary values. For example, by re-arranging Equation ([2.89](javascript: void(0))), the first row of \\(b\\) contains,

| \\\[b\_1 = u\_{2}\\frac{U\_{inlet}}{2{\\scriptstyle \\Delta } x} + \\mu \\frac{U\_{inlet}}{{\\scriptstyle \\Delta } x^2}.\\\] | (2.91) 

Since \\(U\_{inlet}\\) does not enter any of the other node's stencils, the remaining rows of \\(b\\) will be zero (unless they are altered by the other boundary).

Effect of boundary conditions on the number of degrees of freedom for the 1D Laplace equation
---------------------------------------------------------------------------------------------

The number of degrees of freedom in a set of equations is considered to be the number of unknowns. Consider the 1D Laplace equation defined on a finite domain \\(x \\in \[0, T\].\\)

| \\\[\\frac{\\partial ^2 u(x)}{\\partial x^2} = 0, \\quad u(0) = a\_1, u(T) = a\_2\\\] | (2.92) 

Suppose we discretize \\(x\\) into \\(N\\) unknowns \\((x\_1, \\ldots x\_ N)\\) and we use a second order central difference scheme to approximate the left side of the Laplace equation. The resulting linear equations become

| &nbsp; | \\(\\displaystyle \\frac{1}{(\\Delta x)^2} \\left\[ \\begin{array}{cccccc} (\\Delta x)^2 & 0 & 0 & 0 & \\ldots & 0 \\\\ 1 & -2 & 1 & 0 & \\ldots & 0 \\\\ 0 & 1 & -2 & 1 & \\ldots & 0 \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ 0 & \\ldots & 0 & 1 & -2 & 1 \\\\ 0 & \\ldots & 0 & 0 & 0 & (\\Delta x)^2 \\end{array} \\right\] \\left\[ \\begin{array}{c} u(x\_1) \\\\ u(x\_2) \\\\ \\vdots \\\\ u(x\_{N-1}) \\\\ u(x\_{N}) \\end{array}\\right\] = \\left\[ \\begin{array}{c} a\_1 \\\\ 0 \\\\ \\vdots \\\\ 0 \\\\ a\_2 \\end{array} \\right\]\\) | &nbsp; | (2.93) 

It appears that this equation has \\(N\\) unknowns and \\(N\\) degrees of freedom.

However if we rewrite the first two equations specified by this system:

| &nbsp; | \\(\\displaystyle u(x\_1)\\) | \\(\\displaystyle = a\_1\\) | &nbsp; | (2.94) |
| &nbsp; | \\(\\displaystyle u(x\_1) - 2u(x\_2) + u(x\_3)\\) | \\(\\displaystyle = 0\\) | &nbsp; | (2.95) 

We can now remove \\(x\_1\\) from this system by converting the second equation into

| \\\[-2 u(x\_2) + u(x\_3) = -a\_1\\\] | (2.96) 

We can perform the same trick for the last equation to obtain

| \\\[u(x\_{N-2}) - 2u(x\_{N-1}) = - a\_2\\\] | (2.97) 

Finally we obtain the system

| \\\[\\frac{1}{(\\Delta x^2)}\\left\[ \\begin{array}{cccccc} -2(\\Delta x^2) & \\Delta x^2 & 0 & \\ldots & \\ldots & 0 \\\\ 1 & -2 & 1 & 0 & \\ldots & 0 \\\\ 0 & 1 & -2 & 1 & \\ldots & 0 \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ 0 & \\ldots & 1 & -2 & 1 & 0 \\\\ 0 & \\ldots & \\ldots & 0 & \\Delta x^2 & -2\\Delta x^2 \\\\ \\end{array} \\right\] \\left\[ \\begin{array}{c} u(x\_2) \\\\ u(x\_3) \\\\ \\vdots \\\\ u(x\_{N-1}) \\end{array}\\right\]= \\left\[ \\begin{array}{c} -a\_1 \\\\ 0 \\\\ \\vdots \\\\ 0 \\\\ -a\_2 \\end{array} \\right\]\\\] | (2.98) 

This system has \\(N-2\\) degrees of freedom. Thus we see that the specification of the Dirichlet boundary conditions has _reduced_ the number of degrees of freedom of the system compared to the number of discretization points.

BackGeneral Finite Difference Approximations ContinueIntroduction to Finite Volume Methods