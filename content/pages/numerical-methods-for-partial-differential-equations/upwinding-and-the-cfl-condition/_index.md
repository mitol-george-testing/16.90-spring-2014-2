---
content_type: page
parent_title: 'Unit 2: Numerical Methods for Partial Differential Equations'
parent_uid: 125c58ac-6a34-5a7c-bba8-de2d3160cb8b
title: 2.6 Upwinding and the CFL Condition
uid: ce70b6b2-dea9-62c9-1d8e-4789958e4499
---

*   [<Finite Volume Method for Nonlinear Systems]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-nonlinear-systems)
*   [2.6.1Upwinding]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/upwinding-and-the-cfl-condition)
*   [2.6.2The CFL Condition]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/upwinding-and-the-cfl-condition/1690r-the-cfl-condition)
*   [\>The CFL Condition]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/upwinding-and-the-cfl-condition/1690r-the-cfl-condition)

2.6.1 Upwinding
---------------

[Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22), [Measurable Outcome 2.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO25), [Measurable Outcome 2.6]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO26), [Measurable Outcome 2.9]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO29)

Consider the one-dimensional convection equation,

| &nbsp; | \\(\\displaystyle \\dfrac {\\partial U}{\\partial t} + u \\dfrac {\\partial U}{\\partial x}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0.\\) | &nbsp; | (2.120) 

For simplicity, we will consider the specific case in which \\(u>0\\). Recall that for the convection equation, the solution \\(U(x,t)\\) is obtained by following the characteristic line back to the inditial condition and evaluating \\(U\_0(\\xi )\\) where \\(\\xi = x-ut\\). For the case of \\(u>0\\) this means that the solution at \\((\\hat{x}, \\hat{t})\\) only depend on the locations to the left of \\(\\hat{x}\\) and for tmes before \\(\\hat{t}\\). Since the convection equation has some inherent directionality, it is natural for our numerical scheme to also have some sort of directional bias. First consider the FTCS method. The solution \\(U\_ i^{n+1}\\) is updated as:

| &nbsp; | \\(\\displaystyle U\_ i^{n+1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle U\_ i^{n} -\\frac{u \\Delta t}{2 \\Delta x} (U\_{i+1}^{n}-U\_{i-1}^ n)\\) | &nbsp; | (2.121) 

This is graphically depicted in Figure [2.16]({{< baseurl >}}/resources/soldepftcs). This numerical scheme has no inherent directionality as it uses a derivative approximation that is centered, taking equal (magnitude) weights from nodes to the left and right.

![The graph, generated using the Forward Time-Central Space method, shows points at intersections of the x and y axes, which all refer to one centered derivative approximation.](BASEURL_PLACEHOLDER/resources/soldepftcs)

**Figure 2.16**: Solution dependence using the Forward Time-Central Space method.

Now consider the Forward Time-Backward Space (FTBS) method. It uses the backwards difference formula \\(\\delta \_ x^{-}U\_ i\\), and gives the update

| &nbsp; | \\(\\displaystyle U\_ i^{n+1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle U\_ i^{n} -\\frac{u\\Delta t}{\\Delta x} (U\_{i}^{n}-U\_{i-1}^ n).\\) | &nbsp; | (2.122) 

The method is graphically depicted in Figure [2.17]({{< baseurl >}}/resources/soldepftbs).

![This graph, generated using the Forward Time-Backward Space method, shows points at the intersections of the x and y axes, which all refer to one centered derivative approximation.  The graph shows how the numerical scheme is now biased to upstream values.](BASEURL_PLACEHOLDER/resources/soldepftbs)

**Figure 2.17**: Solution dependence using the Forward Time-Backward Space method.

Notice that the numerical scheme is now biased to upstream values. The upstream direction is the left in this case, because the characteristic lines travel towards the right as time increases. (The upstream direction would be the right if the characteristic lines travel towrads the left as time increases.) Numerical schemes which exhibit such an upstream bias are called **upwind** schemes. Thus, the FTBS method is also known as the first-order upwind scheme. Not that when \\(u<0\\) then the forward difference \\(\\delta \_ x^{+}U\_ i = (U\_{i+1}-U\_{i})/\\Delta x\\) leads to the correct upwind scheme.

Exercise
--------

Which of the following is a second-order accurate upwind difference of \\(U\_{x\_ i}\\) (assume positive convection velocity)?

Exercise 1

 \\((U\_{i+1}-U\_ i)/\\Delta x\\)

 \\((\\frac{3}{2} U\_ i - 2 U\_{i-1}+\\frac{1}{2} U\_{i-2})/\\Delta x\\)

 \\((\\frac{3}{4} U\_ i - U\_{i-1}+\\frac{1}{2} U\_{i-2})/\\Delta x\\)

 \\((U\_{i}-U\_{i-1})/\\Delta x\\)

CheckShow Answer

Answer: By plugging in the Taylor series expansion of each term, we see that this formula is a second order accurate approximation of the first deriative at \\(i\\).

BackFinite Volume Method for Nonlinear Systems ContinueThe CFL Condition