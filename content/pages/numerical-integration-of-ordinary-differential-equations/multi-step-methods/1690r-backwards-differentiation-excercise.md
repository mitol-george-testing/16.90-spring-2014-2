---
content_type: page
parent_title: 1.8 Multi-Step Methods
parent_uid: 67717326-dffb-7444-5162-101fd9a9ec91
title: 1.8 Multi-Step Methods
uid: f02cecfe-1cd4-8c17-eeff-25be1aaa895d
---

*   [<Backwards Differentiation Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-methods)
*   [1.8.1Adams-Bashforth Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods)
*   [1.8.2Adams-Moulton Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-adams-moulton-methods)
*   [1.8.3Backwards Differentiation Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-methods)
*   [1.8.4Backwards Differentiation Excercise]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-excercise)
*   [\>Runge-Kutta Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/runge-kutta-methods)

1.8.4 Backwards Differentiation Exercise
----------------------------------------

[Measurable Outcome 1.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO112), [Measurable Outcome 1.15]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO115), [Measurable Outcome 1.18]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO118), [Measurable Outcome 1.19]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO119)

Suppose we wish to simulate the ODE \\(u\_ t = Au\\) defined by the 2-by-2 matrix \\(A\\) for \\({\\Delta t}=0.1\\). For which of the following \\(A\\) matrices will the fourth-order accurate backwards differentiation method be eigenvalue stable?

Exercise 1

&nbsp; \\(A = \\left\[\\begin{array}{cc} 0 & 1 \\\\ -180 & 0 \\end{array}\\right\]\\) &nbsp;

&nbsp; \\(A = \\left\[\\begin{array}{cc} 0 & 1 \\\\ -290 & -2 \\end{array}\\right\]\\) &nbsp;

&nbsp; \\(A = \\left\[\\begin{array}{cc} 0 & 1 \\\\ -8 & -4 \\end{array}\\right\]\\) &nbsp;

&nbsp; \\(A = \\left\[\\begin{array}{cc} -5 & 0 \\\\ 0 & 5 \\end{array}\\right\]\\) &nbsp;

CheckShow Answer

Answer: The third matrix is the only one with both eigenvalues inside of the stability region for \\({\\Delta t}=0.1\\).

BackBackwards Differentiation Methods ContinueRunge-Kutta Methods