---
content_type: page
parent_title: 'Unit 1: Numerical Integration of Ordinary Differential Equations'
parent_uid: 5cae4847-c59a-a247-c767-3c0c6b0abef1
title: 1.3 Order of Accuracy
uid: a3fbfbbd-e140-393b-aed5-af945a9316f9
---

*   [<The Midpoint Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/discretizing-odes/1690r-the-midpoint-method)
*   [1.3.1Errors]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy)
*   [1.3.2Local Truncation Error]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-local-truncation-error)
*   [1.3.3Local Order of Accuracy]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-local-order-of-accuracy)
*   [1.3.4Definition of Multi-Step Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-definition-of-multi-step-methods)
*   [1.3.5Example of Most Accurate Multi-Step Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-example-of-most-accurate-multi-step-method)
*   [\>Local Truncation Error]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-local-truncation-error)

1.3.1 Errors
------------

[Measurable Outcome 1.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO15)

There are two sources of error when we solve an ODE with a numerical method. The first is _rounding error_, due to the finite precision of floating-point arithmetic. The second is _truncation error_ (sometimes called discretization error), due to the method used. The truncation error would remain even if we were to use exact arithmetic. We will be concerned with truncation error, which is typically the dominant error source for our problems of interest. We will further define two types of truncation error: the _global error_ is the difference between the computed solution at \\(t^ n\\) and the true solution of the ODE at \\(t^ n\\), while the _local error_ is the error made in one step of the numerical method, i.e. the difference between the computed solution at \\(t^ n\\) and the solution of the ODE passing through the previous point \\((t^{n-1},v^{n-1})\\). We defer the global error to Section [1.4.2]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/convergence/1690r-convergence-of-numerical-methods) and will investigate the local error here.

BackThe Midpoint Method ContinueLocal Truncation Error