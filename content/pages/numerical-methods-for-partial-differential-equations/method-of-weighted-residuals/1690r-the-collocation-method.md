---
content_type: page
parent_title: 2.8 Method of Weighted Residuals
parent_uid: bda18124-71a5-87a7-513f-cb81480a1e18
title: 2.8 Method of Weighted Residuals
uid: 06f65fc2-70a3-d410-b331-d186ad67852a
---

*   [<Method of Weighted Residuals]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals)
*   [2.8.1Functional Approximation of the Solution]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals)
*   [2.8.2The Collocation Method]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-the-collocation-method)
*   [2.8.3The Method of Weighted Residuals]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-the-method-of-weighted-residuals)
*   [2.8.4Galerkin Method with New Basis]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-galerkin-method-with-new-basis)
*   [\>The Method of Weighted Residuals]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-the-method-of-weighted-residuals)

2.8.2 The Collocation Method
----------------------------

[Measurable Outcome 2.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO212), [Measurable Outcome 2.13]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO213) 

One approach to determine the \\(N\\) unknown values of \\(a\_ j\\) would be to enforce the governing PDE at \\(N\\) spatial points in the domain (i.e., to make sure that the the approximate solution exactly satisfies the PDE at \\(N\\) points). Note that in general, the exact solution will not be a linear combination of the \\(\\phi \_ j(x)\\), so it will not be possible for our approximate solution to satisfy the PDE at every point in the domain. To see this, let's substitute our approximate solution \\(\\tilde{T}(x)= 100 + a\_1 \\phi \_1(x) + a\_2 \\phi \_2(x)\\) into Equation  [2.149](javascript: void(0)). First, let's derive an expression for \\(\\tilde{T}\_{xx}\\):

| &nbsp; | \\(\\displaystyle \\tilde{T}\_{xx}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{\\partial ^2}{\\partial x^2}\\left\[a\_1 \\phi \_1(x) + a\_2 \\phi \_2(x)\\right\],\\) | &nbsp; | (2.162) |
| &nbsp; | \\(\\displaystyle (\\phi \_1)\_{xx}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle -2,\\) | &nbsp; | (2.163) |
| &nbsp; | \\(\\displaystyle (\\phi \_2)\_{xx}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle -6x,\\) | &nbsp; | (2.164) |
| &nbsp; | \\(\\displaystyle \\Rightarrow \\tilde{T}\_{xx}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle -2 a\_1 - 6 a\_2 x.\\) | &nbsp; | (2.165) 

Next, we define a residual for Equation  [2.149](javascript: void(0)),

| \\\[R(\\tilde{T},x) \\equiv \\left(k \\tilde{T}\_ x\\right)\_ x + f.\\\] | (2.166) 

The residual tells us by how much the approximate solution does not satisfy the governing PDE. If the solution \\(\\tilde{T}\\) were exact, then \\(R = 0\\) for all \\(x\\). Now, substitution of our chosen \\(\\tilde{T}\\) into the residual (recall \\(k=1\\) and \\(f=50 e^ x\\) in this example) gives

| \\\[R(\\tilde{T},x) = -2 a\_1 - 6 a\_2 x + 50 e^ x. \\label{equ:steady\_ dif1d\_ residual}\\\] | (2.167) 

Clearly, since \\(a\_1\\) and \\(a\_2\\) are constants (i.e., they do not depend on \\(x\\)), there is no way for this residual to be zero for all \\(x\\).

By setting the residual to be zero at \\(N\\) different points \\(x\\), we will obtain \\(N\\) equations that we can solve to determine the \\(N\\) unknown coefficients. The question remains, where should the \\(N\\) points be selected? The points at which the governing equation will be enforced are known as the collocation points. For our example with \\(N=2\\) , we will choose the relatively simple approach of equally subdividing the domain with \\(N=2\\) interior collocation points. For this domain from \\(-1 \\leq x \\leq 1\\), the equi-distant collocation points would be at \\(x = \\pm 1/3\\). Thus, the two conditions for determining \\(a\_1\\) and \\(a\_2\\) are,

| &nbsp; | \\(\\displaystyle R(\\tilde{T},-1/3)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0,\\) | &nbsp; | (2.168) |
| &nbsp; | \\(\\displaystyle R(\\tilde{T},1/3)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0.\\) | &nbsp; | (2.169) 

From Equation  [2.167](javascript: void(0)) this gives,

| &nbsp; | \\(\\displaystyle -2 a\_1 + 2 a\_2 + 50 e^{-1/3}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0,\\) | &nbsp; | (2.170) |
| &nbsp; | \\(\\displaystyle -2 a\_1 - 2 a\_2 + 50 e^{1/3}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0.\\) | &nbsp; | (2.171) 

Re-arranging this into a matrix form gives,

| \\\[\\left(\\begin{array}{rr} -2 & 2 \\\\ -2 & -2 \\end{array}\\right) \\left(\\begin{array}{c} a\_1 \\\\ a\_2 \\end{array}\\right) = \\left(\\begin{array}{l} -50 e^{-1/3} \\\\ -50 e^{1/3} \\end{array}\\right).\\\] | (2.172) | \\\[\\Rightarrow \\left(\\begin{array}{c} a\_1 \\\\ a\_2 \\end{array}\\right) = \\left(\\begin{array}{l} 25 \\cosh (1/3) \\\\ 25 \\sinh (1/3) \\end{array}\\right) = \\left(\\begin{array}{r} 26.402 \\\\ 8.489 \\end{array}\\right).\\\] | (2.173) 

The results using this collocation method are shown in the figures below which include plots of \\(\\tilde{T}(x)\\), the error (i.e., \\(\\tilde{T}(x)-T(x)\\)), and the residual. Note that the residual is exactly zero at the collocation points (i.e., \\(x = \\pm 1/3\\)), though the approximation is not exact at these points (i.e., \\(\\tilde{T} \\neq T\\) at \\(x = \\pm 1/3\\)). This is because the residual \\(R(\\tilde{T},x)\\) measures a different thing to the error \\(\\tilde{T}(x)-T(x)\\). Remember, the residual tells us by how much the PDE is not satisfied at a given point, so it relates to the balance between the terms in the PDE (in our case between the term \\(\\left(k \\tilde{T}\_ x\\right)\_ x\\) and the heat source term \\(f(x)\\)). Even if the PDE is satisfied at a particular point (i.e., the residual is zero at that point), the solution might not be exact at that point.

![This graph shows two very similar lines, each with a single peak, that represent the results T and ~T using the collocation method.](BASEURL_PLACEHOLDER/resources/t_collocation)

**Figure 2.27**: Comparison of \\(T\\) (solid) and \\(\\tilde{T}\\) (dashed) for collocation method.

![This graph has one line, representing the error T minus ~T for collocation method.  The line begins at the y-axis point zero, then decreases below -0.8, increases slightly above -0.8, decreases to almost -1.2, and finally increases back to zero.](BASEURL_PLACEHOLDER/resources/e_collocation)

**Figure 2.28**: Error \\(\\tilde{T}-T\\) for collocation method.

![This graph of the residual R(~T, x) has a single line that steadily decreases and then increases.](BASEURL_PLACEHOLDER/resources/r_collocation)

**Figure 2.29**: Residual \\(R(\\tilde{T},x)\\) for collocation method.

BackMethod of Weighted Residuals ContinueThe Method of Weighted Residuals