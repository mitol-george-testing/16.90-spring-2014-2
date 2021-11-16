---
content_type: page
parent_title: 2.8 Method of Weighted Residuals
parent_uid: bda18124-71a5-87a7-513f-cb81480a1e18
title: 2.8 Method of Weighted Residuals
uid: b85dba09-9fd2-582c-61f1-a5573f5c79a5
---

*   [<The Method of Weighted Residuals]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-the-method-of-weighted-residuals)
*   [2.8.1Functional Approximation of the Solution]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals)
*   [2.8.2The Collocation Method]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-the-collocation-method)
*   [2.8.3The Method of Weighted Residuals]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-the-method-of-weighted-residuals)
*   [2.8.4Galerkin Method with New Basis]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-galerkin-method-with-new-basis)
*   [\>Introduction to Finite Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements)

2.8.4 Galerkin Method with New Basis
------------------------------------

[Measurable Outcome 2.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO212), [Measurable Outcome 2.13]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO213), [Measurable Outcome 2.14]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO214)

Suppose we introduce another basis function \\(\\phi \_3(x) = x^2(1-x)(1+x)\\) into the example problem discussed in Section 2.8.3, which introduces an additional unknown \\(a\_3\\). Use the Galerkin approach to solve for the new values \\(a\_1\\), \\(a\_2\\), and \\(a\_3\\). (Hint: to check your solution, it might be a good idea to plot the estimate of \\(\\tilde{T}\\) to check if it agrees well with the plot above.) Please include at least two decimal places in your answer.

\\(a\_1\\):

Exercise 1

Numerical Response

\\(a\_2\\):

Exercise 2

Numerical Response

\\(a\_3\\):

Exercise 3

Numerical Response

CheckShow Answer

Answer:

The three residual equations that we solve are:

| \\\[R\_1(\\tilde{T}) = -8/3 a\_1 - 8/15 a\_3 + 200e^{-1} = 0\\\] | (2.195) | \\\[R\_2(\\tilde{T}) = -8/5 a\_2 +100e^1 - 700e^{-1} = 0\\\] | (2.196) | \\\[R\_3(\\tilde{T}) = -8/15 a\_1 - 88/105 a\_3 -400e^{1}+ 3000e^{-1} = 0\\\] | (2.197) 

BackThe Method of Weighted Residuals ContinueIntroduction to Finite Elements