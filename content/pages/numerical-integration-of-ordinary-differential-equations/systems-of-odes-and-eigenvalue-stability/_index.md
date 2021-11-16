---
content_type: page
parent_title: 'Unit 1: Numerical Integration of Ordinary Differential Equations'
parent_uid: 5cae4847-c59a-a247-c767-3c0c6b0abef1
title: 1.6 Systems of ODE's and Eigenvalue Stability
uid: 36e637ce-d6ff-e05d-3606-0d537611ad2e
---

*   [<Dahlquist Equivalence Theorem]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/zero-stability-and-the-dahlquist-equivalence-theorem/1690r-dahlquist-equivalence-theorem)
*   [1.6.1Nonlinear Systems]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/systems-of-odes-and-eigenvalue-stability)
*   [1.6.2Linear Constant Coefficient Systems]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/systems-of-odes-and-eigenvalue-stability/1690r-linear-constant-coefficient-systems)
*   [1.6.3Eigenvalue Stability for a Linear ODE]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/systems-of-odes-and-eigenvalue-stability/1690r-eigenvalue-stability-for-a-linear-ode)
*   [1.6.4Imaginary Eigenvalues]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/systems-of-odes-and-eigenvalue-stability/1690r-imaginary-eigenvalues)
*   [\>Linear Constant Coefficient Systems]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/systems-of-odes-and-eigenvalue-stability/1690r-linear-constant-coefficient-systems)

1.6.1 Nonlinear Systems
-----------------------

[Measurable Outcome 1.1]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO11), [Measurable Outcome 1.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO13), [Measurable Outcome 1.6]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO16) 

For a system of ODE's, we have the same canonical form as for a scalar (see Equation [1.8](javascript: void(0))),

| \\\[u\_ t = f(u,t), \\label{equ:ODEsystem\_ nonlinear}\\\] | (1.84) 

except that \\(u\\) and \\(f\\) are vectors of the same length, \\(d\\):

| \\\[u = \[u\_1, u\_2, u\_3, \\cdots , u\_ d\]^ T \\qquad f = \[f\_1, f\_2, f\_3, \\cdots , f\_ d\]^ T\\\] | (1.85) 

Nonlinear Pendulum
------------------

One manner in which a system of ODE's occurs is for higher-order ODE's. A classic example of this is a second-order oscillator such as a pendulum. The nonlinear dynamics of a pendulum of length \\(L\\) satisfy the following second-order system of equations:

| \\\[\\theta \_{tt} + \\frac{g}{L}\\sin \\theta = 0. \\label{equ:nonpendulum}\\\] | (1.86) 

To transform this into a system of first-order equations, we define the angular rate, \\(\\omega\\),

| \\\[\\theta \_ t = \\omega .\\\] | (1.87) 

Then, Equation [1.86](javascript: void(0)) becomes,

| \\\[\\omega \_ t + \\frac{g}{L}\\sin \\theta = 0.\\\] | (1.88) 

For this example,

| \\\[u = \\left(\\begin{array}{c} \\omega \\\\ \\theta \\end{array} \\right) \\qquad f = \\left(\\begin{array}{c} -\\frac{g}{L}\\sin \\theta \\\\ \\omega \\end{array} \\right)\\\] | (1.89) 

A forward Euler method was used to simulate the motion of a pendulum (with \\(L\\) = 1 m, \\(g = 9.8\\) m/sec\\(^2\\)) released from rest at an angle of \\(45^\\circ\\) at a timestep of \\({\\Delta t}= 0.02\\) seconds. The results are shown in Figure [1.8]({{< baseurl >}}/resources/nonpen_fe). While the oscillatory motion is evident, the amplitude is growing which is not expected physically. This would indicate some kind of numerical stability problem. Note, however, that if a smaller \\({\\Delta t}\\) were used, the amplification would still be present but not as significant.

![The graph shows the oscillation of a non-linear pendulum increases in amplitude when simulated using forward Euler.](BASEURL_PLACEHOLDER/resources/nonpen_fe)

**Figure 1.8**: Forward Euler solution for nonlinear pendulum with \\(L\\) = 1 m, \\(g = 9.8\\) m/sec\\(^2\\), and \\({\\Delta t}= 0.02\\) seconds.

The same problem was also simulated using the midpoint method. These results are shown in Figure [1.9]({{< baseurl >}}/resources/nonpen_mp). For this method and \\({\\Delta t}\\) choice, the oscillation amplitude is constant and indicates that the midpoint method is a better choice for this problem than the forward Euler method.

![The graph shows the oscillation of a non-linear pendulum increases in amplitude when simulated using the midpoint method.](BASEURL_PLACEHOLDER/resources/nonpen_mp)

**Figure 1.9**: Midpoint solution for nonlinear pendulum with \\(L\\) = 1 m, \\(g = 9.8\\) m/sec\\(^2\\), and \\({\\Delta t}= 0.02\\) seconds.

BackDahlquist Equivalence Theorem ContinueLinear Constant Coefficient Systems