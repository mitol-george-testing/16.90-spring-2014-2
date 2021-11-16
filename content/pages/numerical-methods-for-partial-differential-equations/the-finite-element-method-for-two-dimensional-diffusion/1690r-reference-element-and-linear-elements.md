---
content_type: page
parent_title: 2.11 The Finite Element Method for Two-Dimensional Diffusion
parent_uid: c782bcc9-abb3-f6bc-c638-027dfffdc386
title: 2.11 The Finite Element Method for Two-Dimensional Diffusion
uid: 16176028-e869-5612-f636-568d503833fc
---

*   [<The Finite Element Method for Two-Dimensional Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion)
*   [2.11.1Overview]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion)
*   [2.11.2Reference Element and Linear Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-reference-element-and-linear-elements)
*   [2.11.3Differentiation using the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-differentiation-using-the-reference-element)
*   [2.11.4Construction of the Stiffness Matrix]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-construction-of-the-stiffness-matrix)
*   [2.11.5Integration in the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-integration-in-the-reference-element)
*   [\>Differentiation using the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-differentiation-using-the-reference-element)

2.11.2 Reference Element and Linear Elements
--------------------------------------------

[Measurable Outcome 2.15]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO215), [Measurable Outcome 2.16]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO216)

In multiple dimensions, a common practice in defining the polynomial functions within an element is to transform each element into a canonical, or so-called “reference" element. Figure [2.47]({{< baseurl >}}/resources/2dreferenceelement) shows the mapping commonly used for triangular elements which maps a generic triangle in \\((x,y)\\) into a right triangle in \\((\\xi \_1, \\xi \_2)\\).

![A tilted triangle representing a polynomial function in space is shown on the left.  This triangle is rotated in multiple dimensions (x and y) to transform the triangle into a right triangle representing the reference element on the right.](BASEURL_PLACEHOLDER/resources/2dreferenceelement)

**Figure 2.47**: Transformation of a generic triangular element in \\((x,y)\\) into the reference element in \\((\\xi \_1,\\xi \_2)\\).

In the reference element space, the nodal basis for linear polynomials will be one at one of the nodes, and reduce linearly to zero at the other nodes. These functions are

| &nbsp; | \\(\\displaystyle \\phi \_1(\\xi \_1, \\xi \_2)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 1 - \\xi \_1 - \\xi \_2, \\label{equ:phi1\_2d}\\) | &nbsp; | (2.262) |
| &nbsp; | \\(\\displaystyle \\phi \_2(\\xi \_1, \\xi \_2)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\xi \_1, \\label{equ:phi2\_2d}\\) | &nbsp; | (2.263) |
| &nbsp; | \\(\\displaystyle \\phi \_3(\\xi \_1, \\xi \_2)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\xi \_2. \\label{equ:phi3\_2d}\\) | &nbsp; | (2.264) 

Then, within the element, the solution \\(\\tilde{T}\\) in the \\((\\xi \_1,\\xi \_2)\\) space is the combination of these three basis functions multiplied by the corresponding nodal coefficients,

| \\\[\\tilde{T}(\\xi \_1,\\xi \_2) = \\sum \_{j=1}^{3} a\_ j \\phi \_ j(\\xi \_1,\\xi \_2). \\label{equ:Txi}\\\] | (2.265) 

Using Equation ([2.265](javascript: void(0))), the value of \\(\\tilde{T}\\) can be found at any \\((\\xi \_1,\\xi \_2)\\). To find the \\((x,y)\\) locations in terms of the \\((\\xi \_1, \\xi \_2)\\), we can expand them using the nodal locations and the nodal basis functions, i.e.,

| \\\[\\vec{x}(\\xi \_1,\\xi \_2) = \\sum \_{j=1}^{3} \\vec{x}\_ j \\phi \_ j(\\xi \_1,\\xi \_2).\\\] | (2.266) 

Since the \\(\\phi \_ i(\\xi \_1,\\xi \_2)\\) are linear functions of \\(\\xi \_1\\) and \\(\\xi \_2\\), this amounts to a linear transformation between \\((\\xi \_1,\\xi \_2)\\) and \\((x,y)\\). Specifically, substituting the nodal basis functions gives

| &nbsp; | \\(\\displaystyle \\vec{x}(\\xi \_1,\\xi \_2)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\vec{x}\_1 \\left(1 - \\xi \_1 - \\xi \_2\\right) + \\vec{x}\_2\\xi \_1 + \\vec{x}\_3\\xi \_2,\\) | &nbsp; | (2.267) |
| &nbsp; | \\(\\displaystyle \\Rightarrow \\vec{x}(\\xi \_1,\\xi \_2)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\vec{x}\_1 + \\left(\\vec{x}\_2-\\vec{x}\_1\\right)\\xi \_1 + \\left(\\vec{x}\_3-\\vec{x}\_1\\right)\\xi \_2.\\) | &nbsp; | (2.268) 

This can be written in a matrix notation as,

| \\\[\\left(\\begin{array}{c} x \\\\ y \\end{array}\\right) = \\left(\\begin{array}{c} x\_1 \\\\ y\_1 \\end{array}\\right) + \\left(\\begin{array}{cc} x\_2-x\_1 & x\_3-x\_1 \\\\ y\_2-y\_1 & y\_3-y\_1\\end{array}\\right) \\left(\\begin{array}{c} \\xi \_1 \\\\ \\xi \_2 \\end{array}\\right) \\label{equ:xi\_ to\_ x}\\\] | (2.269) 

This equation can be inverted to also determine \\((\\xi \_1,\\xi \_2)\\) as a function of \\((x,y)\\),

| \\\[\\left(\\begin{array}{c} \\xi \_1 \\\\ \\xi \_2 \\end{array}\\right) = \\left(\\begin{array}{cc} x\_2-x\_1 & x\_3-x\_1 \\\\ y\_2-y\_1 & y\_3-y\_1\\end{array}\\right)^{-1} \\left(\\begin{array}{c} x-x\_1 \\\\ y-y\_1 \\end{array}\\right) \\label{equ:x\_ to\_ xi}\\\] | (2.270) 

BackThe Finite Element Method for Two-Dimensional Diffusion ContinueDifferentiation using the Reference Element