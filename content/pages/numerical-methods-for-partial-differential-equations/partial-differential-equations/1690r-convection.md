---
content_type: page
parent_title: 2.2 Partial Differential Equations
parent_uid: 735249e6-5cf9-7136-d3a6-4f4d3458178c
title: 2.2 Partial Differential Equations
uid: 5b35a359-99c0-aad1-8b33-6126f6b0a143
---

*   [<One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-one-dimensional-burgers-equation)
*   [2.2.1Conservation Laws in Integral and Differential Form]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations)
*   [2.2.2One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-one-dimensional-burgers-equation)
*   [2.2.3Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection)
*   [2.2.4Characteristics for One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-characteristics-for-one-dimensional-burgers-equation)
*   [2.2.5Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-diffusion)
*   [2.2.6Convection-Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-convection-diffusion)
*   [2.2.7Linear Elasticity]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-linear-elasticity)
*   [\>Characteristics for One-Dimensional Burgers Equation]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-characteristics-for-one-dimensional-burgers-equation)

2.2.3 Convection
----------------

[Measurable Outcome 2.1]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO21), [Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22), [Measurable Outcome 2.5]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO25)

[Convection](http://en.wikipedia.org/wiki/Convection) is the concerted, collective movement of groups or aggregates of molecules within fluids. It is a transport mechanism of a substance or conserved property by a fluid due to the fluid's bulk motion. An example of convection is the transport of pollutants or silt in a river by bulk water flow downstream. Another commonly convected quantity is energy or enthalpy. Here the fluid may be any material that contains thermal energy, such as water or air. In general, any substance or conserved, extensive quantity can be convected by a fluid that can hold or contain the quantity or substance. Convection occurs on a large scale in atmospheres, oceans, planetary mantles, and it provides the mechanism of heat transfer for a large fraction of the outermost interiors of our sun and all stars. Fluid movement during convection may be invisibly slow, or it may be obvious and rapid, as in a hurricane. On astronomical scales, convection of gas and dust is thought to occur in the accretion disks of black holes, at speeds which may closely approach that of light.

In many applications, especially those in fluid dynamics, convection is the dominant physical transport mechanism over much of the domain of interest. While diffusion (see Section [2.2.5]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/partial-differential-equations/1690r-diffusion)) is always present, often its effects are smaller except in limited regions (often near solid boundaries where boundary layers form due to the combined effects of diffusion and convection).

In this section, we will derive the convection equation using the conservation law as given in Equation [2.1](javascript: void(0)). Specifically, let \\(U\\) be the 'conserved' scalar quantity, e.g., mass, energy, momentum, number of atoms or amount of "stuff" per unit volume, per unit area or per unit length. Let the flux of \\(U\\) be given by,

| \\\[\\vec{F} = \\vec{v}U \\label{equ:convection\_ fluxes}\\\] | (2.18) 

where \\(\\vec{v}(\\vec{x},t)\\) is a known velocity vector. This flux describes the amount of conserved quantity that, during a unit time, goes through a unit area (in 3 spatial dimensions), through a unit length (in 2 spatial dimensions), or through a point (in 1 spatial dimension). Note, we also use a zero source term, \\(S=0\\), a non-zero source term could be included, but for simplicity is assumed to be zero. As a PDE, this scalar conservation law is,

| \\\[\\frac{\\partial U}{\\partial t} + \\nabla \\cdot \\left(\\vec{v}U\\right) = 0.\\\] | (2.19) 

Expanding the spatial derivatives gives,

| \\\[\\frac{\\partial U}{\\partial t} + \\vec{v} \\cdot \\nabla U + \\left( \\nabla \\cdot \\vec{v} \\right)U = 0.\\\] | (2.20) 

Often a reasonable assumption is that the velocity field is divergence free such that \\(\\nabla \\cdot \\vec{v} = 0\\). In this case, we arrive at what is commonly referred to as the convection equation,

| \\\[\\frac{\\partial U}{\\partial t} + \\vec{v} \\cdot \\nabla U = 0. \\label{equ:convection\_ pde}\\\] | (2.21) 

Physically, this equation states that following along the streamwise direction (i.e. convecting with the velocity), the quantity \\(U\\) does not change.

In developing numerical methods for convection-dominated problems, we will often rely on insight that can be gained from the convection equation for the specific case when the velocity field is a constant value, i.e. \\(\\vec{v}(\\vec{x}, t) = \\vec{v}\\). In this situation, the solution to Equation [2.21](javascript: void(0)) has the following form,

| \\\[U(\\vec{x}, t) = U\_0(\\vec{\\xi }) \\quad \\mbox{where} \\quad \\vec{\\xi } = \\vec{x} - \\vec{v}t, \\label{equ:convection\_ solution}\\\] | (2.22) 

where \\(U\_0(\\vec{x})\\) is the distribution of \\(U\\) at time \\(t=0\\). By substitution, we can confirm that this indeed is a solution of Equation [2.21](javascript: void(0)), Using the chain rule

| &nbsp; | \\(\\displaystyle \\dfrac {\\partial U}{\\partial t} + \\vec{v} \\cdot \\nabla U\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\dfrac {\\partial }{\\partial t}U\_0(\\vec{\\xi }) + \\vec{v} \\cdot \\nabla \_{\\vec{x}} U\_0(\\vec{\\xi })\\) | &nbsp; | (2.23) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\nabla \_{\\vec{\\xi }} U\_0 \\cdot \\dfrac {\\partial \\vec{\\xi }}{\\partial t} + \\vec{v} \\cdot \\left( \\nabla \_{\\vec{\\xi }} U\_0 \\cdot \\nabla \_{\\vec{x}} \\xi \\right)\\) | &nbsp; | (2.24) 

, where \\(\\nabla \_{\\vec{x}}\\) and \\(\\nabla \_{\\vec{\\xi }}\\) denote, respectively, the gradients with respect to \\(\\vec{x}\\) and \\(\\vec{\\xi }\\). The partial derivatives of \\(\\vec{\\xi }\\) with respect to \\(\\vec{x}\\) and \\(r\\) are,

| &nbsp; | \\(\\displaystyle \\nabla \_{\\vec{x}} \\vec{\\xi } = I, \\quad \\dfrac {\\partial \\vec{\\xi }}{\\partial t} = -\\vec{v},\\) | &nbsp; | (2.25) 

where \\(I\\) is the identity tensor. Upon substitution of these partial derivatives,

| &nbsp; | \\(\\displaystyle \\dfrac {\\partial U}{\\partial t} + \\vec{v} \\cdot \\nabla {U}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\nabla \_{\\vec{\\xi }} U\_0 \\cdot (-\\vec{v}) + \\vec{v} \\cdot \\left( \\nabla \_{\\vec{\\xi }} U\_0 \\cdot I \\right)\\) | &nbsp; | (2.26) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\nabla \_{\\vec{\\xi }} U\_0 \\cdot (-\\vec{v}) + \\vec{v} \\cdot \\left( \\nabla \_{\\vec{\\xi }} U\_0 \\right)\\) | &nbsp; | (2.27) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle 0.\\) | &nbsp; | (2.28) 

Thus, \\(U(\\vec{x},t) = U\_0(\\vec{x}-\\vec{v}t)\\) is a solution to the convection equation.

**Example** One-dimensional Convection

To illustrate the behavior of the convection equation consider a simple one-dimensional convection problem

| \\\[\\frac{\\partial U}{\\partial t} + v\\frac{\\partial u}{\\partial x} = 0 \\label{equ:onedconvect}\\\] | (2.29) 

on the domain \\(\\Omega = \[0,2\]\\), with constant flow velocity \\(v=1\\). The initial distribution \\(U\_0\\) is

| \\\[U\_0(x) = 0.75e^{-\\left(\\frac{x-0.5}{0.1}\\right)^2}\\\] | (2.30) 

Figure [2.1]({{< baseurl >}}/resources/onedconvect) plots the initial solution \\(U\_0\\) as well as \\(U\\) at \\(t=1\\).

![The graph shows two peaks for a simple one-dimensional convection initial solution U0 (left peak) as well as U at t=1 (right peak).](BASEURL_PLACEHOLDER/resources/onedconvect)

**Figure 2.1**: Distribution of \\(U\\) at \\(t=0\\) and at \\(t=1\\) for a one-dimensional convection problem with velocity \\(v=1\\).

Looking at the solution for the one-dimensional convection problem, we observe that \\(U(x,t)\\) has the same shape as \\(U\_0(x)\\), except the solution has been shifted by a distance \\(v \\times t\\). This behavior in which the state \\(U\\) does not change as it propagates leads to the concept of a **characteristic**. A characteristic is defined as a trajectory \\(\\vec{x}(t)\\) along which the state does not change. The rate-of-change of \\(U\\) along a trajectory \\(\\vec{x}(t)\\) can be written using the total derivative as,

| &nbsp; | \\(\\displaystyle \\dfrac {d U}{d t}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\dfrac {\\partial U}{\\partial t} + \\dfrac {\\partial U}{\\partial x} \\dfrac {d x}{d t}.\\) | &nbsp; | (2.31) 

Comparing this to Equation [2.29](javascript: void(0)), we see that if \\(\\frac{dx}{dt}=v\\), then \\(\\frac{dU}{dt}=0\\) (i.e., \\(U=\\) constant). In other words, the characteristic for the convection equation is a line with slope \\(v\\). Figure [2.2]({{< baseurl >}}/resources/charlines) shows the characteristic lines for the one-dimensional convection problem (in dashed lines) with the solutions at \\(t=0\\) and \\(t=1\\) superimposed. As we can see from Figure [2.2]({{< baseurl >}}/resources/charlines), the solution at \\((x,t)\\) is simply obtained by following the characteristic line back to \\(t=0\\) and evaluating the initial condition.

![The graph shows characteristic lines for the one-dimensional convection problem with the solutions at t=0 and t=1 superimposed.](BASEURL_PLACEHOLDER/resources/charlines)

**Figure 2.2**: Characteristic lines for a one-dimensional convection problem with velocity \\(v=1\\)

For convection and other equations which possess characteristics, the solution at a particular point in space and time \\(U(\\vec{x}, t)\\) depends only upon the points along the characteristics from earlier times. For any partial differential equation, we call the region which affects the solution at \\((\\vec{x}, t)\\)the **domain of dependence**. For convection, the domain of dependence for \\((\\vec{x},t)\\) is simply the characteristic line, \\(\\vec{x}(t)\\),\\(s<t\\).

Among other phenomena, this equation can model the convection of cars along a freeway. \\(U\\) is the number of cars per unit length of the freeway. There is with no entrance or exit ramps (source term) in the segment of freeway. The initial condition \\(U(x, 0)\\) is a distribution of cars at time \\(t=0\\). All cars are moving at velocity \\(v\\). So the flux, i.e., the number of cars that moves past a fixed spatial location per unit time, is \\(v U\\). At time \\(t=1\\) the distribution of cars, \\(U(x,1)\\), has shifted to the right, notice that the number of cars at point \\(x\\) at time \\(t=1\\) is the same as the number of cars at point \\(x-vt\\) at time \\(t=0\\). Notice that the car distribution \\(at t=1\\) does not depend on what is to the left or right of the characteristic.

BackOne-Dimensional Burgers Equation ContinueCharacteristics for One-Dimensional Burgers Equation