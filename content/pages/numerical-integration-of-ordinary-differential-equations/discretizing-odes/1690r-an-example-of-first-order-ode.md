---
content_type: page
parent_title: 1.2 Discretizing ODEs
parent_uid: f239c31a-53e6-28b3-a06a-8e6fff5ed57c
title: 1.2 Discretizing ODEs
uid: 18e3e2fd-45b7-38b5-b9bb-4940200d150a
---

*   [<Discretizing ODEs]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes)
*   [1.2.1First-Order ODEs]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes)
*   [1.2.2An Example of First Order ODE]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-an-example-of-first-order-ode)
*   [1.2.3Discretization]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-discretization)
*   [1.2.4The Forward Euler Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-the-forward-euler-method)
*   [1.2.5The Midpoint Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-the-midpoint-method)
*   [\>Discretization]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-discretization)

1.2.2 An example of first order ODE
-----------------------------------

[Measurable Outcome 1.1]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO11), [Measurable Outcome 1.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO13), [Measurable Outcome 1.4]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO14)

Ordinary differential equations (ODEs) occur throughout science and engineering.

Free Fall Example
-----------------

A model for the velocity \\(u(t)\\) of a spherical object falling freely through the atmosphere can be derived by applying Newton's Law. Specifically,

| \\\[m\_ p u\_ t = m\_ p g - D(u) \\label{equ:freefall}\\\] | (1.4) 

where \\(m\_ p\\) is the mass of the particle, \\(g\\) is the gravity, \\(D\\) is the aerodynamic drag acting on the particle, and \\(u\_ t\\) denotes the derivative of \\(u(t)\\) with respect to time \\(t\\). For low speeds, this drag can be modeled as (recall Unified fluids),

| &nbsp; | \\(\\displaystyle D\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{1}{2}\\rho \_ g \\pi a^2 u^2 C\_ D(Re) \\label{equ:freefall\_ drag}\\) | &nbsp; | (1.5) |
| &nbsp; | \\(\\displaystyle Re\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{2 \\rho \_ g u a}{\\mu \_ g} \\label{equ:freefall\_ Re}\\) | &nbsp; | (1.6) |
| &nbsp; | \\(\\displaystyle C\_ D\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{24}{Re} + \\frac{6}{1 + \\sqrt {Re}} + 0.4 \\label{equ:freefall\_ CD}\\) | &nbsp; | (1.7) 

where \\(\\rho \_ g\\) and \\(\\mu \_ g\\) are the density and dynamic viscosity of the atmosphere, \\(a\\) is the sphere radius, \\(Re\\) is the Reynolds number for the sphere, and \\(C\_ D\\) is the drag coefficient. To complete the problem specification, an initial condition is required on the velocity. For example, at time \\(t=0\\), let \\(u(0) = u\_0\\). By solving Equation [1.4](javascript: void(0)) with this initial condition, the velocity at any time \\(u(t)\\) can be found.

General ODEs
------------

A general ODE is typically written in the form,

| \\\[u\_ t(t) = f(u(t),t), \\label{equ:ODE\_ nonlinear}\\\] | (1.8) 

where \\(f(u(t),t)\\) is the forcing function that results in the evolution of \\(u(t)\\) in time. When \\(f(u(t),t)\\) depends on \\(u(t)\\) in a nonlinear manner, then the ODE is called a nonlinear ODE. Note that in these notes, where clarity permits, we will omit the arguments of functions.

For the example defined by Equation [1.4](javascript: void(0)), the forcing function is,

| \\\[f(u,t) = g - \\frac{1}{m\_ p} D(u)\\\] | (1.9) 

From the definition of \\(D(u)\\), \\(f(u,t)\\) is nonlinear in \\(u\\). Note also that in this example, \\(f\\) does not depend on \\(t\\) directly, rather \\(f(u(t),t) = f(u(t))\\).

Linear ODEs
-----------

Although the use of numerical integration is most important for nonlinear ODE's (since analytic solutions rarely exist), the study of numerical methods applied to linear ODE's is often quite helpful in understanding the behavior for nonlinear problems. The general form for a single, linear ODE, is

| \\\[u\_ t = \\lambda (t) u(t) + g(t), \\label{equ:ODE\_ linear}\\\] | (1.10) 

where \\(\\lambda (t)\\) is independent of \\(u\\). When \\(\\lambda (t)\\) is a constant, the ODE is referred to as a linear ODE with constant coefficients.

In many situations, the linear ODE is derived by linearizing a nonlinear ODE about a constant state. Specifically, define the dependent state \\(u(t)\\) as a sum of \\(u\_0\\) and a perturbation, \\(\\tilde{u}(t)\\),

| \\\[u(t) = u\_0 + \\tilde{u}(t). \\label{equ:perturbation}\\\] | (1.11) 

A linearized equation for the evolution of \\(\\tilde{u}(t)\\) can be derived by substitution of this into Equation [1.8](javascript: void(0)):

| &nbsp; | \\(\\displaystyle u\_ t\\) | \\(\\displaystyle =\\) | \\(\\displaystyle f(u(t),t),\\) | &nbsp; | (1.12) |
| &nbsp; | \\(\\displaystyle \\tilde{u}\_ t\\) | \\(\\displaystyle =\\) | \\(\\displaystyle f(u\_0 + \\tilde{u}(t),t)\\) | &nbsp; | (1.13) |
| &nbsp; | \\(\\displaystyle \\tilde{u}\_ t\\) | \\(\\displaystyle =\\) | \\(\\displaystyle f(u\_0, 0) + \\left.\\frac{\\partial f}{\\partial u}\\right&#124;\_{u\_0,0}\\tilde{u}(t) + \\left.\\frac{\\partial f}{\\partial t}\\right&#124;\_{u\_0,0}t + O(t^2, \\tilde{u} t, \\tilde{u}^2).\\) | &nbsp; | (1.14) 

Note that the last equation is obtained using [Taylor series](http://crosslinks.mit.edu/topic/taylor-series/). Thus, when \\(t\\) and \\(\\tilde{u}\\) are small, the perturbation satisfies the linear equation,

| \\\[\\tilde{u}\_ t \\approx f(u\_0, 0) + \\left.\\frac{\\partial f}{\\partial u}\\right&#124;\_{u\_0,0}\\tilde{u}(t) + \\left.\\frac{\\partial f}{\\partial t}\\right&#124;\_{u\_0,0}t \\label{equ:ODE\_ linearized}\\\] | (1.15) 

Comparing Equation [1.10](javascript: void(0)) to [1.15](javascript: void(0)), we see that in this example,

| &nbsp; | \\(\\displaystyle \\lambda (t)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\left.\\frac{\\partial f}{\\partial u}\\right&#124;\_{u\_0,0},\\) | &nbsp; | (1.16) |
| &nbsp; | \\(\\displaystyle g(t)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle f(u\_0, 0) + \\left.\\frac{\\partial f}{\\partial t}\\right&#124;\_{u\_0,0}t\\) | &nbsp; | (1.17) 

For the falling sphere problem, a linear ODE can be derived by linearizing about the initial velocity \\(u\_0\\). As shown above, this requires the calculation of \\({\\partial f}/{\\partial u}\\) and \\({\\partial f}/{\\partial t}\\). For the sphere,

| \\\[\\frac{\\partial f}{\\partial u} = \\frac{\\partial }{\\partial u}\\left\[ g - \\frac{1}{m\_ p} D(u(t))\\right\] = -\\frac{1}{m\_ p}\\frac{\\partial D}{\\partial u}\\\] | (1.18) 

The value of \\({\\partial D}/{\\partial u}\\) is

| &nbsp; | \\(\\displaystyle \\frac{\\partial D}{\\partial u}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{\\partial }{\\partial u}\\left\[ \\frac{1}{2}\\rho \_ g \\pi a^2 u^2 C\_ D(Re) \\right\],\\) | &nbsp; | (1.19) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\rho \_ g \\pi a^2 u C\_ D(Re) + \\frac{1}{2}\\rho \_ g \\pi a^2 u^2 \\frac{\\partial C\_ D}{\\partial Re}\\frac{\\partial Re}{\\partial u},\\) | &nbsp; | (1.20) 

and \\({\\partial C\_ D}/{\\partial Re}\\) and \\({\\partial Re}/{\\partial u}\\) can be found from their definitions. Also, since \\(f\\) does not directly depend on \\(t\\) for this problem, \\({\\partial f}/{\\partial t} = 0.\\)

BackDiscretizing ODEs ContinueDiscretization