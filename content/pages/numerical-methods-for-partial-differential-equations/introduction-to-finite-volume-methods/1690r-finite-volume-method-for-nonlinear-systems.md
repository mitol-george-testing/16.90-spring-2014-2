---
content_type: page
parent_title: 2.5 Introduction to Finite Volume Methods
parent_uid: 3d8df8b8-2291-7094-b5a6-9893808a75cc
title: 2.5 Introduction to Finite Volume Methods
uid: eaeacad2-dafd-9383-3c0e-0227dade769c
---

*   [<Finite Volume Method for 2-D Convection on a Rectangular Mesh]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-2-d-convection-on-a-rectangular-mesh)
*   [2.5.1Finite Volume Method in 1-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods)
*   [2.5.2Finite Volume Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-applied-to-1-d-convection)
*   [2.5.3Finite Volume Method in 2-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-in-2-d)
*   [2.5.4Finite Volume Method for 2-D Convection on a Rectangular Mesh]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-2-d-convection-on-a-rectangular-mesh)
*   [2.5.5Finite Volume Method for Nonlinear Systems]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-nonlinear-systems)
*   [\>Upwinding and the CFL Condition]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/upwinding-and-the-cfl-condition)

2.5.5 Finite Volume Method for Nonlinear Systems
------------------------------------------------

[Measurable Outcome 2.1]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO21), [Measurable Outcome 2.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO23), [Measurable Outcome 2.4]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO24)

The basic finite volume approach can be extended to nonlinear systems of equations such as the Euler equations. The main issue in this extension is how to calculate an upwind flux when there is a system of equations. In one dimension, the basic finite volume discretization remains the same as given by Equation [2.108](javascript: void(0)),

| \\\[\\Delta x\_ i \\frac{U\_ i^{n+1} - U\_ i^ n}{{\\Delta t}} + F\_{i+\\frac{1}{2}}^{n} - F\_{i-\\frac{1}{2}}^ n = 0.\\\] | (2.117) 

The flux, however, must upwind (to some degree) all of the states in the equation. One relatively simple way in which this can be done is using what is known as the local Lax-Friedrichs flux. In this case, the flux is given by,

| \\\[F\_{i+\\frac{1}{2}}(U\_ i, U\_{i+1}) = \\frac{1}{2}\\left\[F(U\_{i+1}) + F(U\_{i})\\right\] - \\frac{1}{2}s\_{\\max }\\left(U\_{i+1} - U\_{i}\\right), \\label{equ:upwindflux\_ laxfriedrichs}\\\] | (2.118) 

where \\(s\_{\\max }\\) is the maximum speed of propagation of any small disturbance for either state \\(U\_ i\\) or \\(U\_{i+1}\\).

Lax-Friedrichs Flux for 1-D Euler Equations
-------------------------------------------

For the one-dimensional Euler equations, there are three equations which are approximated, i.e. conservation of mass, conservation of \\(x\\)-momentum, and conservation of energy. A small perturbation analysis can be performed which shows that the three speeds of propagation for this set of equations are \\(u\\), \\(u-a\\), and \\(u+a\\) where \\(u\\) is the flow velocity and \\(a\\) is the speed of sound. Thus, the maximum speed will always be \\(|u| + a\\) and the corresponding value of \\(s\_{\\max }\\) for the Lax-Friedrichs flux is,

| \\\[s\_{\\max } = \\max \\left(&#124;u&#124;\_{i} + a\_{i}, \\, &#124;u&#124;\_{i+1} + a\_{i+1}\\right).\\\] | (2.119) 

BackFinite Volume Method for 2-D Convection on a Rectangular Mesh ContinueUpwinding and the CFL Condition