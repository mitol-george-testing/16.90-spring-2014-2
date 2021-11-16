---
content_type: page
parent_title: 2.7 Eigenvalue Stability of Finite Difference Methods
parent_uid: 935b6a61-8d7d-2772-6ca1-df78ee864834
title: 2.7 Eigenvalue Stability of Finite Difference Methods
uid: cb633bb1-3925-0ab5-7f90-8bb74bb848bb
---

*   [<Circulant Matrices]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-circulant-matrices)
*   [2.7.1Fourier Analysis of PDEs]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods)
*   [2.7.2Matrix Stability for Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-matrix-stability-for-finite-difference-methods)
*   [2.7.3Circulant Matrices]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-circulant-matrices)
*   [2.7.4Stability Exercises]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-stability-exercises)
*   [\>Method of Weighted Residuals]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals)

2.7.4 Stability Exercises
-------------------------

[Measurable Outcome 2.9]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO29), [Measurable Outcome 2.10]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO210), [Measurable Outcome 2.11]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO211)

Exercise 1
----------

Download the MATLAB® code in Section [2.7.2]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-matrix-stability-for-finite-difference-methods). Modify this code to compute the eigenvalues of the FTBS method with periodic boundary conditions. For CFL=1, where are there eigenvalues of \\(A\\)?

Exercise 1

&nbsp; All in the left half plane &nbsp;

&nbsp; Two in the left half plane, the rest in a circle in the right half plane &nbsp;

&nbsp; Two in the right half plane, the rest in a circle in the right half plane &nbsp;

&nbsp; "Along the imaginary axis &nbsp;

Answer:

To implement a backward spatial discretization, we modify the matrix A:

for i = 2:Nx-1 A(i,i) = u/dx; A(i,i-1) = -u/dx; end

Exercise 2
----------

Compute analytically the eigenvalues for the FTBS method with periodic boundary conditions. The eigenvalues are

Exercise 2

&nbsp; \\(-\\frac{u}{\\Delta x} -\\frac{u}{\\Delta x}\\left\[\\cos \\left(2\\pi \\frac{n}{N}\\right) - i\\sin \\left(2\\pi \\frac{n}{N}\\right)\\right\]\\) &nbsp;

&nbsp; \\(-\\frac{u}{\\Delta x} +\\frac{u}{\\Delta x}\\left\[\\cos \\left(2\\pi \\frac{n}{N}\\right) - i\\sin \\left(2\\pi \\frac{n}{N}\\right)\\right\]\\) &nbsp;

&nbsp; \\(\\frac{u}{\\Delta x} +\\frac{u}{\\Delta x}\\left\[\\cos \\left(2\\pi \\frac{n}{N}\\right) + i\\sin \\left(2\\pi \\frac{n}{N}\\right)\\right\]\\) &nbsp;

&nbsp; \\(-\\frac{u}{\\Delta x} +\\frac{u}{\\Delta x}\\left\[\\cos \\left(2\\pi \\frac{n}{N}\\right) + i\\sin \\left(2\\pi \\frac{n}{N}\\right)\\right\]\\) &nbsp;

CheckShow Answer

Answer: We use the formula for the eigenvalues of a circulant matrix with \\(a\_1= -u/\\Delta x\\) and \\(a\_ N = u/ \\Delta x\\).

BackCirculant Matrices ContinueMethod of Weighted Residuals