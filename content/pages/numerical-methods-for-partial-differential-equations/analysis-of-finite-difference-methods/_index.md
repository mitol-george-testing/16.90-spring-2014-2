---
content_type: page
parent_title: 'Unit 2: Numerical Methods for Partial Differential Equations'
parent_uid: 125c58ac-6a34-5a7c-bba8-de2d3160cb8b
title: 2.4 Analysis of Finite Difference Methods
uid: c9ae23f7-07d4-0d5c-c85b-b19ebf476df0
---

*   [<Forward Time-Backward Space FTBS]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-forward-time-backward-space--ftbs-)
*   [2.4.1Local Truncation Error for a Derivative Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods)
*   [2.4.2Truncation Error of Central Difference Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-of-central-difference-approximation)
*   [2.4.3Truncation Error for a PDE]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-for-a-pde)
*   [2.4.4Finite Difference Methods in Matrix Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-finite-difference-methods-in-matrix-form)
*   [2.4.5General Finite Difference Approximations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-general-finite-difference-approximations)
*   [2.4.6Boundary Conditions for Finite Differences]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-boundary-conditions-for-finite-differences)
*   [\>Truncation Error of Central Difference Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-of-central-difference-approximation)

2.4.1 Local Truncation Error for a Derivative Approximation
-----------------------------------------------------------

[Measurable Outcome 2.8]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO28), [Measurable Outcome 2.9]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO29)

In the discussion of ODE integration, we used the ideas of consistency and stability to prove convergence through the Dahlquist Equivalence Theorem. Similar concepts also exist for PDE discretizations, however, we cannot cover these here. We will briefly review the local truncation error for finite difference approximations of derivatives here and discuss its application in computing the truncation error of a PDE in Section [2.4.3]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-for-a-pde).

Suppose we use a backwards difference, \\(\\delta \_ x^- U\_ i\\) to approximate the first derivative, \\(U\_ x\\) at point \\(i\\). The local truncation error for this derivative approximation can be calculated using Taylor series as we have done in the past:

| &nbsp; | \\(\\displaystyle \\tau\\) | \\(\\displaystyle \\equiv\\) | \\(\\displaystyle \\delta \_ x^{-} U\_ i - {U\_ x}\_ i ,\\) | &nbsp; | (2.61) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{1}{{\\scriptstyle \\Delta } x}\\left( U\_ i - U\_{i-1}\\right) - {U\_ x}\_ i,\\) | &nbsp; | (2.62) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{1}{{\\scriptstyle \\Delta } x}\\left\[ U\_ i - \\left( U\_ i - {\\scriptstyle \\Delta } x{U\_ x}\_ i + \\frac{1}{2}{\\scriptstyle \\Delta } x^2{U\_{xx}}\_ i + O({\\scriptstyle \\Delta } x^3)\\right)\\right\] - {U\_ x}\_ i,\\) | &nbsp; | (2.63) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle -\\frac{1}{2}{\\scriptstyle \\Delta } x{U\_{xx}}\_ i + O({\\scriptstyle \\Delta } x^2).\\) | &nbsp; | (2.64) 

Thus, the analysis shows that the backwards difference is a first-order accurate discretization of the derivative at node \\(i\\).

BackForward Time-Backward Space FTBS ContinueTruncation Error of Central Difference Approximation