---
content_type: page
parent_title: 2.9 Introduction to Finite Elements
parent_uid: 876be530-ac05-3384-5428-281b2b3c5b68
title: 2.9 Introduction to Finite Elements
uid: c369789e-d0c6-3741-858a-5dcba10708e4
---

*   [<Weak Form of the Weighted Residual]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-weak-form-of-the-weighted-residual)
*   [2.9.1Motivation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements)
*   [2.9.21-D Finite Element Mesh and Notation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-1-d-finite-element-mesh-and-notation)
*   [2.9.31-D Linear Elements and the Nodal Basis]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-1-d-linear-elements-and-the-nodal-basis)
*   [2.9.4Weak Form of the Weighted Residual]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-weak-form-of-the-weighted-residual)
*   [2.9.5Calculation of the Finite Element Weighted Residual]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-calculation-of-the-finite-element-weighted-residual)
*   [2.9.6Calculation of the Stiffness Matrix]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-calculation-of-the-stiffness-matrix)
*   [\>Calculation of the Stiffness Matrix]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-calculation-of-the-stiffness-matrix)

2.9.5 Calculation of the Finite Element Weighted Residual
---------------------------------------------------------

[Measurable Outcome 2.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO212), [Measurable Outcome 2.14]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO214), [Measurable Outcome 2.15]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO215), [Measurable Outcome 2.16]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO216), [Measurable Outcome 2.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO217), [Measurable Outcome 2.20]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO220)

The implementation of the finite element method requires finding the weak form of the residual for each weight function \\(\\phi \_ j(x)\\). For the diffusion problem the \\(j^{th}\\) weighted residual is

| \\\[r(\\tilde{T}, \\phi \_ j) \\equiv \\left\[\\phi \_ j\\, k \\tilde{T}\_ x\\right\]^{L/2}\_{-L/2} - \\int \_{-L/2}^{L/2} {\\phi \_ j}\_ x\\, k \\tilde{T}\_ x\\, dx + \\int \_{-L/2}^{L/2} \\phi \_ j f\\, dx. \\label{equ:Rj\_ dif1d}\\\] | (2.211) 

We will consider the evaluation of the term \\(\\int \_{-L/2}^{L/2} \\phi \_{j\_ x}k\\tilde{T}\_{x} dx\\) below. The approximation of \\(\\int \_{-L/2}^{L/2} \\phi \_{j\_ x} f dx\\) will be discussed in Section [2.10.1]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/more-on-finite-element-methods); for now, we assume that this integral can be calculated analytically. For now, consider the term \\(\\int \_{-L/2}^{L/2} {\\phi \_ j}\_ x\\, k \\tilde{T}\_ x\\, dx\\). While it is a global integral (i.e., an integral over the entire domain), in reality \\(\\phi \_ j(x)\\) is non-zero only over the two elements that include node \\(j\\):

| \\\[\\Rightarrow \\int \_{-L/2}^{L/2} {\\phi \_ j}\_ x\\, k \\tilde{T}\_ x\\, dx = \\int \_{x\_{j-1}}^{x\_{j+1}} {\\phi \_ j}\_ x\\, k \\tilde{T}\_ x\\, dx.\\\] | (2.212) 

The derivative of basis function \\(j\\) is

| \\\[{\\phi \_ j}\_ x(x) = \\left\\{ \\begin{array}{cl} 0, & \\mbox{for } x < x\_{j-1}, \\\\\[0.1in\] \\frac{1}{\\Delta x\_{j-1}}, & \\mbox{for } x\_{j-1} < x < x\_{j},\\\\\[0.1in\] \\frac{-1}{\\Delta x\_{j}}, & \\mbox{for } x\_{j} < x < x\_{j+1},\\\\\[0.1in\] 0, & \\mbox{for } x > x\_{j+1}. \\end{array}\\right. \\label{equ:phi\_ x\_ linear}\\\] | (2.213) 

Thus,

| \\\[\\int \_{x\_{j-1}}^{x\_{j+1}} {\\phi \_ j}\_ x\\, k \\tilde{T}\_ x\\, dx = \\frac{1}{\\Delta x\_{j-1}} \\int \_{x\_{j-1}}^{x\_{j }} k \\tilde{T}\_ x\\, dx - \\frac{1}{\\Delta x\_{j }} \\int \_{x\_{j }}^{x\_{j+1}} k \\tilde{T}\_ x\\, dx.\\\] | (2.214) 

Next, take the derivative of \\(\\tilde{T}\\):

| \\\[\\tilde{T}\_ x(x) = \\sum \_{i=1}^{N+1} a\_ i {\\phi \_ i}\_ x(x).\\\] | (2.215) 

For the integral in element \\(j-1\\), the only non-zero contributions to \\(\\tilde{T}\_ x\\) are from \\(\\phi \_{j-1}\\) and \\(\\phi \_{j}\\), specifically,

| \\\[\\mbox{In element }j-1: \\qquad \\tilde{T}\_ x = a\_{j-1}{\\phi \_{j-1}}\_ x + a\_{j}{\\phi \_{i}}\_ x = \\frac{a\_ j - a\_{j-1}}{\\Delta x\_{j-1}}.\\\] | (2.216) 

Similarly,

| \\\[\\mbox{In element }j: \\qquad \\tilde{T}\_ x = a\_{j}{\\phi \_{j}}\_ x + a\_{j+1}{\\phi \_{j+1}}\_ x = \\frac{a\_{j+1}-a\_ j}{\\Delta x\_{j}}.\\\] | (2.217) 

Substituting these expressions for the derivatives into the integral gives

| \\\[\\int \_{x\_{j-1}}^{x\_{j+1}} {\\phi \_ j}\_ x\\, k \\tilde{T}\_ x\\, dx = \\frac{a\_{j}-a\_{j-1}}{(\\Delta x\_{j-1})^2} \\int \_{x\_{j-1}}^{x\_{j }} k \\, dx - \\frac{a\_{j+1}-a\_{j}}{(\\Delta x\_{j })^2} \\int \_{x\_{j }}^{x\_{j+1}} k \\, dx.\\\] | (2.218) 

At this point, we must integrate \\(k(x)\\) in each element. Efficient numerical methods to approximate this integral are discussed in Section [2.10.1]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/more-on-finite-element-methods). For the situation in which \\(k\\) is constant throughout the domain the integral reduces to the following expression.

| \\\[\\mbox{For }k = \\mbox{constant}: \\qquad \\int \_{x\_{j-1}}^{x\_{j+1}} {\\phi \_ j}\_ x\\, k \\tilde{T}\_ x\\, dx = k\\frac{a\_{j}-a\_{j-1}}{\\Delta x\_{j-1}}- k\\frac{a\_{j+1}-a\_{j}}{\\Delta x\_{j }}.\\\] | (2.219) 

Exercise
--------

For constant spacing \\(\\Delta x\\), what does the integral \\(\\int \_{x\_{j-1}}^{x\_{j+1}} {\\phi \_ j}\_ x\\, \\tilde{T}\_ x\\, dx\\) equal?

Exercise 1

 \\(k\\frac{-a\_{j-1} - a\_{j+1}}{\\Delta x}\\)

 \\(k\\frac{-a\_{j-1} + 2a\_ j - a\_{j+1}}{\\Delta x}\\)

 \\(k\\frac{-a\_{j-1} - a\_{j+1}}{2\\Delta x}\\)

 \\(k\\frac{ a\_{j-1} + 2a\_ j + a\_{j+1}}{\\Delta x}\\)

CheckShow Answer

Answer: Setting \\(\\Delta x\_{j-1} = \\Delta x\_{j+1} = \\Delta x\\), we get the same approximation for the second derivative that we saw in the section of finite differences. Is that a coincidence?

BackWeak Form of the Weighted Residual ContinueCalculation of the Stiffness Matrix