---
content_type: page
parent_title: 1.3 Order of Accuracy
parent_uid: a3fbfbbd-e140-393b-aed5-af945a9316f9
title: 1.3 Order of Accuracy
uid: 6121a3ca-d8f1-c652-7821-6a952ea8ff2c
---

*   [<Order of Accuracy]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy)
*   [1.3.1Errors]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy)
*   [1.3.2Local Truncation Error]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-local-truncation-error)
*   [1.3.3Local Order of Accuracy]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-local-order-of-accuracy)
*   [1.3.4Definition of Multi-Step Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-definition-of-multi-step-methods)
*   [1.3.5Example of Most Accurate Multi-Step Method]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-example-of-most-accurate-multi-step-method)
*   [\>Local Order of Accuracy]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-local-order-of-accuracy)

1.3.2 Local Truncation Error
----------------------------

[Measurable Outcome 1.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO15)

Global error measures the difference between the computed solution at a given time and the true solution of the initial value problem that we are trying to solve. Local error is the error made in one step of the numerical method. While we are generally interested in obtaining small global errors, local errors are the errors over which we have direct control. Both global and local accuracy are related to the behavior of the error as \\({\\Delta t}\\rightarrow 0\\). Convergence is related to global accuracy; for local accuracy we will see in [1.5.1]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/zero-stability-and-the-dahlquist-equivalence-theorem) an important concept known as consistency.

If we can quantify how much the error changes in a single timestep, then we will have an indication of how much the error could change over a series of timesteps. Specifically, let's write the solution error, \\(e\\), at \\(t=T\\) as a sum of the change in error at each timestep,

| \\\[e(T) = u(T) - v^{T/{\\Delta t}} = \\sum \_{n=1}^{T/{\\Delta t}} \\Delta e^ n,\\\] | (1.35) 

where \\(\\Delta e^ n\\) is the change in the error from iteration \\(n-1\\) to \\(n\\) (i.e. the local error). Suppose the local error is \\(O({\\Delta t}^{p+1})\\), then the global error might be expected to behave as,

| &nbsp; | \\(\\displaystyle e(T)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\sum \_{n=1}^{T/{\\Delta t}} \\Delta e^ n,\\) | &nbsp; | (1.36) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\sum \_{n=1}^{T/{\\Delta t}} O({\\Delta t}^{p+1}),\\) | &nbsp; | (1.37) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{T}{{\\Delta t}} O({\\Delta t}^{p+1})\\) | &nbsp; | (1.38) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle O({\\Delta t}^ p).\\) | &nbsp; | (1.39) 

Thus, the global error would decrease with \\({\\Delta t}\\) by one order less than the local error because the local errors sum for \\(T/{\\Delta t}\\) timesteps. However, we must be careful because the local errors do not have to sum this way, particularly if the numerical method is not stable. We will see in the next lecture that if a numerical method is both consistent and stable, this will be enough to guarantee convergence. For now, we concentrate on quantifying the local accuracy and leave the discussion of consistency and stability for another lecture.

The local error (usually called the local truncation error) is the difference between the approximate solution at step \\(n+1\\) and the solution at \\(t^{n+1}\\) of the ODE that passes through the previous computed point \\(v^ n\\). The local error can be evaluated by considering the difference between the approximate solution at step \\(n+1\\) computed using the exact solution for the required data and the exact solution at \\(t^{n+1}\\).

Example: Local error of the forward Euler method
------------------------------------------------

Let's consider the forward Euler method as an example. Recall, the forward Euler method is,

| \\\[v^{n+1} = v^ n + {\\Delta t}f(v^ n,t^ n).\\\] | (1.40) 

Thus, for the forward Euler method, \\(v^{n+1} = v^{n+1}(v^ n,{\\Delta t},t^ n)\\). Then, if we substitute the exact solution into the right-hand side, we find,

| \\\[v^{n+1}(u^ n,{\\Delta t},t^ n) = u^ n + {\\Delta t}f(u^ n,t^ n).\\\] | (1.41) 

Recall our notation that \\(u\\) is the exact solution; in this discussion we use the superscript notation \\(u^ n = u(n{\\Delta t})\\) realizing that \\(u = u(t)\\). Therefore the equation above gives the value of \\(v^{n+1}\\) that would be computed if the exact solution were available at time \\(t^ n\\). The local truncation error for the forward Euler method is then,

| \\\[\\mbox{Local truncation error} \\equiv v^{n+1}(u^ n,{\\Delta t},t^ n) - u^{n+1}. \\label{equ:local\_ error\_ fe}\\\] | (1.42) 

Substitution gives,

| \\\[\\mbox{Local truncation error} = u^ n + {\\Delta t}f(u^ n,t^ n) - u^{n+1}.\\\] | (1.43) 

The local order of accuracy is then found using a Taylor series expansion about \\(t = t^ n\\). Recall that \\(f(u^ n,t^ n) = u\_ t(t^ n)\\) and

| \\\[u(t^{n+1}) = u(t^ n) + {\\Delta t}u\_ t(t^ n) + \\frac{1}{2}{\\Delta t}^2 u\_{tt}(t^ n) + O({\\Delta t}^3).\\\] | (1.44) 

Substitution gives the local truncation error as,

| &nbsp; | \\(\\displaystyle \\mbox{Local truncation error}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle u^ n + {\\Delta t}f(u^ n,t^ n) - u^{n+1},\\) | &nbsp; | (1.45) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle u(t^ n) + {\\Delta t}u\_ t(t^ n) - \\left\[u(t^ n) + {\\Delta t}u\_ t(t^ n) + \\frac{1}{2}{\\Delta t}^2 u\_{tt}(t^ n) + O({\\Delta t}^3)\\right\]\\) | &nbsp; | (1.46) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle -\\frac{1}{2}{\\Delta t}^2 u\_{tt}(t^ n) + O({\\Delta t}^3).\\) | &nbsp; | (1.47) 

Thus, the leading term of the local truncation error for the forward Euler method is \\(-\\frac{1}{2}{\\Delta t}^2 u\_{tt}(t^ n) = O({\\Delta t}^2)\\). Based on our previous argument, we expect that the global accuracy of the forward Euler method should be \\(O({\\Delta t})\\) (i.e. first order accuracy). This was in fact observed in Example [1.5]({{< baseurl >}}/resources/ga_fe).

BackOrder of Accuracy ContinueLocal Order of Accuracy