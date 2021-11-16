---
content_type: page
parent_title: 1.2 Discretizing ODEs
parent_uid: f239c31a-53e6-28b3-a06a-8e6fff5ed57c
title: 1.2 Discretizing ODEs
uid: 9b1b577d-12e2-e60d-75d3-f8fb6ed609d5
---

*   [<Discretization]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-discretization)
*   [1.2.1First-Order ODEs]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes)
*   [1.2.2An Example of First Order ODE]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-an-example-of-first-order-ode)
*   [1.2.3Discretization]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-discretization)
*   [1.2.4The Forward Euler Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-the-forward-euler-method)
*   [1.2.5The Midpoint Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-the-midpoint-method)
*   [\>The Midpoint Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-the-midpoint-method)

1.2.4 The Forward Euler Method
------------------------------

[Measurable Outcome 1.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO15), [Measurable Outcome 1.6]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO16)

We now consider our first numerical method for ODE integration, the forward Euler method. The general problem we wish to solve is to approximate the solution \\(u(t)\\) for Equation [1.8](javascript: void(0)) with an appropriate initial condition, \\(u(0) = u\_0\\). Usually, we are interested in approximating this solution over some range of \\(t\\), say from \\(t = 0\\) to \\(t = T\\). Or, we may not know a precise final time but wish to integrate forward in time until an event occurs (e.g. the problem reaches a steady state). In either case, the basic philosophy of numerical integration using finite difference methods is to start from a known initial state, \\(u(0)\\), and somehow approximate the solution a small time forward, \\(u({\\Delta t})\\) where \\({\\Delta t}\\) is a small time increment. Then, we repeat this process and move forward to the next time to find, \\(u(2{\\Delta t})\\), and so on. Initially, we will consider the situation in which \\({\\Delta t}\\) is fixed for the entire integration from \\(t=0\\) to \\(T\\). However, the best methods for solving ODE's tend to be adaptive methods in which \\({\\Delta t}\\) is adjusted depending on the current approximation.

Before moving on to the specific form of the forward Euler method, let's put some notations in place. Superscripts will be used to indicate a particular iteration, that is \\(t^ n\\) denotes the time at iteration \\(n\\). Thus, assuming constant \\({\\Delta t}\\),

| \\\[t^ n = n{\\Delta t}.\\\] | (1.21) 

The approximation from the numerical integration will be defined as \\(v\\). Thus, using the superscript notation,

| \\\[v^ n = \\mbox{the approximation of } u(t^ n).\\\] | (1.22) 

Now, let's derive the forward Euler method. There are several ways to motivate the forward Euler method. We will start with an approach based on Taylor series. Specifically, the [Taylor expansion](http://crosslinks.mit.edu/topic/taylor-series/) of \\(u(t^{n+1})\\) about \\(t^ n\\) is,

| \\\[u(t^{n+1}) = u(t^ n) + {\\Delta t}u\_ t(t^ n) + \\frac{1}{2}{\\Delta t}^2 u\_{tt}(t^ n) + O({\\Delta t}^3).\\\] | (1.23) 

Using only the first two terms in this expansion,

| \\\[u(t^{n+1}) \\approx u(t^ n) + {\\Delta t}u\_ t(t^ n).\\\] | (1.24) 

Finally, the term \\(u\_ t(t^ n)\\) is in fact just \\(f(u(t^ n),t^ n)\\) since the governing equation is Equation [1.8](javascript: void(0)). Thus,

| \\\[u(t^{n+1}) \\approx u(t^ n) + {\\Delta t}f(u(t^ n),t^ n). \\label{equ:fe\_ approx}\\\] | (1.25) 

Since we do not know \\(u(t^ n)\\), we will instead use the approximation from the previous timestep, \\(v^ n\\). Thus, the forward Euler algorithm is,

| \\\[v^{n+1} = v^ n + {\\Delta t}f(v^ n,t^ n) \\qquad \\mbox{for} \\qquad n \\geq 0, \\label{equ:fe}\\\] | (1.26) 

and \\(v^0 = u(0)\\).

Falling Ice Problem
-------------------

Now, let's apply the forward Euler method to solving the falling sphere problem. Suppose the sphere is actually a small particle of ice falling in the atmosphere at an altitude of approximately 3000 meters. Specifically, let's assume the radius of the particle is \\(a = 0.01 m\\). Then, since the density of ice is approximately \\(\\rho \_ p = 917 \\, kg/m^3\\), the mass of the particle can be calculated from,

| \\\[m\_ p = \\rho \_ p \\mbox{Volume}\_ p = \\rho \_ p \\frac{4}{3}\\pi a^3 = 0.0038\\, kg\\\] | (1.27) 

At that altitude, the properties of the atmosphere are:

| &nbsp; | \\(\\displaystyle \\rho \_ g\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0.9\\, kg/m^3\\) | &nbsp; | (1.28) |
| &nbsp; | \\(\\displaystyle \\mu \_ g\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 1.69 E{-5}\\, kg/(m\\, sec)\\) | &nbsp; | (1.29) |
| &nbsp; | \\(\\displaystyle g\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 9.8 m/sec^2\\) | &nbsp; | (1.30) 

We expect the particle to accelerate until it reaches its terminal velocity which will occur when the drag force is equal to the gravitational force. But, a priori, we do not know how long that will take (in class, we will discuss some ways to make this estimate). For now, let's set \\(T= 25\\, sec\\) and use a timestep of \\({\\Delta t}= 0.25\\, sec\\). The results are shown in Figure [1.2]({{< baseurl >}}/resources/ice_fe).

![This figure shows three bar graphs that represent the behavior of velocity, Reynolds number, and drag coefficient as a function of time for an ice particle falling through the atmosphere. This simulation was performed using the forward Euler method with Δt=0.25sec.](BASEURL_PLACEHOLDER/resources/ice_fe)

**Figure 1.2**: Behavior of velocity, Reynolds number, and drag coefficient as a function of time for an ice particle falling through the atmosphere. Simulation performed using the forward Euler method with \\({\\Delta t}= 0.25\\, sec\\).

BackDiscretization ContinueThe Midpoint Method