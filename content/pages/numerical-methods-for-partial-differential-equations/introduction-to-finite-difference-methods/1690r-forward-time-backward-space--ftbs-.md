---
content_type: page
parent_title: 2.3 Introduction to Finite Difference Methods
parent_uid: 02467893-75dd-44cc-fcac-58f1a4ee9702
title: 2.3 Introduction to Finite Difference Methods
uid: 31ee5fcb-1e6b-78ca-5cb4-d3cb7c073c22
---

*   [<Finite Difference Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-method-applied-to-1-d-convection)
*   [2.3.1Finite Difference Approximations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods)
*   [2.3.2Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-methods)
*   [2.3.3Finite Difference Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-method-applied-to-1-d-convection)
*   [2.3.4Forward Time-Backward Space FTBS]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-forward-time-backward-space--ftbs-)
*   [\>Analysis of Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods)

2.3.4 Forward Time-Backward Space (FTBS)
----------------------------------------

[Measurable Outcome 2.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO23), [Measurable Outcome 2.9]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO29), [Measurable Outcome 2.10]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO210)

Download the code from the Section [2.3.3]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-method-applied-to-1-d-convection). Modify it to use the backward difference formula \\(\\delta \_ x^{-}\\). This method known as the Forward Time-Backward Space (FTBS) method. Using the same \\(u=1, {\\Delta t}= \\frac{1}{1000}\\) and \\(\\Delta x = \\frac{1}{50}\\) does the FTBS method exhibit the same instability as the FTCS method?

Exercise 1

 Yes

 No

 Hard To Tell

 Sometimes

CheckShow Answer

Answer: It can be shown that the FTBS method is stable for the timestep chosen. The stability of the FTBS method means the solution will not grow unbounded in time.

BackFinite Difference Method Applied to 1-D Convection ContinueAnalysis of Finite Difference Methods