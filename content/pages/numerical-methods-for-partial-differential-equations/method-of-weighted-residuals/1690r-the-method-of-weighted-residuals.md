---
content_type: page
parent_title: 2.8 Method of Weighted Residuals
parent_uid: bda18124-71a5-87a7-513f-cb81480a1e18
title: 2.8 Method of Weighted Residuals
uid: 2bb791a5-f105-8421-b20e-147e46034287
---

*   [<The Collocation Method]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-the-collocation-method)
*   [2.8.1Functional Approximation of the Solution]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals)
*   [2.8.2The Collocation Method]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-the-collocation-method)
*   [2.8.3The Method of Weighted Residuals]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-the-method-of-weighted-residuals)
*   [2.8.4Galerkin Method with New Basis]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-galerkin-method-with-new-basis)
*   [\>Galerkin Method with New Basis]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals/1690r-galerkin-method-with-new-basis)

2.8.3 The Method of Weighted Residuals
--------------------------------------

[Measurable Outcome 2.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO212), [Measurable Outcome 2.13]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO213), [Measurable Outcome 2.14]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO214)

While the collocation method enforces the residual to be zero at \\(N\\) points, the method of weighted residuals requires \\(N\\) weighted integrals of the residual to be zero. A weighted residual is simply the integral over the domain of the residual multiplied by a weight function, \\(w(x)\\). For example, in the one-dimensional diffusion problem we are considering, a weighted residual is,

| \\\[\\int \_{-1}^{1} w(x)\\, R(\\tilde{T},x)\\, dx.\\\] | (2.174) 

By choosing \\(N\\) weight functions, \\(w\_ i(x)\\) for \\(i=1,\\ldots ,N\\), and setting these \\(N\\) weighted residuals to zero, we obtain \\(N\\) equations which we solve to determine the \\(N\\) unknown values of \\(a\_ j\\).

We define the weighted residual for \\(w\_ i(x)\\) to be

| \\\[R\_ i(\\tilde{T}) \\equiv \\int \_{-1}^{1} w\_ i(x)\\, R(\\tilde{T},x)\\, dx.\\\] | (2.175) 

The method of weighted residuals requires

| \\\[R\_ i(\\tilde{T}) = 0 \\qquad \\mbox{for } i=1,\\ldots ,N.\\\] | (2.176) 

In the method of weighted residuals, the next step is to determine appropriate weight functions. A common approach, known as the Galerkin method, is to set the weight functions equal to the functions used to approximate the solution. That is,

| \\\[w\_ i(x) = \\phi \_ i(x). \\quad \\mbox{(Galerkin)}.\\\] | (2.177) 

For the heat diffusion example we have been considering, this would give weight functions as

| &nbsp; | \\(\\displaystyle w\_1(x)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle (1-x)(1+x),\\) | &nbsp; | (2.178) |
| &nbsp; | \\(\\displaystyle w\_2(x)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle x(1-x)(1+x).\\) | &nbsp; | (2.179) 

Now, we must calculate the weighted residuals. For our example, we have

| &nbsp; | \\(\\displaystyle R\_1(\\tilde{T})\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\int \_{-1}^{1} w\_1(x)\\, R(\\tilde{T},x)\\, dx,\\) | &nbsp; | (2.180) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\int \_{-1}^{1} (1-x)(1+x)\\, \\left(-2 a\_1 - 6 a\_2 x + 50 e^ x\\right)\\, dx,\\) | &nbsp; | (2.181) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle -\\frac{8}{3} a\_1 + 200 e^{-1}.\\) | &nbsp; | (2.182) 

To do this integral, the following results were used:

| &nbsp; | \\(\\displaystyle \\int \_ a^ b (1-x)(1+x)\\, dx\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\left\[ x - \\frac{1}{3}x^3 \\right\]\_ a^ b,\\) | &nbsp; | (2.183) |
| &nbsp; | \\(\\displaystyle \\int \_ a^ b x(1-x)(1+x)\\, dx\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\left\[ \\frac{1}{2}x^2 - \\frac{1}{4}x^4 \\right\]\_ a^ b,\\) | &nbsp; | (2.184) |
| &nbsp; | \\(\\displaystyle \\int \_ a^ b x^2 e^ x\\, dx\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\left\[ x^2 e^ x - 2 x e^ x + 2 e^ x \\right\]\_ a^ b.\\) | &nbsp; | (2.185) 

Similarly, calculating \\(R\_2\\):

| &nbsp; | \\(\\displaystyle R\_2(\\tilde{T})\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\int \_{-1}^{1} w\_2(x)\\, R(\\tilde{T},x)\\, dx,\\) | &nbsp; | (2.186) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\int \_{-1}^{1} x(1-x)(1+x)\\, \\left(-2 a\_1 - 6 a\_2 x + 50 e^ x\\right)\\, dx,\\) | &nbsp; | (2.187) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle -\\frac{8}{5} a\_2 + 100 e^{1} - 700 e^{-1},\\) | &nbsp; | (2.188) 

where the following results have been used:

| &nbsp; | \\(\\displaystyle \\int \_ a^ b x^2(1-x)(1+x)\\, dx\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\left\[ \\frac{1}{3}x^3 - \\frac{1}{5}x^5 \\right\]\_ a^ b,\\) | &nbsp; | (2.189) |
| &nbsp; | \\(\\displaystyle \\int \_ a^ b x e^ x\\, dx\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\left\[ x e^ x - e^ x \\right\]\_ a^ b,\\) | &nbsp; | (2.190) |
| &nbsp; | \\(\\displaystyle \\int \_ a^ b x^3 e^ x\\, dx\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\left\[ x^3 e^ x - 3 x^2 e^ x + 6x e^ x - 6e^ x \\right\]\_ a^ b.\\) | &nbsp; | (2.191) 

Finally, we can solve for \\(a\_1\\) and \\(a\_2\\) by setting the weighted residuals \\(R\_1\\) and \\(R\_2\\) to zero:

| &nbsp; | \\(\\displaystyle -\\frac{8}{3} a\_1 + 200 e^{-1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0,\\) | &nbsp; | (2.192) |
| &nbsp; | \\(\\displaystyle -\\frac{8}{5} a\_2 + 100 e^{1} - 700 e^{-1}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle 0.\\) | &nbsp; | (2.193) 

This could be written as a \\(2\\times 2\\) matrix equation and solved, but the equations are decoupled and can be readily solved,

| \\\[\\Rightarrow \\left(\\begin{array}{c} a\_1 \\\\ a\_2 \\end{array}\\right) = \\left(\\begin{array}{r} 75 e^{-1} \\\\ \\frac{125}{2}e^{1} - \\frac{875}{2}e^{-1} \\end{array}\\right) = \\left(\\begin{array}{r} 27.591 \\\\ 8.945 \\end{array}\\right).\\\] | (2.194) 

The results using this method of weighted residuals are shown in the figures below. Comparison with the collocation method results shows that the method of weighted residuals is more accurate in this case.

![This graph shows two very similar lines, each with a single peak, that represent the results T and ~T for method of weighted residuals.](BASEURL_PLACEHOLDER/resources/t_mwr)

**Figure 2.30**: Comparison of \\(T\\) (solid) and \\(\\tilde{T}\\) (dashed) for method of weighted residuals.

![This graph has one line, representing the error T minus ~T for method of weighted residuals.  The line begins at the y-axis point zero, then decreases below -0.3, increases above 0.4, then decreases to almost -0.4, and finally increases back to zero.](BASEURL_PLACEHOLDER/resources/e_mwr)

**Figure 2.31**: Error \\(\\tilde{T}-T\\) for method of weighted residuals.

![This graph of the residual R(~T, x) for method of weighted resiuduals has a single line that steadily decreases and then increases.](BASEURL_PLACEHOLDER/resources/r_mwr)

**Figure 2.32**: Residual \\(R(\\tilde{T},x)\\) for method of weighted residuals.

BackThe Collocation Method ContinueGalerkin Method with New Basis