---
content_type: page
parent_title: 2.5 Introduction to Finite Volume Methods
parent_uid: 3d8df8b8-2291-7094-b5a6-9893808a75cc
title: 2.5 Introduction to Finite Volume Methods
uid: d4283096-1401-99d2-0c85-a833f3518826
---

*   [<Finite Volume Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-applied-to-1-d-convection)
*   [2.5.1Finite Volume Method in 1-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods)
*   [2.5.2Finite Volume Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-applied-to-1-d-convection)
*   [2.5.3Finite Volume Method in 2-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-in-2-d)
*   [2.5.4Finite Volume Method for 2-D Convection on a Rectangular Mesh]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-2-d-convection-on-a-rectangular-mesh)
*   [2.5.5Finite Volume Method for Nonlinear Systems]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-nonlinear-systems)
*   [\>Finite Volume Method for 2-D Convection on a Rectangular Mesh]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-2-d-convection-on-a-rectangular-mesh)

2.5.3 Finite Volume Method in 2-D
---------------------------------

[Measurable Outcome 2.1]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO21), [Measurable Outcome 2.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO23), [Measurable Outcome 2.4]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO24)

The finite volume discretization can be extended to two-dimensional problems. Suppose the physical domain is divided into a set of triangular control volumes, as shown in Figure [2.15]({{< baseurl >}}/resources/triangle_cv).

![This schematic shows a finite volume discretization extended over two dimensions by dividing the physical domain into a set of four triangles.](BASEURL_PLACEHOLDER/resources/triangle_cv)

**Figure 2.15**: Triangular mesh and notation for finite volume method.

Application of Equation [2.1](javascript: void(0)) to control volume A gives,

| \\\[\\frac{{\\rm d}}{{\\rm d}t}\\int \_{\\Omega \_ A} U\\, dA + \\int \_{\\delta \\Omega \_ A} H(U,\\vec{n})\\, ds = \\int \_{\\Omega \_ A} S(U,t)\\, dA, \\label{equ:2d\_ cv\_ temp}\\\] | (2.109) 

where \\(\\Omega \_ A\\) is the interior and \\(\\delta \\Omega \_ A\\) is the boundary of control volume A. \\(H(U,\\vec{n})\\) is the flux normal to the face,

| \\\[H(U,\\vec{n}) \\equiv \\left\[F(U)\\vec{i} + G(U)\\vec{j}\\right\]\\cdot \\vec{n}. \\label{equ:H\_ def}\\\] | (2.110) 

As in the one-dimensional case, we define the cell average,

| \\\[U\_ A \\equiv \\frac{1}{A\_ A} \\int \_{\\Omega \_ A} U\\, dA,\\\] | (2.111) 

where \\(A\_ A\\) is the area of control volume \\(A\\). Thus, Equation [2.109](javascript: void(0)) becomes,

| \\\[A\_ A\\frac{{\\rm d}U\_ A}{{\\rm d}t} + \\int \_{\\delta \\Omega \_ A} H(U,\\vec{n})\\, ds = \\int \_{\\Omega \_ A} S(U,t)\\, dA.\\\] | (2.112) 

In the case of convection, we again assume \\(S=0\\). Also, we expand the surface integral into the contributions for the three edges,

| \\\[A\_ A\\frac{{\\rm d}U\_ A}{{\\rm d}t} + \\int \_{1}^{2} H(U,\\vec{n}\_{AB} )\\, ds + \\int \_{2}^{3} H(U,\\vec{n}\_{AC} )\\, ds + \\int \_{3}^{1} H(U,\\vec{n}\_{AD} )\\, ds = 0,\\\] | (2.113) 

where \\(\\vec{n}\_{AB}\\) is the unit normal pointing from cell A to cell B, and similarly for \\(\\vec{n}\_{AC}\\) and \\(\\vec{n}\_{AD}\\).

As in one-dimensional case, we assume that the solution everywhere in the control volume is equal to the cell average value. Finally, the flux at each interface is determined by the ‘upwind' value using the velocity component normal to the face. For example, at the interface between cell A and B,

| \\\[H(U,\\vec{n}\_{AB}) \\approx \\hat{H}(U\_ A, U\_ B, \\vec{n}\_{AB}) \\equiv \\frac{1}{2}\\vec{u}\_{AB}\\cdot \\vec{n}\_{AB}\\left(U\_ B + U\_ A\\right) - \\frac{1}{2}&#124;\\vec{u}\_{AB}\\cdot \\vec{n}\_{AB}&#124;\\left(U\_ B - U\_ A\\right), \\label{equ:upwindflux\_ convection2d}\\\] | (2.114) 

where \\(\\vec{u}\_{AB}\\) is the velocity between the control volumes. Thus, when \\(\\vec{u}\_{AB}\\cdot \\vec{n}\_{AB} > 0\\), the flux is determined by the state from cell A, i.e. \\(U\_ A\\). Likewise, when \\(\\vec{u}\_{AB}\\cdot \\vec{n}\_{AB} < 0\\), the flux is determined by the state from cell B, i.e. \\(U\_ B\\). The velocity, \\(\\vec{u}\_{AB}\\) is usually approximated as the velocity at the midpoint of the edge (note: \\(\\vec{u}\\) can be a function of \\(\\vec{x}\\) in two-dimensions even though the velocity is assumed to be divergence free, i.e. \\({\\partial u}/{\\partial x} + {\\partial v}/{\\partial y} = 0\\)). We use the notation \\(\\hat{H}\\) to indicate that the flux is an approximation to the true flux when \\(\\vec{u}\\) is not constant. Thus, the finite volume algorithm prior to time discretization would be given by,

| \\\[A\_ A\\frac{{\\rm d}U\_ A}{{\\rm d}t} + \\hat{H}(U\_ A,U\_ B,\\vec{n}\_{AB} )\\Delta s\_{AB} + \\hat{H}(U\_ A,U\_ C,\\vec{n}\_{AC} )\\Delta s\_{AC} + \\hat{H}(U\_ A,U\_ D,\\vec{n}\_{AD} )\\Delta s\_{AD} = 0.\\\] | (2.115) 

The final step is to integrate in time. As in the one-dimensional case, we might use a forward Euler algorithm which would result in the final fully discrete finite volume method,

| \\\[A\_ A\\frac{U\_ A^{n+1} - U\_ A^ n}{{\\Delta t}} + \\hat{H}(U\_ A^ n,U\_ B^ n,\\vec{n}\_{AB} )\\Delta s\_{AB} + \\hat{H}(U\_ A^ n,U\_ C^ n,\\vec{n}\_{AC} )\\Delta s\_{AC} + \\hat{H}(U\_ A^ n,U\_ D^ n,\\vec{n}\_{AD} )\\Delta s\_{AD} = 0. \\label{equ:conservation\_2d\_ FVM}\\\] | (2.116) 

BackFinite Volume Method Applied to 1-D Convection ContinueFinite Volume Method for 2-D Convection on a Rectangular Mesh