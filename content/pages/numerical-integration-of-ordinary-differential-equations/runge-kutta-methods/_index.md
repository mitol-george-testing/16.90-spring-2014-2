---
content_type: page
parent_title: 'Unit 1: Numerical Integration of Ordinary Differential Equations'
parent_uid: 5cae4847-c59a-a247-c767-3c0c6b0abef1
title: 1.9 Runge-Kutta Methods
uid: c5e7e539-a82c-8e62-0c8a-e738a18f6f10
---

*   [<Backwards Differentiation Excercise]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-excercise)
*   [1.9.1Two-Stage Runge-Kutta Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/runge-kutta-methods)
*   [1.9.2Four-Stage Runge-Kutta Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/runge-kutta-methods/1690r-four-stage-runge-kutta-method)
*   [1.9.3Stability Regions]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/runge-kutta-methods/1690r-stability-regions)
*   [\>Four-Stage Runge-Kutta Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/runge-kutta-methods/1690r-four-stage-runge-kutta-method)

1.9.1 Two-stage Runge-Kutta Methods
-----------------------------------

[Measurable Outcome 1.16]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO116), [Measurable Outcome 1.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO117), [Measurable Outcome 1.19]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO119)

In the previous lectures, we have concentrated on multi-step methods. However, another powerful set of methods are known as multi-stage methods. Perhaps the best known of multi-stage methods are the Runge-Kutta methods. In this lecture, we give some of the most popular Runge-Kutta methods and briefly discuss their properties.

A popular two-stage Runge-Kutta method is known as the modified Euler method:

| &nbsp; | \\(\\displaystyle a\\) | \\(\\displaystyle =\\) | \\(\\displaystyle {\\Delta t}f(v^ n, t^ n)\\) | &nbsp; | (1.139) |
| &nbsp; | \\(\\displaystyle b\\) | \\(\\displaystyle =\\) | \\(\\displaystyle {\\Delta t}f(v^ n + a/2, t^ n + {\\Delta t}/2)\\) | &nbsp; | (1.140) |
| &nbsp; | \\(\\displaystyle v^{n+1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle v^ n + b\\) | &nbsp; | (1.141) 

Another popular two-stage Runge-Kutta method is known as the Heun method:

| &nbsp; | \\(\\displaystyle a\\) | \\(\\displaystyle =\\) | \\(\\displaystyle {\\Delta t}f(v^ n, t^ n)\\) | &nbsp; | (1.142) |
| &nbsp; | \\(\\displaystyle b\\) | \\(\\displaystyle =\\) | \\(\\displaystyle {\\Delta t}f(v^ n + a, t^ n + {\\Delta t})\\) | &nbsp; | (1.143) |
| &nbsp; | \\(\\displaystyle v^{n+1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle v^ n + \\frac{1}{2}(a+b)\\) | &nbsp; | (1.144) 

As can been seen with either of these methods, \\(f\\) is evaluated twice in finding the new value of \\(v^{n+1}\\): once to determine \\(a\\) and once to determine \\(b\\). Both of these methods are second-order accurate, \\(p=2\\).

BackBackwards Differentiation Excercise ContinueFour-Stage Runge-Kutta Method