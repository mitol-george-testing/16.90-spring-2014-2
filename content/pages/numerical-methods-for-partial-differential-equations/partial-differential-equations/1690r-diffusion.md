---
content_type: page
parent_title: 2.2 Partial Differential Equations
parent_uid: 735249e6-5cf9-7136-d3a6-4f4d3458178c
title: 2.2 Partial Differential Equations
uid: 91200789-ca43-fa38-473a-bc690667c305
---

*   [<Characteristics for One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-characteristics-for-one-dimensional-burgers-equation)
*   [2.2.1Conservation Laws in Integral and Differential Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations)
*   [2.2.2One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-one-dimensional-burgers-equation)
*   [2.2.3Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection)
*   [2.2.4Characteristics for One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-characteristics-for-one-dimensional-burgers-equation)
*   [2.2.5Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-diffusion)
*   [2.2.6Convection-Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection-diffusion)
*   [2.2.7Linear Elasticity]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-linear-elasticity)
*   [\>Convection-Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection-diffusion)

2.2.5 Diffusion
---------------

[Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22), [Measurable Outcome 2.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO25)

In many engineering applications the dominant physical transport phenomenon is modeled as [**diffusion**](http://en.wikipedia.org/wiki/Diffusion). A distinguishing feature of diffusion is that it results in mixing or mass transport, without requiring bulk motion. Thus, diffusion should not be confused with convection, which is a transport mechanism that utilize bulk motion to move particles from one place to another. In Latin, "diffundere" means "to spread out". In 1831, Thomas Graham studied diffusion in gases, and the main phenomenon was described by him:

"...gases of different nature, when brought into contact, do not arrange themselves according to their density, the heaviest undermost, and the lighter uppermost, but they spontaneously diffuse, mutually and equally, through each other, and so remain in the intimate state of mixture for any length of time."

Heat conduction is another example of diffusion, the diffusion of thermal energy. This section presents the conservation law for diffusion in differential form and discuss the behavior of problems modeled with diffusion. Diffusion is characterized by a flux,\\(\\vec{F}\\) , of the form:

| &nbsp; | \\(\\displaystyle \\vec{F} = -\\mu \\nabla U,\\) | &nbsp; | (2.32) 

where \\(\\mu\\) is the diffusion coefficient and \\(U\\) is the state. The differential form of the conservation law for the diffusion is,

| \\\[\\dfrac {\\partial U}{\\partial t} - \\nabla \\cdot (\\mu \\nabla U) = S \\label{equ:diffconserv}\\\] | (2.33) 

Equation [2.33](javascript: void(0)) is a second-order partial differential equation often called the diffusion equation or heat equation. Partial differential equations of this form arise in many applications including molecular diffusion and heat conduction.

One-dimensional Diffusion
-------------------------

We now illustrate the behavior of the diffusion equation considering a simple one-dimensional model problem. Consider the one-dimensional diffusion equation with constant \\(\\mu\\). The diffusion equation simplifies to

| \\\[\\dfrac {\\partial U}{\\partial t} - \\mu \\dfrac {\\partial ^2 U}{\\partial x^2} = 0 \\label{equ:oneddiff}\\\] | (2.34) 

Figure [2.3]({{< baseurl >}}/resources/oneddiff) shows the initial condition

| \\\[U\_0(x) = 0.75 e^{-(\\frac{x-0.5}{0.1})^2},\\\] | (2.35) 

as well as the solution after a short time \\(t=0.05\\). The behavior of the diffusion equation is markedly different from what we have seen for the convection equation. The effect of the diffusion equation is to "smooth" out the conserved state in regions of steep gradients.

![The graph shows the peaks from a diffusion equation considering a simple one-dimensional model problem at two time points.](BASEURL_PLACEHOLDER/resources/oneddiff)

**Figure 2.3**: One-dimensional diffusion problem, \\(\\mu =1\\)

Unlike in the case of convection, (where the domain of dependence is along characteristics), the solution at any point \\((\\vec{x},t)\\) for the diffusion equation depends on the solution everywhere else in the domain. Thus the domain of dependence at any point \\((\\vec{x}, t)\\) is the entire domain at all previous time.

![The graph shows another diffusion equation considering a simple one-dimensional model problem at four time points.](BASEURL_PLACEHOLDER/resources/diff2)

**Figure 2.4**: Another one-dimensional diffusion problem

BackCharacteristics for One-Dimensional Burgers Equation ContinueConvection-Diffusion