---
content_type: page
parent_title: 'Unit 1: Numerical Integration of Ordinary Differential Equations'
parent_uid: 5cae4847-c59a-a247-c767-3c0c6b0abef1
title: 1.8 Multi-Step Methods
uid: 67717326-dffb-7444-5162-101fd9a9ec91
---

*   [<Apply Newton-Rhapson]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-apply-newton-rhapson)
*   [1.8.1Adams-Bashforth Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods)
*   [1.8.2Adams-Moulton Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-adams-moulton-methods)
*   [1.8.3Backwards Differentiation Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-methods)
*   [1.8.4Backwards Differentiation Excercise]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-excercise)
*   [\>Adams-Moulton Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-adams-moulton-methods)

1.8.1 Adams-Bashforth Methods
-----------------------------

[Measurable Outcome 1.15]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO115), [Measurable Outcome 1.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO117), [Measurable Outcome 1.18]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO118), [Measurable Outcome 1.19]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO119)

Adams-Bashforth methods are explicit methods of the form,

| \\\[v^{n+1} - v^{n} = {\\Delta t}\\sum \_{i=1}^ s \\beta \_ i f^{n+1-i}.\\\] | (1.136) 

Thus, the basic time derivative approximation remains the same for all \\(p\\) (i.e. \\(du/dt\\) is approximated by \\((v^{n+1} - v^ n)/Dt\\)) and the higher-order accuracy is achieved by using more values of \\(f\\).

|  {{< br >}}{{< br >}} \\(p\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\beta \_1\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\beta \_2\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\beta \_3\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\beta \_4\\) {{< br >}}{{< br >}}  |
|  {{< br >}}{{< br >}} 1 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} 1 {{< br >}}{{< br >}}  | &nbsp; |
|  {{< br >}}{{< br >}} 2 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{3}{2}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{1}{2}\\) {{< br >}}{{< br >}}  | &nbsp; |
|  {{< br >}}{{< br >}} 3 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{23}{12}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{16}{12}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{5}{12}\\) {{< br >}}{{< br >}}  | &nbsp; |
|  {{< br >}}{{< br >}} 4 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{55}{24}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{59}{24}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{37}{24}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{9}{24}\\) {{< br >}}{{< br >}}  

**Table 2**: Coefficients for Adams-Bashforth methods (these methods are explicit so \\(\\beta \_0 = 0\\)). Note: the \\(p=1\\) method is the forward Euler method.

The coefficients for the first through fourth order methods are given in the table above. The first-order Adams-Bashforth is forward Euler.

![The graph shows the shrinking, but all overlapping, Adams-Bashforth stability regions for p=1 through p=4 methods.](BASEURL_PLACEHOLDER/resources/ab_stab)

**Figure 1.19**: Adams-Bashforth stability regions for \\(p=1\\) through \\(p=4\\) methods. Note: interior of contours is stable region.

The stability boundary for these methods are shown in Figure [1.19]({{< baseurl >}}/resources/ab_stab). As the order of accuracy increases, the stability regions become smaller. Note, this is the opposite of Runge-Kutta methods for which the size of the stability regions increases with increased accuracy (see Section [1.9]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/runge-kutta-methods)).

BackApply Newton-Rhapson ContinueAdams-Moulton Methods