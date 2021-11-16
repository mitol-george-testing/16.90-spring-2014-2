---
content_type: page
parent_title: 1.2 Discretizing ODEs
parent_uid: f239c31a-53e6-28b3-a06a-8e6fff5ed57c
title: 1.2 Discretizing ODEs
uid: 0baef83e-dfb4-b312-66ed-4f9fe5c876ba
---

*   [<An Example of First Order ODE]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-an-example-of-first-order-ode)
*   [1.2.1First-Order ODEs]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes)
*   [1.2.2An Example of First Order ODE]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-an-example-of-first-order-ode)
*   [1.2.3Discretization]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-discretization)
*   [1.2.4The Forward Euler Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-the-forward-euler-method)
*   [1.2.5The Midpoint Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-the-midpoint-method)
*   [\>The Forward Euler Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-the-forward-euler-method)

1.2.3 Discretization
--------------------

[Measurable Outcome 1.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO15)

When you plot the solution in MATLAB®, you are likely creating two vectors: one corresponding to points in time \\(t=\[t\_0, t\_1, \\ldots ,t\_ N\]\\) and another corresponding to the solution \\(\\mathbf{u}(t)= \[u(t\_0),u(t\_1),\\ldots ,u(t\_ N)\]\\) at those points in time. This process of representing a continuous function by a finite set of numbers is referred to as discretization. The main idea is illustrated in Figure [1.1]({{< baseurl >}}/resources/discretization). Instead of representing the function continuously, we represent it as a finite set of ordered pairs \\((t\_ n, u(t\_ n))\\).

![This figure shows three line graphs that represent the behavior of velocity, Reynolds number, and drag coefficient as a function of time for an ice particle falling through the atmosphere. The simulation was performed using the forward Euler method with Δt=0.25sec.](BASEURL_PLACEHOLDER/resources/discretization)

**Figure 1.1**: Numerical solutions are represented as a finite set of ordered pairs (blue dots) representing the discretization of a continuous function.

When we solve mathematical problems on a computer, it will always be necessary to discretize them. For initial value problems, we will begin with the initial condition \\(u\_0\\) at time \\(t=0\\) and solve forward in time. First we select a time step \\({\\Delta t}>0\\) representing the length of the interval between any two adjacent time points \\(t\_ n\\) and \\(t\_{n+1}\\). Although it is not necessary to choose a constant \\({\\Delta t}\\) for the entire simulation, this is the approach we will take for this course. (You should be aware that state of the art numerical simulation codes adaptively select the time step, e.g., based on an estimate of the error.) Our numerical solution will then involve computing an approximation to the solution \\(u(t\_ n)\\) using information up to (and sometimes including, see implicit methods) time step \\(n\\).

BackAn Example of First Order ODE ContinueThe Forward Euler Method