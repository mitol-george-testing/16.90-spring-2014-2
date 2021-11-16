---
content_type: page
parent_title: 'Unit 2: Numerical Methods for Partial Differential Equations'
parent_uid: 125c58ac-6a34-5a7c-bba8-de2d3160cb8b
title: 2.5 Introduction to Finite Volume Methods
uid: 3d8df8b8-2291-7094-b5a6-9893808a75cc
---

*   [<Boundary Conditions for Finite Differences]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-boundary-conditions-for-finite-differences)
*   [2.5.1Finite Volume Method in 1-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods)
*   [2.5.2Finite Volume Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-applied-to-1-d-convection)
*   [2.5.3Finite Volume Method in 2-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-in-2-d)
*   [2.5.4Finite Volume Method for 2-D Convection on a Rectangular Mesh]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-2-d-convection-on-a-rectangular-mesh)
*   [2.5.5Finite Volume Method for Nonlinear Systems]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-nonlinear-systems)
*   [\>Finite Volume Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-applied-to-1-d-convection)

2.5.1 Finite Volume Method in 1-D
---------------------------------

[Measurable Outcome 2.1]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO21), [Measurable Outcome 2.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO23)

The basis of the finite volume method is the integral convervation law. The essential idea is to divide the domain into many control volumes and approximate the integral conservation law on each of the control volumes. For example, as shown in Figure [2.13]({{< baseurl >}}/resources/onedfvmesh), cell \\(i\\) lies between the points at \\(x\_{i-\\frac{1}{2}}\\) and \\(x\_{i+\\frac{1}{2}}\\). Note that the points do not have to be equally-spaced.

![This figure shows a horizontal line where the span between two neighboring points is labeled as an approximate of the integral conservation law.](BASEURL_PLACEHOLDER/resources/onedfvmesh)

**Figure 2.13**: Mesh and notation for one-dimensional finite volume method.

The one-dimensional form of Equation [2.1](javascript: void(0)) is

| \\\[\\frac{{\\rm d}}{{\\rm d}t}\\int \_{x\_ L}^{x\_ R} U\\, dx + \\left.F(U)\\right&#124;\_{x\_ R} - \\left.F(U)\\right&#124;\_{x\_ L} = \\int \_{x\_ L}^{x\_ R} S(U,t)\\, dx. \\label{equ:conservation\_1d}\\\] | (2.99) 

Thus, applying this to control volume \\(i\\) (and recalling that \\(S=0\\) for convection) gives,

| \\\[\\frac{{\\rm d}}{{\\rm d}t}\\int \_{x\_{i-\\frac{1}{2}}}^{x\_{i+\\frac{1}{2}}} U\\, dx + \\left. F(U)\\right&#124;\_{x\_{i+\\frac{1}{2}}} - \\left.F(U)\\right&#124;\_{x\_{i-\\frac{1}{2}}} = 0. \\label{equ:conservation\_1d\_ cv}\\\] | (2.100) 

Next, we define the mean value of \\(U\\) in control volume \\(i\\) as,

| \\\[U\_ i \\equiv \\frac{1}{\\Delta x\_ i} \\int \_{x\_{i-\\frac{1}{2}}}^{x\_{i+\\frac{1}{2}}} U\\, dx, \\quad \\mbox{where} \\quad \\Delta x\_ i \\equiv x\_{i+\\frac{1}{2}} - x\_{i-\\frac{1}{2}}.\\\] | (2.101) 

Then, Equation [2.100](javascript: void(0)) becomes,

| \\\[\\Delta x\_ i \\frac{{\\rm d}U\_ i}{{\\rm d}t} + \\left. F(U)\\right&#124;\_{x\_{i+\\frac{1}{2}}} - \\left.F(U)\\right&#124;\_{x\_{i-\\frac{1}{2}}} = 0. \\label{equ:conservation\_1d\_ cv\_ final}\\\] | (2.102) 

At this point, no approximations have been made thus Equation [2.102](javascript: void(0)) is exact. Now, we make the first approximation. Specifically, we assume that the solution in each control volume is constant,

| \\\[U(x,t) = U\_ i(t) \\quad \\mbox{for} \\quad x\_{i-\\frac{1}{2}} < x < x\_{i+\\frac{1}{2}}.\\\] | (2.103) 

Thus, the finite volume approximation will be piecewise constant as shown in Figure [2.14]({{< baseurl >}}/resources/onedpiece).

![This figure has the same features as figure 2.13, but now each span has a box that represents the peicewise constant solution for 1-D finite volume method.](BASEURL_PLACEHOLDER/resources/onedpiece)

**Figure 2.14**: Piecewise constant solution for one-dimensional finite volume method.

With this assumed form of the solution, the next issue is to determine the flux at \\(i\\pm \\frac{1}{2}\\) at a time \\(t\\). This can be done with the knowledge that the solution convects with the velocity \\(u(t)\\). Thus, for the initial instant after \\(t\\) (which we denote as \\(t^{+} = t + \\epsilon\\) where \\(\\epsilon\\) is an infinitesimal, positive number):

| \\\[U(x\_{i+\\frac{1}{2}},t^{+}) = \\left\\{ \\begin{array}{cc} U\_{i}(t) & \\mbox{if } u(t)>0 \\\\ U\_{i+1}(t) & \\mbox{if } u(t)<0 \\end{array}\\right.\\\] | (2.104) 

The flux can be calculated directly from this value of \\(U\\),

| \\\[F(x\_{i+\\frac{1}{2}},t^{+}) = \\left\\{ \\begin{array}{cc} u(t) U\_{i}(t) & \\mbox{if } u(t)>0 \\\\ u(t) U\_{i+1}(t) & \\mbox{if } u(t)<0 \\end{array}\\right.\\\] | (2.105) 

An alternative way to write this flux which is valid regardless of the sign of \\(u(t)\\) is,

| \\\[F(x\_{i+\\frac{1}{2}},t^{+}) = \\frac{1}{2}u(t)\\left\[U\_{i+1}(t) + U\_{i}(t)\\right\] - \\frac{1}{2}&#124;u(t)&#124;\\left\[U\_{i+1}(t) - U\_{i}(t)\\right\]. \\label{equ:upwindflux\_ convection1d\_ continuous}\\\] | (2.106) 

This flux, which uses the upstream value of \\(U\\) to determine the flux, is known as an ‘upwind' flux. When \\(U\\) is positive, the ‘upwind' direction is the negative \\(x\\) direction because the solution moves towards the positive \\(x\\) direction as \\(t\\) increases. When \\(U\\) is negative, the ‘upwind' direction is the positive \\(x\\) direction because the solution moves towards the negative \\(x\\) direction as \\(t\\) increases.

The final step in arriving at a full-discrete approximation for one-dimensional convection is to discretize Equation [2.102](javascript: void(0)) in time. This can be done choosing any of the ODE integration methods we studied previously. For simplicity, we choose the forward Euler method so that the final fully-discrete form of the finite volume method is,

| \\\[\\Delta x\_ i \\frac{U\_ i^{n+1} - U\_ i^ n}{{\\Delta t}} + F\_{i+\\frac{1}{2}}^{n} - F\_{i-\\frac{1}{2}}^ n = 0, \\label{equ:conservation\_1d\_ FVM}\\\] | (2.107) 

where we use the notation,

| \\\[F\_{i+\\frac{1}{2}}^ n = \\frac{1}{2}u^ n\\left(U\_{i+1}^ n + U\_{i}^ n\\right) - \\frac{1}{2}&#124;u^ n&#124;\\left(U\_{i+1}^ n - U\_{i}^ n\\right). \\label{equ:upwindflux\_ convection1d}\\\] | (2.108) 

BackBoundary Conditions for Finite Differences ContinueFinite Volume Method Applied to 1-D Convection