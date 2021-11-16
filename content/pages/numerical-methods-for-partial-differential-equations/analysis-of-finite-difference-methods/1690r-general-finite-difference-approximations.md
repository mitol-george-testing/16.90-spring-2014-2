---
content_type: page
parent_title: 2.4 Analysis of Finite Difference Methods
parent_uid: c9ae23f7-07d4-0d5c-c85b-b19ebf476df0
title: 2.4 Analysis of Finite Difference Methods
uid: 7e5587c8-fac2-cbac-56c4-7e6cdfc52004
---

*   [<Finite Difference Methods in Matrix Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-finite-difference-methods-in-matrix-form)
*   [2.4.1Local Truncation Error for a Derivative Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods)
*   [2.4.2Truncation Error of Central Difference Approximation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-of-central-difference-approximation)
*   [2.4.3Truncation Error for a PDE]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-truncation-error-for-a-pde)
*   [2.4.4Finite Difference Methods in Matrix Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-finite-difference-methods-in-matrix-form)
*   [2.4.5General Finite Difference Approximations]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-general-finite-difference-approximations)
*   [2.4.6Boundary Conditions for Finite Differences]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-boundary-conditions-for-finite-differences)
*   [\>Boundary Conditions for Finite Differences]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/analysis-of-finite-difference-methods/1690r-boundary-conditions-for-finite-differences)

2.4.5 General Finite Difference Approximations
----------------------------------------------

[Measurable Outcome 2.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO23), [Measurable Outcome 2.8]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO28)

So far we have developed several finite difference approximations for the first derivative and the central difference operator for the second derivative. As we've seen before for first and second derivative approximations, finite difference approximations may be obtained from the definition of the derivative. In practice, generating a finite difference approximation starting from the definition of the derivative can be difficult to extend to a variety of situations. For example, suppose that a backwards difference was desired for \\(U\_{x\_ i}\\) using three nodes. Mathematically, we want to find coefficients \\(\\alpha \_ i\\), \\(\\alpha \_{i-1}\\), and \\(\\alpha \_{i-2}\\) of \\(U\_ i\\), \\(U\_{i-1}\\), and \\(U\_{i-2}\\) that would give an approximation to \\(U\_{x\_ i}\\), i.e.

| \\\[\\frac{1}{\\Delta x}\\left(\\alpha \_ i U\_ i + \\alpha \_{i-1} U\_{i-1} + \\alpha \_{i-2} U\_{i-2}\\right) \\approx {U\_ x}\_ i.\\\] | (2.81) 

Note, we have included a factor of \\(1/\\Delta x\\) in this backwards finite difference approximation of the first derivative since we know that the formal definition of the first derivative involves calculating the difference of \\(U(x+\\Delta x/2)\\) and \\(U(x-\\Delta x/2)\\) dividing by \\(\\Delta x\\). Doing this, the coefficients \\(\\alpha\\) will not depend on \\(\\Delta x\\). Now, we will utilize Taylor series to construct the truncation error for this approximation and then find the \\(\\alpha\\) values that achieve the highest-order of accuracy. The necessary Taylor series expansions are,

| &nbsp; | \\(\\displaystyle \\begin{array}{rcrcrcrcrcr} U\_{i} & = & U\_{i} \\\\ U\_{i-1} & = & U\_ i & -& \\Delta x {U\_ x}\_ i & +& \\frac{1}{2} \\Delta x^2 {U\_{xx}}\_ i & -& \\frac{1}{6} \\Delta x^3 {U\_{xxx}}\_ i & +& O(\\Delta x^4) \\\\ U\_{i-2} & = & U\_ i & -& (2\\Delta x) {U\_ x}\_ i & +& \\frac{1}{2} (2\\Delta x)^2 {U\_{xx}}\_ i & -& \\frac{1}{6} (2\\Delta x)^3 {U\_{xxx}}\_ i & +& O(\\Delta x^4) \\end{array}\\) | &nbsp; | (2.82) 

Substituting these Taylor series into the three-point backwards difference formula and gathering the terms that are the same order in \\(\\Delta x\\) gives,

| \\\[\\begin{array}{ccrcccccrr} \\frac{1}{\\Delta x}\\left(\\alpha \_ i U\_ i + \\alpha \_{i-1} U\_{i-1} + \\alpha \_{i-2} U\_{i-2}\\right) & = & ( & \\alpha \_{i} & +& \\alpha \_{i-1} & +& \\alpha \_{i-2} & ) & \\frac{1}{\\Delta x} U\_ i \\\\ & - & ( & & & \\alpha \_{i-1} & +& 2\\alpha \_{i-2} & ) & {U\_ x}\_ i \\\\ & + & \\frac{1}{2}( & & & \\alpha \_{i-1} & +& 4\\alpha \_{i-2} & ) & \\Delta x {U\_{xx}}\_ i \\\\ & - & \\frac{1}{6}( & & & \\alpha \_{i-1} & +& 8\\alpha \_{i-2} & ) & \\Delta x^2 {U\_{xxx}}\_ i \\\\ & + & O( & \\Delta x^3 & ) \\end{array} \\label{equ:taylorsintobwd}\\\] | (2.83) 

Since we have 3 coefficients (\\(\\alpha \_ i, \\alpha \_{i-1}, \\alpha \_{i-2}\\)), we may choose these coefficients such that the terms multiplying \\(U\_{x\_ i}\\) sum to 1, while the terms multiplying \\(\\frac{1}{\\Delta x} U\_ i\\) and \\(\\Delta x U\_{xx\_ i}\\) sum to zero. Using matrix notation:

| &nbsp; | \\(\\displaystyle \\left\[\\begin{array}{rrr} 1 & 1 & 1 \\\\ 0 & -1 & -2 \\\\ 0 & 1 & 4 \\end{array}\\right\] \\left\[\\begin{array}{c} \\alpha \_{i} \\\\ \\alpha \_{i-1} \\\\ \\alpha \_{i-2} \\end{array}\\right\] = \\left\[\\begin{array}{c} 0 \\\\ 1 \\\\ 0 \\end{array}\\right\] \\qquad \\qquad \\text {which gives}\\qquad \\qquad \\left\[\\begin{array}{c} \\alpha \_{i} \\\\ \\alpha \_{i-1} \\\\ \\alpha \_{i-2} \\end{array}\\right\] = \\left\[\\begin{array}{r} \\tfrac {3}{2} \\\\ -2 \\\\ \\tfrac {1}{2} \\end{array}\\right\].\\) | &nbsp; | (2.84) 

Thus the three-point backwards difference approximation for \\(U\_{x\_ i}\\) is equal to \\((\\frac{3}{2}U\_ i - 2U\_{i-1} + \\frac{1}{2}U\_{i-2})/\\Delta x\\). The truncation error can be found by substituting the \\(\\alpha\\)'s in Equation [2.83](javascript: void(0)) to show that,

| \\\[\\tau = \\frac{1}{\\Delta x}\\left(\\frac{3}{2}U\_ i - 2 U\_{i-1} + \\frac{1}{2}U\_{i-2}\\right) - {U\_ x}\_ i = -\\frac{1}{3}\\Delta x^2 {U\_{xxx}}\_ i + O(\\Delta x^3)\\\] | (2.85) 

Thus, this approximation for \\(U\_{x\_ i}\\) is second-order accurate. This approach can be generalized to the approximation of the \\(k-th\\) derivative,

| &nbsp; | \\(\\displaystyle \\left.\\frac{\\partial ^ k U}{\\partial x^ k}\\right&#124;\_ i\\) | \\(\\displaystyle \\approx\\) | \\(\\displaystyle \\frac{1}{(\\Delta x)^ k} \\sum \_{j \\in \\mathcal{S}} \\alpha \_ j U\_{j}\\) | &nbsp; | (2.86) 

where \\(\\alpha \_ j\\) are the coefficients for the finite difference approximation. \\(\\mathcal{S}\\) is called the stencil, and contains the list of points used in the finite difference approximation. For example the central difference approximation, \\(\\delta \_ x^2\\), has a 3-point stencil using the nodal values \\(U\_{i-1}, U\_ i\\) and \\(U\_{i+1}\\).

Exercise
--------

Give the coefficients \\((\\alpha \_{i-2}, \\alpha \_{i-1}, \\alpha \_ i)\\) of the highest-order accurate finite difference approximation for \\(U\_{xx\_ i}\\) using the 3-point stencil \\((U\_{i-2}, U\_{i-1}, U\_{i}\\)).

Exercise 1

 \\(\[1,-2,1\]\\)

 \\(\[\\frac{1}{2},-2,\\frac{3}{2}\]\\)

 \\(\[\\frac{3}{2},-2,\\frac{1}{2}\]\\)

 \\(\[1,-4,3\]\\)

CheckShow Answer

Answer: We solve the system shown above with the right hand side \\(\[0,0,1\]\\) to obtain the coefficients.

BackFinite Difference Methods in Matrix Form ContinueBoundary Conditions for Finite Differences