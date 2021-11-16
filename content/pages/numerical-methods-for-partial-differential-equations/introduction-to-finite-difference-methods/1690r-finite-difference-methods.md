---
content_type: page
parent_title: 2.3 Introduction to Finite Difference Methods
parent_uid: 02467893-75dd-44cc-fcac-58f1a4ee9702
title: 2.3 Introduction to Finite Difference Methods
uid: 2687d50f-29a8-875f-7b1d-d6bf668d5db7
---

*   [<Introduction to Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods)
*   [2.3.1Finite Difference Approximations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods)
*   [2.3.2Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-methods)
*   [2.3.3Finite Difference Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-method-applied-to-1-d-convection)
*   [2.3.4Forward Time-Backward Space FTBS]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-forward-time-backward-space--ftbs-)
*   [\>Finite Difference Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-method-applied-to-1-d-convection)

2.3.2 Finite Difference Methods
-------------------------------

To approximate the convection-diffusion equation we can combine various finite difference derivative approximations. For example, consider the one-dimensional convection-diffusion equation,

| &nbsp; | \\begin{equation} \\frac{\\partial U}{\\partial t} + u\\frac{\\partial U}{\\partial x} - \\mu\\frac{\\partial^2 U}{\\partial x^2} = 0 \\label{equ:condif1d\_pde} \\end{equation} | &nbsp; | (2.55) 

Approximating this using central differences for all derivatives, the convection-diffusion equation at node \\( i \\) can be approximated as,

| &nbsp; | \\begin{equation} \\frac{{\\rm d}U\_i}{{\\rm d}t} + u\_{i}\\delta\_{2x} U\_{i} - \\mu \\delta^2\_x U\_{i} = 0 \\label{equ:condif\_central} \\end{equation} | &nbsp; | (2.56) 

This is an ordinary differential equation for \\( U\_{i} \\) which is coupled to the nodal values at \\( U\_{i\\pm 1} \\). We refer to Equation [2.33](javascript: void(0)) as being semi-discrete, since we have discretized the PDE in space but not in time. To make this a fully discrete approximation, we need to discretize in time. To do this, we could apply any of the ODE integration methods that we discussed previously. For example, the simple forward Euler integration method would give,

| &nbsp; | \\begin{equation} \\frac{U\_i^{n+1}-U\_i^n}{\\Delta t} + u\_{i}^n\\delta\_{2x} U^n\_{i} = \\mu \\delta^2\_x U^n\_{i}. \\label{equ:condif\_ftcs} \\end{equation} | &nbsp; | (2.57) 

Using central difference operators for the spatial derivatives and forward Euler integration gives the method widely known as a Forward Time-Central Space (FTCS) approximation.

BackIntroduction to Finite Difference Methods ContinueFinite Difference Method Applied to 1-D Convection