---
content_type: page
parent_title: 1.7 Stiffness and Implicit Methods
parent_uid: 935324e3-1ab2-cb57-9059-0ba1f034fcd5
title: 1.7 Stiffness and Implicit Methods
uid: 543e8406-3445-482c-0202-05c77ce31e71
---

*   [<Spectral Condition Number]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-spectral-condition-number)
*   [1.7.1Stiffness]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods)
*   [1.7.2Spectral Condition Number]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-spectral-condition-number)
*   [1.7.3Implicit Methods for Linear Systems of ODEs]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-implicit-methods-for-linear-systems-of-odes)
*   [1.7.4Newton-Raphson Implement Implicit Methods on Nonlinear Problems]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-newton-raphson-implement-implicit-methods-on-nonlinear-problems)
*   [1.7.5Apply Newton-Rhapson]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-apply-newton-rhapson)
*   [\>Newton-Raphson Implement Implicit Methods on Nonlinear Problems]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-newton-raphson-implement-implicit-methods-on-nonlinear-problems)

1.7.3 Implicit Methods for Linear Systems of ODE's
--------------------------------------------------

[Measurable Outcome 1.9]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO19), [Measurable Outcome 1.11]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO111), [Measurable Outcome 1.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO112), [Measurable Outcome 1.13]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO113)

While implicit methods can allow significantly larger timesteps, they do involve more work than explicit methods. Consider the forward method applied to \\(u\_ t = Au\\) where \\(A\\) is a \\(d \\times d\\) matrix.

| \\\[v^{n+1} = v^ n + {\\Delta t}A v^ n.\\\] | (1.122) 

In this explicit algorithm, the largest computational cost is the matrix vector multiply, \\(A v^ n\\) which is an \\(O(d^2)\\) operation. Now, for backward Euler,

| \\\[v^{n+1} = v^ n + {\\Delta t}A v^{n+1}.\\\] | (1.123) 

Re-arranging to solve for \\(v^{n+1}\\) gives:

| &nbsp; | \\(\\displaystyle v^{n+1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle v^ n + {\\Delta t}A v^{n+1},\\) | &nbsp; | (1.124) |
| &nbsp; | \\(\\displaystyle v^{n+1} - {\\Delta t}A v^{n+1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle v^ n,\\) | &nbsp; | (1.125) |
| &nbsp; | \\(\\displaystyle \\left(I - {\\Delta t}A\\right)v^{n+1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle v^ n,\\) | &nbsp; | (1.126) 

Thus, to find \\(v^{n+1}\\) requires the solution of a \\(d \\times d\\) system of equations which is an \\(O(d^3)\\) cost. As a result, for large systems, the cost of the \\(O(d^3)\\) linear solution may begin to outweigh the benefits of the larger timesteps that are possible when using implicit methods.

BackSpectral Condition Number ContinueNewton-Raphson Implement Implicit Methods on Nonlinear Problems