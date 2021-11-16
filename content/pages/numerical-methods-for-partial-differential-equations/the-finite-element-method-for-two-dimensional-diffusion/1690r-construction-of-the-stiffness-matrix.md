---
content_type: page
parent_title: 2.11 The Finite Element Method for Two-Dimensional Diffusion
parent_uid: c782bcc9-abb3-f6bc-c638-027dfffdc386
title: 2.11 The Finite Element Method for Two-Dimensional Diffusion
uid: d29ce1ed-3626-60b8-be9b-f2741bbc6ee9
---

*   [<Differentiation using the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-differentiation-using-the-reference-element)
*   [2.11.1Overview]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion)
*   [2.11.2Reference Element and Linear Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-reference-element-and-linear-elements)
*   [2.11.3Differentiation using the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-differentiation-using-the-reference-element)
*   [2.11.4Construction of the Stiffness Matrix]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-construction-of-the-stiffness-matrix)
*   [2.11.5Integration in the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-integration-in-the-reference-element)
*   [\>Integration in the Reference Element]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-integration-in-the-reference-element)

2.11.4 Construction of the Stiffness Matrix
-------------------------------------------

[Measurable Outcome 2.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO217), [Measurable Outcome 2.20]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO220)

The stiffness matrix arises in the calculation of \\(\\int \_{\\Omega } \\nabla \\phi \_ i \\cdot \\left(k\\nabla \\tilde{T}\\right)\\, dA\\). As in the one-dimensional case, the \\(i\\)-th row of the stiffness matrix \\(K\\) corresponds to the weighted residual of \\(\\phi \_ i\\). The \\(j\\)-th column in the \\(i\\)-th row corresponds to the dependence of the \\(i\\)-th weighted residual on \\(a\_ j\\). Further drawing on the one-dimensional example, the weighted residuals are assembled by calculating the contribution to all of the residuals from within a single element. In the two-dimensional linear element situation, three weighted residuals are impacted by a given element, specifically, the weighted residuals corresponding to the nodal basis functions of the three nodes of the triangle. For example, in each element we must calculate

| \\\[\\int \_{\\Omega \_ e} \\nabla \\phi \_1 \\cdot \\left(k\\nabla \\tilde{T}\\right)\\, dA, \\qquad \\int \_{\\Omega \_ e} \\nabla \\phi \_2 \\cdot \\left(k\\nabla \\tilde{T}\\right)\\, dA, \\qquad \\int \_{\\Omega \_ e} \\nabla \\phi \_3 \\cdot \\left(k\\nabla \\tilde{T}\\right)\\, dA,\\\] | (2.281) 

where \\(\\Omega \_ e\\) is spatial domain for a specific element. As described in Section [2.11.3]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion/1690r-differentiation-using-the-reference-element), the gradient of \\(\\tilde{T}\\) can be written,

| \\\[\\nabla \\tilde{T}(x,y)= \\sum \_{j=1}^{3} a\_ j\\nabla \\phi \_ j(x,y),\\\] | (2.282) 

thus the weighted residuals expand to,

| \\\[\\int \_{\\Omega } \\nabla \\phi \_ i \\cdot \\left(k\\nabla \\tilde{T}\\right)\\, dA = \\sum \_{j=1}^{3} a\_ j K\_{i,j}, \\qquad \\mbox{where } \\qquad K\_{i,j} \\equiv \\int \_{\\Omega } \\nabla \\phi \_ i \\cdot \\left(k\\nabla \\phi \_ j\\right)\\, dA.\\\] | (2.283) 

For the situation in which \\(k\\) is constant and linear elements are used, then this reduces to

| \\\[K\_{i,j} \\equiv k \\nabla \\phi \_ i \\cdot \\nabla \\phi \_ j A\_ e,\\\] | (2.284) 

where \\(A\_ e\\) is the area of element \\(e\\).

BackDifferentiation using the Reference Element ContinueIntegration in the Reference Element