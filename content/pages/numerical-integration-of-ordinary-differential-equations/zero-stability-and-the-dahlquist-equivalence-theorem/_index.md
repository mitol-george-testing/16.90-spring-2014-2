---
content_type: page
parent_title: 'Unit 1: Numerical Integration of Ordinary Differential Equations'
parent_uid: 5cae4847-c59a-a247-c767-3c0c6b0abef1
title: 1.5 Zero Stability and the Dahlquist Equivalence Theorem
uid: fab29380-eb66-91e4-e3ce-4dfce3f50fbe
---

*   [<Rate of Convergence Global Order of Accuracy]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/convergence/1690r-rate-of-convergence--global-order-of-accuracy-)
*   [1.5.1Consistency]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/zero-stability-and-the-dahlquist-equivalence-theorem)
*   [1.5.2Stability]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/zero-stability-and-the-dahlquist-equivalence-theorem/1690r-stability)
*   [1.5.3Dahlquist Equivalence Theorem]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/zero-stability-and-the-dahlquist-equivalence-theorem/1690r-dahlquist-equivalence-theorem)
*   [\>Stability]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/zero-stability-and-the-dahlquist-equivalence-theorem/1690r-stability)

1.5.1 Consistency
-----------------

[Measurable Outcome 1.8]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO18)

As given in Section [1.3.4]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/order-of-accuracy/1690r-definition-of-multi-step-methods), an \\(s\\)-step multi-step method can be written as,

| \\\[v^{n+1} + \\sum \_{i=1}^ s \\alpha \_ i v^{n+1-i} - {\\Delta t}\\sum \_{i=0}^ s \\beta \_ i f^{n+1-i} = 0,\\\] | (1.67) 

where the forcing terms have been moved to the left-hand side. Substituting the exact solution, \\(u(t)\\), into the left-hand side will produce a remainder which is in fact the opposite of the truncation error (see Equation [1.49](javascript: void(0))),

| \\\[u^{n+1} + \\sum \_{i=1}^ s \\alpha \_ i u^{n+1-i} - {\\Delta t}\\sum \_{i=0}^ s \\beta \_ i f^{n+1-i} = u^{n+1} - N(u^{n+1},u^ n, \\ldots , {\\Delta t}) = -\\tau \\label{equ:lte\_ consistency}\\\] | (1.68) 

If we only require that \\(\\tau \\rightarrow 0\\) (i.e. \\(\\tau = O({\\Delta t})\\)) as \\({\\Delta t}\\rightarrow 0\\), the method will not generally be consistent with the ODE. To see why, note that in the limit of \\({\\Delta t}\\rightarrow 0\\), the forcing terms will vanish since they are scaled by \\({\\Delta t}\\). Thus, \\(\\tau \\rightarrow 0\\) would place a constraint only on the \\(\\alpha\\)'s. Let's look at that constraint on the \\(\\alpha\\)'s to build some insight. Substituting Taylor series about \\(t=t^ n\\) for the values of \\(u\\) gives,

| \\\[u^{n+1} + \\sum \_{i=1}^ s \\alpha \_ i u^{n+1-i} = \\left(1 + \\sum \_{i=1}^ s \\alpha \_ i\\right)u^ n + O({\\Delta t}).\\\] | (1.69) 

Thus, for \\(\\tau \\rightarrow 0\\) as \\({\\Delta t}\\rightarrow 0\\) requires,

| \\\[1 + \\sum \_{i=1}^ s \\alpha \_ i = 0. \\label{equ:consistency\_ con1}\\\] | (1.70) 

This constraint can be interpreted as requiring a constant solution, i.e. \\(u(t) =\\) constant, to be a valid solution of the multi-step method. Clearly, this is not enough to guarantee consistency with the ODE since the ODE requires \\(u\_ t = f(u,t)\\).

To achieve a consistent discretization, we force \\(\\tau /{\\Delta t}\\rightarrow 0\\) (i.e. \\(\\tau = O({\\Delta t}^2)\\)). This stronger constraint can be shown to enforce that the ODE is satisfied in the limit of \\({\\Delta t}\\rightarrow 0\\):

| &nbsp; | \\(\\displaystyle \\frac{\\tau }{{\\Delta t}}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{N(u^{n+1},u^ n, \\ldots , {\\Delta t}) - u^{n+1}}{{\\Delta t}}\\) | &nbsp; | (1.71) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{N(u^{n+1},u^ n, \\ldots , {\\Delta t}) - \\left(u^ n + {\\Delta t}u\_ t^ n + O({\\Delta t}^2)\\right)}{{\\Delta t}}\\) | &nbsp; | (1.72) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{N(u^{n+1},u^ n, \\ldots , {\\Delta t}) - u^ n}{{\\Delta t}} - u\_ t^ n + O({\\Delta t})\\) | &nbsp; | (1.73) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{N(u^{n+1},u^ n, \\ldots , {\\Delta t}) - u^ n}{{\\Delta t}} - f(u^ n,t^ n) + O({\\Delta t})\\) | &nbsp; | (1.74) 

Thus, in the limit as \\({\\Delta t}\\rightarrow 0\\), to obtain \\(\\tau /{\\Delta t}\\rightarrow 0\\) then the slope of the numerical method (i.e. the first term) must be equal to the forcing at \\(t^ n\\). In other words, the multi-step discretization would satisfy the governing equation in the limit. An equivalent way to write this consistency constraint is,

| \\\[\\lim \_{{\\Delta t}\\rightarrow 0} \\frac{1}{{\\Delta t}}\\left\[ u^{n+1} + \\sum \_{i=1}^ s \\alpha \_ i u^{n+1-i}\\right\] - \\sum \_{i=0}^ s \\beta \_ i f^{n+1-i} = u\_ t(t^ n) - f(u(t^ n),t^ n) = 0. \\label{equ:consistency\_ constraint}\\\] | (1.75) 

In terms of the local accuracy, consistency requires that the multi-step method be at least first-order \\((p=1)\\) since \\(\\tau = O({\\Delta t}^{p+1})\\) and consistency requires that \\(\\tau /{\\Delta t}= O({\\Delta t}^ p)\\) must go to zero (i.e. \\(p \\geq 1\\)).

**Exercise** Which of the following numerical methods is consistent?

Exercise 1

&nbsp; \\(v^{n+1}=v^ n + \\Delta t f^{n+1}\\) &nbsp;

&nbsp; \\(v^{n+1} = v^ n + \\frac{1}{2} \\Delta t f^{n+1}\\) &nbsp;

&nbsp; \\(v^{n+1} = v^ n + \\frac{1}{2}\\Delta t f^ n\\) &nbsp;

&nbsp; \\(v^{n+1} = v^{n-1}\\) &nbsp;

CheckShow Answer

Answer: This is the backward Euler Method

BackRate of Convergence Global Order of Accuracy ContinueStability