---
content_type: page
parent_title: 2.9 Introduction to Finite Elements
parent_uid: 876be530-ac05-3384-5428-281b2b3c5b68
title: 2.9 Introduction to Finite Elements
uid: 2f262139-b40f-5261-66c9-51230f32cd54
---

*   [<1-D Linear Elements and the Nodal Basis]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-1-d-linear-elements-and-the-nodal-basis)
*   [2.9.1Motivation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements)
*   [2.9.21-D Finite Element Mesh and Notation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-1-d-finite-element-mesh-and-notation)
*   [2.9.31-D Linear Elements and the Nodal Basis]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-1-d-linear-elements-and-the-nodal-basis)
*   [2.9.4Weak Form of the Weighted Residual]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-weak-form-of-the-weighted-residual)
*   [2.9.5Calculation of the Finite Element Weighted Residual]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-calculation-of-the-finite-element-weighted-residual)
*   [2.9.6Calculation of the Stiffness Matrix]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-calculation-of-the-stiffness-matrix)
*   [\>Calculation of the Finite Element Weighted Residual]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-calculation-of-the-finite-element-weighted-residual)

2.9.4 Weak Form of the Weighted Residual
----------------------------------------

[Measurable Outcome 2.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO212), [Measurable Outcome 2.14]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO214), [Measurable Outcome 2.15]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO215)

In this section, we will concentrate on the one-dimensional, steady diffusion equation with a source term. As previously noted in Equation ([2.149](javascript: void(0))), the one-dimensional steady diffusion equation with a source term is

| \\\[\\left(k T\_ x\\right)\_ x = -f,\\\] | (2.204) 

where \\(k(x)\\) thermal conductivity of the material and \\(f(x)\\) is the heat source (per unit length). Note that both \\(k\\) and \\(f\\) could be functions of \\(x\\). Also, let the physical domain for the problem be from \\(x=-L/2\\) to \\(x=L/2\\).

The residual corresponding to this equation is

| \\\[R(\\tilde{T},x) \\equiv \\left(k \\tilde{T}\_ x\\right)\_ x + f. \\label{equ:dif1d\_ steady\_ residual}\\\] | (2.205) 

For an arbitrary weight function, \\(w(x)\\), the weighted residual is defined as

| \\\[\\int \_{-L/2}^{L/2} w(x) R(\\tilde{T},x)\\, dx = \\int \_{-L/2}^{L/2} w \\left\[ \\left(k \\tilde{T}\_ x\\right)\_ x + f\\right\] dx.\\\] | (2.206) 

A general notation for the weighted residual is \\(r(v,w)\\), where the first entry \\(v(x)\\) is the approximate solution (\\(v(x)=\\tilde{T}(x)\\) in our example) and the second entry \\(w(x)\\) is the weight function. The finite element method (or more generally the method of weighted residuals) can be thought of as finding the \\(v(x)\\) for which \\(r(v,w)=0\\) for all of the weight functions. If the approximate solution is a linear combination of \\(M\\) functions, \\(\\phi \_ i(x)\\), then \\(v(x)\\) can be written as,

| \\\[v(x) = \\sum \_{i=1}^ Ma\_ i\\phi \_ i(x).\\\] | (2.207) 

Further, if the Galerkin method of weighted residuals is used, then the weight functions will be the set \\(\\phi \_ i(x)\\), i.e.,

| \\\[w \\in \\left\[\\phi \_1(x), \\phi \_2(x), \\ldots , \\phi \_ M(x) \\right\].\\\] | (2.208) 

Then, the Galerkin method of weighted residuals can be written as: Find the set of \\(a\_ i\\) such that \\(v(x)=\\sum \_{i=1}^ Ma\_ i\\phi \_ i(x)\\) has \\(r(v, \\phi \_ j) =0\\) for all weight functions \\(\\phi \_ j(x)\\), \\(j=1,\\ldots ,M\\).

For the diffusion equation, the weighted residual statement is usually integrated by parts so that the number of derivatives on the weight function and the approximate solution (\\(v(x)=\\tilde{T}(x)\\)) are equal. Thus, performing integration by parts gives the weighted residual for the diffusion equation as

| \\\[\\label{equ:intByParts} r(\\tilde{T}, w) = \\left\[w\\, k \\tilde{T}\_ x\\right\]^{L/2}\_{-L/2} - \\int \_{-L/2}^{L/2} w\_ x\\, k \\tilde{T}\_ x\\, dx + \\int \_{-L/2}^{L/2} w f\\, dx.\\\] | (2.209) 

The first term is on the boundaries of the domain and its use in setting boundary conditions is discussed in Section [2.10.2]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/more-on-finite-element-methods/1690r-boundary-conditions-for-finite-elements). The second and third terms are integrals over the entire domain.

The form of the weighted residual given in Equation [2.209](javascript: void(0)) is known as the **weak form** of the PDE. The residual itself is often referred to as the **strong form** of the governing equation. We see that in the weak form, the spatial derivatives of \\(\\tilde{T}\\) are of lower order than in the residual (because we integrated by parts). In the finite element method, this reduction in the order of derivatives permits the use of lower order polynomials for the functional approximation of the solution. For PDEs in which the highest order derivative is even, the weak form of the weighted residual is chosen so that the highest derivative on the weight function and the solution are the same (e.g., for a fourth-order derivative in the strong form, the weak form will have second-order derivatives on the weight function and second-order derivatives on the approximate solution).

Exercise
--------

The Euler-Bernoulli beam equation is a model for the deflection \\(w(x)\\) of a beam subjected to lateral loading, specifically

| \\\[(EIw\_{xx})\_{xx} = q(x),\\\] | (2.210) 

where \\(E\\) and \\(I\\) are the Young's modulus and the area moment of inertia, respectively, and \\(q(x)\\) is the lateral loading. Let the beam be located from \\(0 \\leq x \\leq L\\). Which of the following is the weak form with an approximate solution \\(v(x)\\) and a weight function \\(\\phi (x)\\)?

Exercise 1

&nbsp; \\(\\int \_0^ L\\phi (EIv\_{xx})\_{xx}dx + \\left\[\\phi (EIv\_{xx})\_ x - \\phi \_ xEIv\_{xx}\\right\]\_0^ L = \\int \_0^ Lq\\phi \\ dx\\) &nbsp;

&nbsp; \\(\\int \_0^ L\\phi \_{x}EIv\_{xx}dx + \\left\[\\phi (EIv\_{xx}) - \\phi \_ xEIv\_{xx}\\right\]\_0^ L = \\int \_0^ Lq\\phi \\ dx\\) &nbsp;

&nbsp; \\(\\int \_0^ L\\phi \_{xx}EIv\_{xx}dx + \\left\[\\phi (EIv\_{xx})\_ x - \\phi \_ xEIv\_{xx}\\right\]\_0^ L = \\int \_0^ Lq\\phi \\ dx\\) &nbsp;

&nbsp; \\(\\int \_0^ L\\phi \_{xx}EIv\_{xx}dx - \\left\[\\phi (EIv\_{xx})\_ x - \\phi \_ xEIv\_{xx}\\right\]\_0^ L = \\int \_0^ Lq\\phi \\ dx\\) &nbsp;

CheckShow Answer

Answer: The answer is found by multiplying both sides by \\(\\phi (x)\\) and integrating the left side by parts twice.

Back1-D Linear Elements and the Nodal Basis ContinueCalculation of the Finite Element Weighted Residual