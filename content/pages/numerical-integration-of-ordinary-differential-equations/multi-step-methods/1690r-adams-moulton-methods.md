---
content_type: page
parent_title: 1.8 Multi-Step Methods
parent_uid: 67717326-dffb-7444-5162-101fd9a9ec91
title: 1.8 Multi-Step Methods
uid: 75e73977-a306-f553-2134-b4e0a24fdb81
---

*   [<Multi-Step Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods)
*   [1.8.1Adams-Bashforth Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods)
*   [1.8.2Adams-Moulton Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-adams-moulton-methods)
*   [1.8.3Backwards Differentiation Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-methods)
*   [1.8.4Backwards Differentiation Excercise]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-excercise)
*   [\>Backwards Differentiation Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-methods)

1.8.2 Adams-Moulton Methods
---------------------------

[Measurable Outcome 1.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO112), [Measurable Outcome 1.15]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO115), [Measurable Outcome 1.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO117), [Measurable Outcome 1.18]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO118), [Measurable Outcome 1.19]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO119)

Adams-Moulton methods are implicit methods of the form,

| \\\[v^{n+1} - v^{n} = {\\Delta t}\\sum \_{i=0}^ s \\beta \_ i f^{n+1-i}.\\\] | (1.137) 

These methods use the same time derivative approximation as the Adams-Bashforth methods, however they include the \\(n+1\\) value of \\(f\\).

|  {{< br >}}{{< br >}} \\(p\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\beta \_0\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\beta \_1\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\beta \_2\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\beta \_3\\) {{< br >}}{{< br >}}  |
|  {{< br >}}{{< br >}} 1 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} 1 {{< br >}}{{< br >}}  | &nbsp; |
|  {{< br >}}{{< br >}} 2 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{1}{2}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{1}{2}\\) {{< br >}}{{< br >}}  | &nbsp; |
|  {{< br >}}{{< br >}} 3 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{5}{12}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{8}{12}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{1}{12}\\) {{< br >}}{{< br >}}  | &nbsp; |
|  {{< br >}}{{< br >}} 4 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{9}{24}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{19}{24}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{5}{24}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{1}{24}\\) {{< br >}}{{< br >}}  

**Table 3**: Coefficients for Adams-Moulton methods. Note: the \\(p=1\\) method is the backward Euler method, and the \\(p=2\\) method is the Trapezoidal method.

The coefficients for the first through fourth order methods are given in the table above.

![The graph shows the shrinking, mostly non-overlapping, Adams-Moulton stability regions for p=1 through p=4 methods.](BASEURL_PLACEHOLDER/resources/am_stab)

**Figure 1.20**: Adams-Moulton stability regions for \\(p=1\\) through \\(p=4\\) methods. Note: \\(p=1\\) is stable outside of contour, the \\(p=2\\) integrator is stable in the left-half plane, and \\(p\\geq 3\\) are stable inside their respective contours.

The stability boundary for these methods are shown in Figure [1.20]({{< baseurl >}}/resources/am_stab). While the stability regions are larger than the Adams-Bashforth methods, for \\(p>2\\) the methods have bounded stability regions. Thus, they will not be appropriate for stiff problems.

BackMulti-Step Methods ContinueBackwards Differentiation Methods