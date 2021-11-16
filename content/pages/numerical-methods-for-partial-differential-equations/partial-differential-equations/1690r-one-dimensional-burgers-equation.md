---
content_type: page
parent_title: 2.2 Partial Differential Equations
parent_uid: 735249e6-5cf9-7136-d3a6-4f4d3458178c
title: 2.2 Partial Differential Equations
uid: 53d47d94-d1a2-5853-95d6-3d7a71ad1144
---

*   [<Partial Differential Equations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations)
*   [2.2.1Conservation Laws in Integral and Differential Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations)
*   [2.2.2One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-one-dimensional-burgers-equation)
*   [2.2.3Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection)
*   [2.2.4Characteristics for One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-characteristics-for-one-dimensional-burgers-equation)
*   [2.2.5Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-diffusion)
*   [2.2.6Convection-Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection-diffusion)
*   [2.2.7Linear Elasticity]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-linear-elasticity)
*   [\>Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection)

2.2.2 One-Dimensional Burgers' Equation
---------------------------------------

[Measurable Outcome 2.1]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO21), [Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22) 

Burgers' equation is a fundamental partial differential equation from fluid mechanics. It occurs in various areas, such as modeling of gas dynamics and traffic flow. It is named for Johannes Martinus Burgers (1895-1981). The one-dimensional Burgers' equation is given in differential form as:

| \\\[\\frac{\\partial u}{\\partial t} + u \\frac{\\partial u}{\\partial x} = 0 \\label{equ:burgers}\\\] | (2.17) 

Which of the following is the correct mapping between the terms of the Burgers' equation and the terms of the canonical conservation equation?

Exercise 1

&nbsp; \\(U=u, \\vec{F}=u\\) &nbsp;

&nbsp; \\(U=u, \\vec{F}=u^2\\) &nbsp;

&nbsp; \\(U=\\frac{1}{2}u, \\vec{F}=u^2\\) &nbsp;

&nbsp; \\(U=u,\\vec{F}=\\frac{1}{2}u^2\\) &nbsp;

CheckShow Answer

Answer: This solution can be verified by plugging in \\(\\vec{F} =\\frac{1}{2} u^2\\) and noting that \\(\\frac{\\partial \\vec{f}}{\\partial x} = \\frac{\\partial \\vec{F}}{\\partial u}\\frac{\\partial u}{\\partial x}\\) and we arrive that the above differential form.

BackPartial Differential Equations ContinueConvection