---
content_type: page
parent_title: 2.4 Analysis of Finite Difference Methods
parent_uid: c9ae23f7-07d4-0d5c-c85b-b19ebf476df0
title: 2.4 Analysis of Finite Difference Methods
uid: 404d1192-4d4a-07bb-c158-0c3605807e8e
---

*   [<Truncation Error for a PDE]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-for-a-pde)
*   [2.4.1Local Truncation Error for a Derivative Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods)
*   [2.4.2Truncation Error of Central Difference Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-of-central-difference-approximation)
*   [2.4.3Truncation Error for a PDE]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-for-a-pde)
*   [2.4.4Finite Difference Methods in Matrix Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-finite-difference-methods-in-matrix-form)
*   [2.4.5General Finite Difference Approximations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-general-finite-difference-approximations)
*   [2.4.6Boundary Conditions for Finite Differences]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-boundary-conditions-for-finite-differences)
*   [\>General Finite Difference Approximations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-general-finite-difference-approximations)

2.4.4 Finite Difference Methods in Matrix Form
----------------------------------------------

[Measurable Outcome 2.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO23), [Measurable Outcome 2.8]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO28)

Consider the one-dimensional convection-diffusion equation,

| &nbsp; | \\(\\displaystyle \\dfrac {\\partial U}{\\partial t} + u \\dfrac {\\partial U}{\\partial x} -\\mu \\dfrac {\\partial ^2 U}{\\partial x^2}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0.\\) | &nbsp; | (2.73) 

Approximating the spatial derivative using the central difference operators gives the following approximation at node \\(i\\),

| &nbsp; | \\(\\displaystyle \\dfrac {d U\_ i}{d t} + u\_ i \\delta \_{2x} U\_ i - \\mu \\delta \_ x^2 U\_ i\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0\\) | &nbsp; | (2.74) 

Assembling all of the nodal states into a single vector

| &nbsp; | \\(\\displaystyle U = \\left( U\_0,\\, U\_1,\\, \\ldots ,\\, U\_{i-1},\\, U\_ i,\\, U\_{i+1},\\, \\ldots ,\\, U\_{N\_ x-1},\\, U\_{N\_ x}\\right)^ T,\\) | &nbsp; | (2.75) 

gives a system of coupled ODEs of the form:

| &nbsp; | \\(\\displaystyle \\dfrac {d U}{d t}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle A U + b \\label{equ:linSys}\\) | &nbsp; | (2.76) 

where \\(b\\) will contain the boundary condition related data. The matrix \\(A\\) has the form:

| &nbsp; | \\(\\displaystyle A\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\left\[\\begin{array}{cccc} A\_{0,0} & A\_{0,1} & \\ldots & A\_{0,N\_ x} \\\\ A\_{1,0} & A\_{1,1} & \\ldots & A\_{1,N\_ x} \\\\ \\vdots & \\vdots & \\ddots & \\vdots \\\\ A\_{N\_ x,0} & A\_{N\_ x,1} & \\ldots & A\_{N\_ x,N\_ x} \\end{array} \\right\].\\) | &nbsp; | (2.77) 

Note that row \\(i\\) of this matrix contains the coefficients of the nodal values for the ODE governing node \\(i\\). Except for rows requiring boundary condition data, the values of \\(A\_{i,j}\\) are related to the coefficients \\(\\alpha \_ j\\) of the finite difference approximation. Specifically, for our central difference approximation

| &nbsp; | \\(\\displaystyle A\_{i,i-1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{u\_ i}{2 \\Delta x} + \\frac{\\mu }{\\Delta x^2},\\) | &nbsp; | (2.78) |
| &nbsp; | \\(\\displaystyle A\_{i,i}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle - 2\\frac{\\mu }{\\Delta x^2},\\) | &nbsp; | (2.79) |
| &nbsp; | \\(\\displaystyle A\_{i,i+1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle -\\frac{u\_ i}{2 \\Delta x} + \\frac{\\mu }{\\Delta x^2},\\) | &nbsp; | (2.80) 

and all other entries of row \\(i\\) are zero. In general, the number of non-zero entries of row \\(i\\) will correspond to the size of the stencil of the finite difference approximations used. We refer to Equation [2.76](javascript: void(0)) as being semi-discrete, since we have discretized the PDE in space but not in time. To make this a fully discrete approximation, we can apply any of the ODE integration methods that we discussed previously.

**Implementation Notes** When explicit methods are used to represent a FD method, then the \\(A\\) matrix does not need to be directly formed. Implementing a finite difference approximation at each node will suffice as we will only be interested in _matrix-vector multiplication_, i.e. we only need to _apply_ \\(A\\).

On the other hand, implicit methods require the solution of a linear system. The solutions methods often require the representation of \\(A\\) as a matrix, and thus it must be constructed.

BackTruncation Error for a PDE ContinueGeneral Finite Difference Approximations