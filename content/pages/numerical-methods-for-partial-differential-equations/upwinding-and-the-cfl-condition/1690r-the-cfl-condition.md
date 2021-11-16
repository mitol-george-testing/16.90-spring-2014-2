---
content_type: page
parent_title: 2.6 Upwinding and the CFL Condition
parent_uid: ce70b6b2-dea9-62c9-1d8e-4789958e4499
title: 2.6 Upwinding and the CFL Condition
uid: cf738358-ae33-664a-5d71-baadd24f92cb
---

*   [<Upwinding and the CFL Condition]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/upwinding-and-the-cfl-condition)
*   [2.6.1Upwinding]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/upwinding-and-the-cfl-condition)
*   [2.6.2The CFL Condition]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/upwinding-and-the-cfl-condition/1690r-the-cfl-condition)
*   [\>Eigenvalue Stability of Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods)

2.6.2 The CFL Condition
-----------------------

[Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22), [Measurable Outcome 2.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO25), [Measurable Outcome 2.6]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO26), [Measurable Outcome 2.7]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO27)

Recall from [2.2.3]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection) that the domain of dependence for the convection equation at \\((x,t)\\) is the characteristic \\(x(s<t)\\). We can also consider the numerical domain of dependence of the solution at \\((x\_ i, t^ n)\\). Figure [2.18]({{< baseurl >}}/resources/ftbsdomdep) shows the numerical domain of dependence of the FTBS method. Note that the numerical domain of dependence at \\(n-2\\) includes the nodes \\(i-2, i-1\\), and \\(i\\). \\((i-2,n-2)\\) and (\\(i-1,n-2\\)) are in the domain of dependence of \\((i,n)\\) because these values are required in the calculation of \\(U\_{i-1}^{n-1}\\), which in turn is required to calculate \\(U\_{i}^ n\\). Similarly, \\((i-1,n-2)\\) and \\((i,n-2)\\) are in the domain of dependence of \\((i,n)\\) because they are required in the calculation of \\(U\_{i}^{n-1}\\).

![This graph has points at the x- and y-axis intersections, with a triangular highlighted area of six points representing a numerical domain of dependence.](BASEURL_PLACEHOLDER/resources/ftbsdomdep)

**Figure 2.18**: Numerical domain of dependence for first order upwind scheme.

We now define two terms:

**CFL condition:** The discretization of a PDE satisfies the CFL condition if the numerical domain of dependence includes the physical domain of dependence.

**CFL Theorem:** The CFL condition is a necessary condition for the discretization of a time-dependent PDE to be convergent (i.e. in the limit as \\(\\Delta t \\to 0\\)). Courant, Friedrichs, and Levy are the authors who first described this requirement in 1928 (well before the first computer!)

In Figures [2.19]({{< baseurl >}}/resources/cfl_stable) and [2.20]({{< baseurl >}}/resources/cfl_unstable), the CFL conditions are shown graphically for the one-dimensional convection equation discretized using the first-order upwind scheme.

![The graph shows a case where the CFL condition has been satisfied, which shows the numerical domain of dependence includes the physical domain of dependence.](BASEURL_PLACEHOLDER/resources/cfl_stable)

**Figure 2.19**: CFL condition satisfied

![This graph shows a case where the CFL condition has not been satisfied and the physical domain of dependence is not included within the numerical domain of dependence.](BASEURL_PLACEHOLDER/resources/cfl_unstable)

**Figure 2.20**: CFL condition not satisfied

For scheme, the CFL condition requires that

| \\\[CFL \\equiv \\frac{&#124;u&#124;{\\Delta t}}{\\Delta x} \\leq 1\\\] | (2.123) 

If this condition is not satisfied, then the characteristic will be outside of the numerical domain of dependence and the numerical solution cannot possibly converge to the exact solution if the same ration of \\({\\Delta t}/\\Delta x\\) is maintained as \\({\\Delta t}\\to 0\\), since the numerical method will not have the proper domain of dependence in that limit. The non-dimensional number \\(\\frac{|u|{\\Delta t}}{\\Delta x}\\) is called the **CFL Number** or just the **CFL**. In general, the CFL condition for explicit finite difference methods for convection will require that the CFL number be bounded by a constant which will depend upon the particular numerical scheme (for FTBS, the constant is \\(1\\)).

Exercise
--------

Suppose we wish to solve the 1-D convection equation with velocity \\(u=2\\) on a mesh with \\(\\Delta x = 0.1\\) using the FTBS method. What is the largest possible time step for which the scheme satisfies the CFL condition?

Exercise 1

&nbsp; \\({\\Delta t}=5\\) &nbsp;

&nbsp; \\({\\Delta t}=1\\) &nbsp;

&nbsp; \\({\\Delta t}=0.01\\) &nbsp;

&nbsp; \\({\\Delta t}=0.05\\) &nbsp;

CheckShow Answer

Answer:

We can solve for the maximum \\(\\Delta t\\) as \\(\\Delta x/ |u| = 0.05.\\)

BackUpwinding and the CFL Condition ContinueEigenvalue Stability of Finite Difference Methods