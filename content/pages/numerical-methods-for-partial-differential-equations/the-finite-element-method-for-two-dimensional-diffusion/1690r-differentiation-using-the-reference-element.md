---
content_type: page
parent_title: 2.11 The Finite Element Method for Two-Dimensional Diffusion
parent_uid: c782bcc9-abb3-f6bc-c638-027dfffdc386
title: 2.11 The Finite Element Method for Two-Dimensional Diffusion
uid: 6075ecc5-d133-cbcb-277c-06977e6970ea
---

*   [<Reference Element and Linear Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-reference-element-and-linear-elements)
*   [2.11.1Overview]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion)
*   [2.11.2Reference Element and Linear Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-reference-element-and-linear-elements)
*   [2.11.3Differentiation using the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-differentiation-using-the-reference-element)
*   [2.11.4Construction of the Stiffness Matrix]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-construction-of-the-stiffness-matrix)
*   [2.11.5Integration in the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-integration-in-the-reference-element)
*   [\>Construction of the Stiffness Matrix]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-construction-of-the-stiffness-matrix)

2.11.3 Differentiation using the Reference Element
--------------------------------------------------

[Measurable Outcome 2.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO217)

To find the derivative of \\(\\tilde{T}\\) with respect to \\(x\\) (or similarly \\(y\\)) within an element, we differentiate the three nodal basis functions within the element:

| &nbsp; | \\(\\displaystyle \\tilde{T}\_ x\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{\\partial }{\\partial x}\\left(\\sum \_{j=1}^{3} a\_ j\\phi \_ j\\right),\\) | &nbsp; | (2.271) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\sum \_{j=1}^{3} a\_ j\\frac{\\partial \\phi \_ j}{\\partial x}.\\) | &nbsp; | (2.272) 

To find the \\(x\\)-derivatives of each of the \\(\\phi \_ j\\)'s, the chain rule is applied:

| \\\[\\frac{\\partial \\phi \_ j}{\\partial x} = \\frac{\\partial \\phi \_ j}{\\partial \\xi \_1}\\frac{\\partial \\xi \_1}{\\partial x} + \\frac{\\partial \\phi \_ j}{\\partial \\xi \_2}\\frac{\\partial \\xi \_2}{\\partial x}.\\\] | (2.273) 

Similarly, to find the derivatives with respect to \\(y\\):

| \\\[\\frac{\\partial \\phi \_ j}{\\partial y} = \\frac{\\partial \\phi \_ j}{\\partial \\xi \_1}\\frac{\\partial \\xi \_1}{\\partial y} + \\frac{\\partial \\phi \_ j}{\\partial \\xi \_2}\\frac{\\partial \\xi \_2}{\\partial y}.\\\] | (2.274) 

The calculation of the derivatives of \\(\\phi \_ j\\) with respect to the \\(\\xi\\) variables gives:

| &nbsp; | \\(\\displaystyle \\frac{\\partial \\phi \_1}{\\partial \\xi \_1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle -1, \\qquad \\frac{\\partial \\phi \_1}{\\partial \\xi \_2} = -1,\\) | &nbsp; | (2.275) |
| &nbsp; | \\(\\displaystyle \\frac{\\partial \\phi \_2}{\\partial \\xi \_1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 1, \\qquad \\frac{\\partial \\phi \_2}{\\partial \\xi \_2} = 0,\\) | &nbsp; | (2.276) |
| &nbsp; | \\(\\displaystyle \\frac{\\partial \\phi \_3}{\\partial \\xi \_1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0, \\qquad \\frac{\\partial \\phi \_3}{\\partial \\xi \_2} = 1.\\) | &nbsp; | (2.277) 

The only remaining terms are the calculation of \\(\\frac{\\partial \\xi \_1}{\\partial x}\\), \\(\\frac{\\partial \\xi \_2}{\\partial x}\\), etc. which can be found by differentiating Equation ([2.270](javascript: void(0))),

| &nbsp; | \\(\\displaystyle \\frac{\\partial \\vec{\\xi }}{\\partial \\vec{x}}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\left(\\begin{array}{cc} x\_2-x\_1 & x\_3-x\_1 \\\\ y\_2-y\_1 & y\_3-y\_1\\end{array}\\right)^{-1},\\) | &nbsp; | (2.278) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{1}{J} \\left(\\begin{array}{cc} y\_3-y\_1 & -(x\_3-x\_1) \\\\ -(y\_2-y\_1) & x\_2-x\_1\\end{array}\\right),\\) | &nbsp; | (2.279) 

where

| \\\[J = (x\_2-x\_1)(y\_3-y\_1) - (x\_3-x\_1)(y\_2-y\_1).\\\] | (2.280) 

Note that the Jacobian, \\(J\\), is equal to twice the area of the triangular element.

BackReference Element and Linear Elements ContinueConstruction of the Stiffness Matrix