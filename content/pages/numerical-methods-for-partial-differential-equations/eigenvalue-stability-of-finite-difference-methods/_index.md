---
content_type: page
parent_title: 'Unit 2: Numerical Methods for Partial Differential Equations'
parent_uid: 125c58ac-6a34-5a7c-bba8-de2d3160cb8b
title: 2.7 Eigenvalue Stability of Finite Difference Methods
uid: 935b6a61-8d7d-2772-6ca1-df78ee864834
---

*   [<The CFL Condition]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/upwinding-and-the-cfl-condition/1690r-the-cfl-condition)
*   [2.7.1Fourier Analysis of PDEs]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods)
*   [2.7.2Matrix Stability for Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-matrix-stability-for-finite-difference-methods)
*   [2.7.3Circulant Matrices]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-circulant-matrices)
*   [2.7.4Stability Exercises]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-stability-exercises)
*   [\>Matrix Stability for Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-matrix-stability-for-finite-difference-methods)

2.7.1 Fourier Analysis of PDEs
------------------------------

[Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22), [Measurable Outcome 2.11]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO211)

We will develop Fourier analysis in one dimension. The basic ideas extend easily to multiple dimensions. We will consider the convection-diffusion equation,

| \\\[\\frac{\\partial U}{\\partial t} + u\\frac{\\partial U}{\\partial x} = \\mu \\frac{\\partial ^2 U}{\\partial x^2}.\\\] | (2.124) 

We will assume that the velocity, \\(u\\), and the viscosity, \\(\\mu\\) are constant.

The solution is assumed to be periodic over a length \\(L\\). Thus,

| \\\[U(x+mL,t) = U(x,t)\\\] | (2.125) 

where \\(m\\) is any integer.

A Fourier series with periodicity over length \\(L\\) is given by,

| \\\[U(x,t) = \\sum \_{m=-\\infty }^{+\\infty } \\hat{U}\_ m(t)e^{i k\_ m x} \\qquad \\mbox{where} \\qquad k\_ m = \\frac{2\\pi m}{L}. \\label{equ:Fourier}\\\] | (2.126) 

\\(k\_ m\\) is generally called the wavenumber, though \\(m\\) is the number of waves occurring over the length \\(L\\). We note that \\(\\hat{U}\_ m(t)\\) is the amplitude of the \\(m\\)-th wavenumber and it is generally complex (since we have used complex exponentials). Substituting the Fourier series into the convection-diffusion equation gives,

| \\\[\\frac{\\partial }{\\partial t}\\left\[\\sum \_{m=-\\infty }^{+\\infty } \\hat{U}\_ m(t)e^{i k\_ m x}\\right\] + u \\frac{\\partial }{\\partial x}\\left\[\\sum \_{m=-\\infty }^{+\\infty } \\hat{U}\_ m(t)e^{i k\_ m x}\\right\] = \\mu \\frac{\\partial ^2}{\\partial x^2}\\left\[\\sum \_{m=-\\infty }^{+\\infty } \\hat{U}\_ m(t)e^{i k\_ m x}\\right\].\\\] | (2.127) | \\\[\\sum \_{m=-\\infty }^{+\\infty } \\frac{{\\rm d}\\hat{U}\_ m}{{\\rm d}t} e^{i k\_ m x} + u \\sum \_{m=-\\infty }^{+\\infty } i k\_ m \\hat{U}\_ m e^{i k\_ m x} = \\mu \\sum \_{m=-\\infty }^{+\\infty } (i k\_ m)^2 \\hat{U}\_ m e^{i k\_ m x}.\\\] | (2.128) 

Noting that \\(i^2 = -1\\) and collecting terms gives,

| \\\[\\sum \_{m=-\\infty }^{+\\infty } \\left\[\\frac{{\\rm d}\\hat{U}\_ m}{{\\rm d}t} + \\left(i u k\_ m + \\mu k\_ m^2\\right) \\hat{U}\_ m\\right\] e^{i k\_ m x} = 0. \\label{equ:Fourier\_ preorth}\\\] | (2.129) 

The next step is to utilize the orthogonality of the different Fourier modes over the length \\(L\\), specifically,

| \\\[\\int \_0^ L e^{-i k\_ n x} e^{i k\_ m x} dx = \\left\\{ \\begin{array}{cc} 0 & \\mbox{if } m \\neq n \\\\ L & \\mbox{if } m = n \\end{array}\\right. \\label{equ:Fourier\_ orth}\\\] | (2.130) 

By multiplying Equation ([2.129](javascript: void(0))) by \\(e^{-i k\_ n x}\\) and integrating from \\(0\\) to \\(L\\), the orthogonality condition gives,

| \\\[\\frac{{\\rm d}\\hat{U}\_ n}{{\\rm d}t} + \\left(i u k\_ n + \\mu k\_ n^2\\right) \\hat{U}\_ n = 0, \\qquad \\mbox{for any integer value of } n. \\label{equ:Fourier\_ condif1d}\\\] | (2.131) 

Thus, the evolution of the amplitude for an individual wavenumber is independent of the other wavenumbers. The solution to Equation ([2.131](javascript: void(0))),

| \\\[\\hat{U}\_ n(t) = \\hat{U}\_ n(0) e^{-i u k\_ n t} e^{-\\mu k\_ n^2 t}.\\\] | (2.132) 

The convection term, which results in the complex time dependent behavior, \\(e^{-i u k\_ n t}\\), only oscillates and does not change the magnitude of \\(\\hat{U}\_ n\\). The diffusion term causes the magnitude to decrease as long as \\(\\mu > 0\\). But, if the diffusion coefficient were negative, then the magnitude would increase unbounded with time. Thus, in the case of the convection-diffusion PDE, as long as \\(\\mu \\geq 0\\), this solution is stable.

Exercise
--------

For the convection-diffusion equation analyzed above, how does the rate of damping compare for a wavelength \\(L\\) mode to a wavelength \\(L/10\\) mode?

Exercise 1

&nbsp; 10 times slower &nbsp;

&nbsp; The damping rates are equal &nbsp;

&nbsp; 1000 times slower &nbsp;

&nbsp; 100 times slower &nbsp;

CheckShow Answer

Answer: The \\(L\_1\\) mode has a damping rate \\(\\mu k\_ m^2 = \\mu (2\\pi /L)^2\\) the \\(L/10\\) mode has a damping rate of \\(\\mu k\_ m^2 = \\mu (20\\pi /L)^2\\)

BackThe CFL Condition ContinueMatrix Stability for Finite Difference Methods