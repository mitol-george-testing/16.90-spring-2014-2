---
content_type: page
parent_title: 1.7 Stiffness and Implicit Methods
parent_uid: 935324e3-1ab2-cb57-9059-0ba1f034fcd5
title: 1.7 Stiffness and Implicit Methods
uid: 84564160-240c-f3be-e329-df42818d2eaa
---

*   [<Newton-Raphson Implement Implicit Methods on Nonlinear Problems]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-newton-raphson-implement-implicit-methods-on-nonlinear-problems)
*   [1.7.1Stiffness]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods)
*   [1.7.2Spectral Condition Number]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-spectral-condition-number)
*   [1.7.3Implicit Methods for Linear Systems of ODEs]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-implicit-methods-for-linear-systems-of-odes)
*   [1.7.4Newton-Raphson Implement Implicit Methods on Nonlinear Problems]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-newton-raphson-implement-implicit-methods-on-nonlinear-problems)
*   [1.7.5Apply Newton-Rhapson]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods/1690r-apply-newton-rhapson)
*   [\>Multi-Step Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods)

1.7.5 Apply Newton-Raphson
--------------------------

[Measurable Outcome 1.4]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO14), [Measurable Outcome 1.13]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO113), [Measurable Outcome 1.14]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO114), [Measurable Outcome 1.19]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO119)

The value of \\(u\_1\\) will be (3 significant digits):

Consider the system of ODEs \\(\\dot{u}\_1 = \\sin (u\_2), \\dot{u\_2}=\\cos (u\_1)\\) starting from an initial condition of \\(u\_1=0, u\_2=\\pi /2\\). Implement trapezoidal integration with a timestep of \\({\\Delta t}=0.1.\\) Ensure that the 2-norm of the residual is less than \\(10^{-5}\\) to ensure that the Newton-Rhapson iteration has converged. After one timestep

The value of \\(u\_1\\) will be:

Exercise 1

Numerical Response

The value of \\(u\_2\\) will be:

Exercise 2

Numerical Response

CheckShow Answer

Answer:

The following code can be used to solve the problem:

dt=0.1; u0=\[0; pi/2\]; w = u0; normR=100; while normR > 1e-5 R = w - u0 - dt/2\*(\[sin(w(2)); cos(w(1))\] + \[sin(u0(2)); cos(u0(1))\]); J = \[0 cos(w(2)); -sin(w(1)) 0\]; dw = (eye(2)-dt/2\*J)­R; normR = norm(R);

BackNewton-Raphson Implement Implicit Methods on Nonlinear Problems ContinueMulti-Step Methods