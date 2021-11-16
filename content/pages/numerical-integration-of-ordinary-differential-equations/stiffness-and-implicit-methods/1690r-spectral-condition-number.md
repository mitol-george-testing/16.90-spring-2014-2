---
content_type: page
parent_title: 1.7 Stiffness and Implicit Methods
parent_uid: 935324e3-1ab2-cb57-9059-0ba1f034fcd5
title: 1.7 Stiffness and Implicit Methods
uid: 900cc931-acfb-c435-72d7-f303ce81ef83
---

*   [<Stiffness and Implicit Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods)
*   [1.7.1Stiffness]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods)
*   [1.7.2Spectral Condition Number]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-spectral-condition-number)
*   [1.7.3Implicit Methods for Linear Systems of ODEs]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-implicit-methods-for-linear-systems-of-odes)
*   [1.7.4Newton-Raphson Implement Implicit Methods on Nonlinear Problems]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-newton-raphson-implement-implicit-methods-on-nonlinear-problems)
*   [1.7.5Apply Newton-Rhapson]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-apply-newton-rhapson)
*   [\>Implicit Methods for Linear Systems of ODEs]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-implicit-methods-for-linear-systems-of-odes)

1.7.2 Spectral Condition Number
-------------------------------

[Measurable Outcome 1.9]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO19), [Measurable Outcome 1.11]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO111), [Measurable Outcome 1.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO112)

Stiffness can also arise in linear or linearized systems when eigenvalues exist with significantly different magnitudes. For example,

| \\\[u\_ t = Au, \\qquad A = \\left(\\begin{array}{cc} -1 & 1 \\\\ 0 & -1000 \\end{array} \\right).\\\] | (1.120) 

The eigenvalues of \\(A\\) are \\(\\lambda = -1\\) and \\(\\lambda = -1000\\). Since the timestep must be set so that both eigenvalues are stable, the larger eigenvalue will dominate the timestep. The spectral condition number is the ratio of the largest to smallest eigenvalue magnitudes,

| \\\[\\mbox{Spectral Condition Number} = \\frac{\\max &#124;\\lambda \_ j&#124;}{\\min &#124;\\lambda \_ j&#124;}\\\] | (1.121) 

When the spectral condition number is greater than around 1000, problems are starting to become stiff and implicit methods are likely to be more efficient than explicit methods.

**Exercise** What is the spectral condition number of the matrix \\(A = \\left\[\\begin{array}{cc} 1032 & 18 \\\\ 54 & -200 \\end{array}\\right\]\\). Please answer with at least 3 significant digits.

Exercise 1

Numerical Response

CheckShow Answer

Answer: The eigenvalues are \\(\\lambda \_1=1032.788\\) and \\(\\lambda \_2=-200.788\\). The ratio of their absolute values gives the correct answer.

BackStiffness and Implicit Methods ContinueImplicit Methods for Linear Systems of ODEs