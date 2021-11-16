---
content_type: page
parent_title: 2.4 Analysis of Finite Difference Methods
parent_uid: c9ae23f7-07d4-0d5c-c85b-b19ebf476df0
title: 2.4 Analysis of Finite Difference Methods
uid: 9064faf9-febc-8ca2-e94e-1b057fcc34be
---

*   [<Analysis of Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods)
*   [2.4.1Local Truncation Error for a Derivative Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods)
*   [2.4.2Truncation Error of Central Difference Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-of-central-difference-approximation)
*   [2.4.3Truncation Error for a PDE]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-for-a-pde)
*   [2.4.4Finite Difference Methods in Matrix Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-finite-difference-methods-in-matrix-form)
*   [2.4.5General Finite Difference Approximations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-general-finite-difference-approximations)
*   [2.4.6Boundary Conditions for Finite Differences]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-boundary-conditions-for-finite-differences)
*   [\>Truncation Error for a PDE]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-for-a-pde)

2.4.2 Truncation Error of Central Difference Approximation
----------------------------------------------------------

[Measurable Outcome 2.8]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO28)

What is the truncation error and order of accuracy of the central difference approximation \\(\\delta \_{2x}U\_ i = \\frac{U\_{i+1}-U\_{i-1}}{2\\Delta x}\\) of \\(U\_{x\_ i}\\)

Exercise 1

 \\(-\\frac{1}{3}\\Delta x U\_{xx\_ i} + \\mathcal{O}(\\Delta x^3)\\), first-order accurate

 \\(-\\frac{1}{6}\\Delta x U\_{xxx\_ i} + \\mathcal{O}(\\Delta x^3)\\), first-order accurate

 \\(-\\frac{1}{6}\\Delta x^2 U\_{xxx\_ i} + \\mathcal{O}(\\Delta x^4)\\), second-order accurate

 \\(-\\frac{1}{12}\\Delta x^2 U\_{xxx\_ i} + \\mathcal{O}(\\Delta x^4)\\), second-order accurate

CheckShow Answer

Answer: The truncation error can be computed by inserting the Taylor series into the finite difference approximation and cancelling the appropriate terms. Since the error is \\(\\mathcal{O}(\\Delta x^2)\\), the approximation is second-order accurate.

BackAnalysis of Finite Difference Methods ContinueTruncation Error for a PDE