---
content_type: page
parent_title: 'Unit 2: Numerical Methods for Partial Differential Equations'
parent_uid: 125c58ac-6a34-5a7c-bba8-de2d3160cb8b
title: 2.11 The Finite Element Method for Two-Dimensional Diffusion
uid: c782bcc9-abb3-f6bc-c638-027dfffdc386
---

*   [<Boundary Conditions for Finite Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/more-on-finite-element-methods/1690r-boundary-conditions-for-finite-elements)
*   [2.11.1Overview]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion)
*   [2.11.2Reference Element and Linear Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-reference-element-and-linear-elements)
*   [2.11.3Differentiation using the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-differentiation-using-the-reference-element)
*   [2.11.4Construction of the Stiffness Matrix]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-construction-of-the-stiffness-matrix)
*   [2.11.5Integration in the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-integration-in-the-reference-element)
*   [\>Reference Element and Linear Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-reference-element-and-linear-elements)

2.11.1 Overview
---------------

In this lecture, we will consider the finite element approximation of the two-dimensional diffusion problem,

| \\\[\\nabla \\cdot \\left(k \\nabla T\\right) + f = 0. \\label{equ:dif2d}\\\] | (2.259) 

As in the previous discussion of the method of weighted residuals and the finite element method, the approximate solution will have the form

| \\\[\\tilde{T}(x,y) = \\sum \_{j=1}^{N} a\_ j \\phi \_ j(x,y),\\\] | (2.260) 

where \\(\\phi \_ j(x,y)\\) are the known basis functions and the \\(a\_ j\\) are the unknown coefficients to be determined for the specific problem. Following the Galerkin method of weighted residuals, we will weight Equation ([2.259](javascript: void(0))) by one of the basis functions and integrate the diffusion term by parts to give the following weighted residual:

| \\\[R\_ i \\equiv \\int \_{\\delta \\Omega } \\phi \_ i\\, k\\nabla \\tilde{T}\\cdot \\vec{n}\\, ds - \\int \_{\\Omega } \\nabla \\phi \_ i \\cdot \\left(k\\nabla \\tilde{T}\\right)\\, dA + \\int \_{\\Omega } \\phi \_ i f\\, dA = 0. \\label{equ:mwr\_ dif2d}\\\] | (2.261) 

BackBoundary Conditions for Finite Elements ContinueReference Element and Linear Elements