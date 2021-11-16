---
content_type: page
parent_title: 2.7 Eigenvalue Stability of Finite Difference Methods
parent_uid: 935b6a61-8d7d-2772-6ca1-df78ee864834
title: 2.7 Eigenvalue Stability of Finite Difference Methods
uid: c4a73127-b3ff-feee-5cd9-2e3e6319d356
---

*   [<Matrix Stability for Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-matrix-stability-for-finite-difference-methods)
*   [2.7.1Fourier Analysis of PDEs]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods)
*   [2.7.2Matrix Stability for Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-matrix-stability-for-finite-difference-methods)
*   [2.7.3Circulant Matrices]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-circulant-matrices)
*   [2.7.4Stability Exercises]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-stability-exercises)
*   [\>Stability Exercises]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-stability-exercises)

2.7.3 Circulant Matrices
------------------------

[Measurable Outcome 2.10]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO210), [Measurable Outcome 2.11]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO211)

Though the eigenvalues of \\(A\\) typically require numerical techniques for the general problem, a special case of practical interest occurs when the matrix is ‘periodic'. That is, the column entries shift a column every row. Thus, the matrix has the form,

| \\\[A = \\left(\\begin{array}{ccccc} a\_1 & a\_2 & a\_3 & \\ldots & a\_{N } \\\\ a\_ N & a\_1 & a\_2 & \\ldots & a\_{N-1} \\\\ \\vdots & \\vdots & \\vdots & \\ddots & \\vdots \\\\ a\_2 & a\_3 & a\_4 & \\ldots & a\_1 \\end{array}\\right)\\\] | (2.140) 

This type of matrix is known as a circulant matrix. Circulant matrices have eigenvalues given by,

| \\\[\\lambda \_ n = \\sum \_{j=1}^{N} a\_ j e^{i\\, 2\\pi (j-1) \\frac{n}{N}} \\qquad \\mbox{for} \\quad n = 0, 1, \\ldots , N-1 \\label{equ:circulant\_ eig}\\\] | (2.141) 

As we saw in Section [2.7.2]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-matrix-stability-for-finite-difference-methods), when periodic boundary conditions are assumed, the central space discretization of one-dimensional convection gives purely imaginary eigenvalues, and when scaled by a timestep for which the CFL number is one, the eigenvalues stretch along the axis until \\(\\pm i\\). Since for a convection problem with constant velocity and periodic boundary conditions gives a circulant matrix, we can use Equation ([2.141](javascript: void(0))) to determine the eigenvalues analytically. We begin by finding the coefficients, \\(a\_ j\\). For a central space discretization, we find,

| \\\[a\_2 = -\\frac{u}{2{\\scriptstyle \\Delta } x}, \\quad a\_ N = \\frac{u}{2{\\scriptstyle \\Delta } x}, \\mbox{ and for all other } j, \\quad a\_ j = 0.\\\] | (2.142) 

Then, substituting these \\(a\_ j\\) into Equation ([2.141](javascript: void(0))) gives,

| &nbsp; | \\(\\displaystyle \\lambda \_ n\\) | \\(\\displaystyle =\\) | \\(\\displaystyle -\\frac{u}{2{\\scriptstyle \\Delta } x} e^{i\\, 2\\pi \\frac{n}{N}} + \\frac{u}{2{\\scriptstyle \\Delta } x} e^{i\\, 2\\pi (N-1) \\frac{n}{N}},\\) | &nbsp; | (2.143) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle -\\frac{u}{2{\\scriptstyle \\Delta } x} e^{i\\, 2\\pi \\frac{n}{N}} + \\frac{u}{2{\\scriptstyle \\Delta } x} e^{i\\, 2\\pi n} e^{-i\\, 2\\pi \\frac{n}{N}}.\\) | &nbsp; | (2.144) 

Since \\(e^{i\\, 2\\pi n} = 1\\) (because \\(n\\) is an integer), then,

| &nbsp; | \\(\\displaystyle \\lambda \_ n\\) | \\(\\displaystyle =\\) | \\(\\displaystyle -\\frac{u}{2{\\scriptstyle \\Delta } x} e^{i\\, 2\\pi \\frac{n}{N}} + \\frac{u}{2{\\scriptstyle \\Delta } x} e^{-i\\, 2\\pi \\frac{n}{N}},\\) | &nbsp; | (2.145) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle -\\frac{u}{2{\\scriptstyle \\Delta } x}\\left(e^{i\\, 2\\pi \\frac{n}{N}} - e^{-i\\, 2\\pi \\frac{n}{N}}\\right),\\) | &nbsp; | (2.146) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle -i\\frac{u}{{\\scriptstyle \\Delta } x}\\sin \\left(2\\pi \\frac{n}{N}\\right).\\) | &nbsp; | (2.147) 

Multiplying by the timestep,

| \\\[\\lambda \_ n {\\Delta t}= -i\\frac{u{\\Delta t}}{{\\scriptstyle \\Delta } x}\\sin \\left(2\\pi \\frac{n}{N}\\right).\\\] | (2.148) 

As observed in Section [2.7.2]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-matrix-stability-for-finite-difference-methods), the eigenvalues are purely imaginary and will extend to \\(\\pm i\\) when \\(\\mathrm{CFL} = |u|{\\Delta t}/{\\scriptstyle \\Delta } x= 1\\).

BackMatrix Stability for Finite Difference Methods ContinueStability Exercises