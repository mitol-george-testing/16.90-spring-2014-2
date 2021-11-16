---
content_type: page
parent_title: 'Unit 1: Numerical Integration of Ordinary Differential Equations'
parent_uid: 5cae4847-c59a-a247-c767-3c0c6b0abef1
title: 1.4 Convergence
uid: 99ee39b7-79f4-9afb-0849-103c798f1c50
---

*   [<Example of Most Accurate Multi-Step Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-example-of-most-accurate-multi-step-method)
*   [1.4.1Types of Errors]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/convergence)
*   [1.4.2Convergence of Numerical Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/convergence/1690r-convergence-of-numerical-methods)
*   [1.4.3Rate of Convergence Global Order of Accuracy]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/convergence/1690r-rate-of-convergence--global-order-of-accuracy-)
*   [\>Convergence of Numerical Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/convergence/1690r-convergence-of-numerical-methods)

1.4.1 Types of Errors
---------------------

[Measurable Outcome 1.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO15), [Measurable Outcome 1.6]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO16)

When we approximate the solution of ODEs numerically, there are two primary sources of error: rounding (or floating point) errors and truncation errors. Rounding errors are associated to the floating-point arithmetic that our computers use to perform calculations. Truncation errors, on the other hand, are errors we incur based on the numerical method; these errors would exist even in the absence of rounding errors. To some extent, we cannot control rounding errors (they are determined by the precision of the machine), but we can control truncation errors.

**Exercise** How are truncation errors introduced in the Forward Euler method of Section [1.2.4]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-the-forward-euler-method).

Exercise 1

 Taylor series approximation of \\(u^ n\\)

 Taylor series approximation of \\(u^{n+1}\\)

 Taylor series approximation of \\(u\_ t^{n}\\)

 None of the above

CheckShow Answer

Answer: The derivative \\(u^{n}\_ t\\) is evaluated directly, and \\(u^ n\\) is given. The truncation error arises due to truncating the Taylor series of \\(u^{n+1}\\).

BackExample of Most Accurate Multi-Step Method ContinueConvergence of Numerical Methods