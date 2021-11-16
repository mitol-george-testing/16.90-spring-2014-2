---
content_type: page
parent_title: 2.2 Partial Differential Equations
parent_uid: 735249e6-5cf9-7136-d3a6-4f4d3458178c
title: 2.2 Partial Differential Equations
uid: d923673e-05c6-3f48-9244-d3fc50c46901
---

*   [<Convection-Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection-diffusion)
*   [2.2.1Conservation Laws in Integral and Differential Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations)
*   [2.2.2One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-one-dimensional-burgers-equation)
*   [2.2.3Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection)
*   [2.2.4Characteristics for One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-characteristics-for-one-dimensional-burgers-equation)
*   [2.2.5Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-diffusion)
*   [2.2.6Convection-Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection-diffusion)
*   [2.2.7Linear Elasticity]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-linear-elasticity)
*   [\>Introduction to Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods)

2.2.7 Linear Elasticity
-----------------------

[Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22)

In addition to fluid dynamics and heat transfer, structural mechanics is a key field in aerospace engineering. In this class, we will utilize forms of the linear elasticity equations as examples. These equations are commonly derived through application of Newton's Law to an elastic solid. The resulting partial differential equations are frequently written in indicial notation as,

| \\\[\\rho \\dfrac {\\partial ^2 u\_ i}{\\partial t^2} = \\dfrac {\\partial \\sigma \_{ji}}{\\partial x\_ j} + f\_ i\\\] | (2.38) | \\\[\\epsilon \_{ij} = \\frac{1}{2}\\left(\\dfrac {\\partial u\_ i}{\\partial x\_ j} + \\dfrac {\\partial u\_ j}{\\partial x\_ i}\\right)\\\] | (2.39) | \\\[\\sigma \_{ij} = C\_{ijkl}\\epsilon \_{kl}\\\] | (2.40) 

where \\(\\rho\\) is the density of the material, \\(u\_ i(\\vec{x},t)\\) is the displacement in the \\(i-\\)th coordinate direction, \\(\\sigma \_{ij}\\) is the stress in the \\(i\\) direction acting on a plane with normal in the \\(j-\\)direction, \\(f\_ i\\) is the body force in the \\(i-\\)direction and \\(\\epsilon \_{ij}\\) is the strain. The stress and strains are related through the generalized Hooke's Law.

Hooke's Law for Isotropic Materials
-----------------------------------

For isotropic materials, i.e. materials in which the stress-strain relationship is the same independent of orientation of the material, Hooke's Law can be reduced to the following form,

| &nbsp; | \\(\\displaystyle \\left\[\\begin{array}{c} \\sigma \_{11} \\\\ \\sigma \_{22} \\\\ \\sigma \_{33} \\\\ \\sigma \_{23} \\\\ \\sigma \_{13} \\\\ \\sigma \_{12} \\end{array}\\right\] = \\left\[\\begin{array}{cccccc} \\lambda + 2\\mu & \\lambda & \\lambda & 0 & 0 & 0 \\\\ \\lambda & \\lambda + 2\\mu & \\lambda & 0 & 0 & 0 \\\\ \\lambda & \\lambda & \\lambda + 2\\mu & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 2\\mu & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 2\\mu & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 2\\mu \\end{array}\\right\] \\left\[\\begin{array}{c} \\epsilon \_{11} \\\\ \\epsilon \_{22} \\\\ \\epsilon \_{33} \\\\ \\epsilon \_{23} \\\\ \\epsilon \_{13} \\\\ \\epsilon \_{12} \\end{array}\\right\]\\) | &nbsp; | (2.41) 

The constants \\(\\lambda\\) and \\(\\mu\\) are often expressed in terms of the Young's Modulus \\((E)\\) and Poissons ration \\((\\nu )\\) as,

| \\\[\\lambda = \\frac{E\\nu }{(1+\\nu )(1-2\\nu )}\\\] | (2.42) | \\\[\\mu = \\frac{E}{2(1+\\nu )}\\\] | (2.43) 

This Hooke's Law relationship can also be written compactly using indicial notation as,

| &nbsp; | \\(\\displaystyle \\sigma \_{ij} = 2\\mu \\epsilon \_{ij} + \\delta \_{ij} \\lambda \\epsilon \_{kk}\\) | &nbsp; | (2.44) 

where \\(\\delta \_{ij}\\) is the Kronecker delta function.

BackConvection-Diffusion ContinueIntroduction to Finite Difference Methods