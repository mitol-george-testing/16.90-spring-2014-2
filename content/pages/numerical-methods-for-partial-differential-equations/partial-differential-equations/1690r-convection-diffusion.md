---
content_type: page
parent_title: 2.2 Partial Differential Equations
parent_uid: 735249e6-5cf9-7136-d3a6-4f4d3458178c
title: 2.2 Partial Differential Equations
uid: e6408661-a4be-8cfb-3204-ee1581c8dff1
---

*   [<Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-diffusion)
*   [2.2.1Conservation Laws in Integral and Differential Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations)
*   [2.2.2One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-one-dimensional-burgers-equation)
*   [2.2.3Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection)
*   [2.2.4Characteristics for One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-characteristics-for-one-dimensional-burgers-equation)
*   [2.2.5Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-diffusion)
*   [2.2.6Convection-Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection-diffusion)
*   [2.2.7Linear Elasticity]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-linear-elasticity)
*   [\>Linear Elasticity]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-linear-elasticity)

2.2.6 Convection-Diffusion
--------------------------

[Measurable Outcome 2.1]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO21), [Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22), [Measurable Outcome 2.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO25)

In practice, both convection and diffusion are important phenomenon governing fluid dynamics. While convection may be the dominant transport mechanism in most of a flow, accounting for diffusion near solid boundaries may be essential for accurately computing engineering quantities such as drag or heat transfer. The convection-diffusion equation is derived from a general conservation law including both convective and diffusive fluxes. In differential form, the convection-diffusion equation is

| \\\[\\dfrac {\\partial U}{\\partial t} + \\vec{v} \\cdot \\nabla U - \\nabla \\cdot ( \\mu \\nabla U ) = S.\\\] | (2.36) 

The convection-diffusion equation arises in many engineering applications ranging from heat transfer to statistical mechanics (and even in finance!). Solutions of the convection-diffusion equation exhibit behavior which is the combined effect of both convection and diffusion. A key question which naturally arises is how significant are the relative effects of convection and diffusion. This is governed by the non-dimensional Peclet number (in aerodynamics applications, the Reynolds number is equivalent).

| \\\[Pe = \\frac{&#124;\\vec{v}&#124; L}{\\mu }\\\] | (2.37) 

where \\(L\\) is a characteristic length scale for the problem of interest. When \\(Pe \\ll 1\\) diffusion effects are dominant, and convection plays a relatively small role. On the other hand, when \\(Pe \\gg 1\\) convection is the dominant transport mechanism. Figures [2.5]({{< baseurl >}}/resources/convdiffpe10), [2.6]({{< baseurl >}}/resources/convdiffpe100), [2.7]({{< baseurl >}}/resources/convdiffpe1000) show solutions for the one-dimensional convection-diffusion problem with Peclet numbers \\(10, 100\\) and \\(1000\\) (\\(\\vec{v}=1\\) is fixed). As the Peclet number increases the solution of the convection-diffusion problem approaches that of the pure convection problem.

![The graph shows the peaks (t=0, t=1) from the convection-diffusion equation at Pe=10.](BASEURL_PLACEHOLDER/resources/convdiffpe10)

**Figure 2.5**: One-dimensional convection-diffusion problem, \\(Pe=10\\)

![The graph shows the peaks (t=0, t=1) from the convection-diffusion equation at Pe=100.](BASEURL_PLACEHOLDER/resources/convdiffpe100)

**Figure 2.6**: One-dimensional convection-diffusion problem, \\(Pe=100\\)

![The graph shows the peaks (t=0, t=1) from the convection-diffusion equation at Pe=1000.](BASEURL_PLACEHOLDER/resources/convdiffpe1000)

**Figure 2.7**: One-dimensional convection-diffusion problem, \\(Pe=1000\\)

BackDiffusion ContinueLinear Elasticity