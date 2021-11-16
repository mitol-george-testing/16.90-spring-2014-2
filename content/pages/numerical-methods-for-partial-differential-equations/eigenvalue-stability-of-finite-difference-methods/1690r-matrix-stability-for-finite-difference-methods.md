---
content_type: page
parent_title: 2.7 Eigenvalue Stability of Finite Difference Methods
parent_uid: 935b6a61-8d7d-2772-6ca1-df78ee864834
title: 2.7 Eigenvalue Stability of Finite Difference Methods
uid: 3e2eea01-ee64-f3f7-264f-4d9e57b3b622
---

*   [<Eigenvalue Stability of Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods)
*   [2.7.1Fourier Analysis of PDEs]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods)
*   [2.7.2Matrix Stability for Finite Difference Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-matrix-stability-for-finite-difference-methods)
*   [2.7.3Circulant Matrices]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-circulant-matrices)
*   [2.7.4Stability Exercises]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-stability-exercises)
*   [\>Circulant Matrices]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/eigenvalue-stability-of-finite-difference-methods/1690r-circulant-matrices)

2.7.2 Matrix Stability for Finite Difference Methods
----------------------------------------------------

[Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22), [Measurable Outcome 2.9]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO29), [Measurable Outcome 2.10]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO210), [Measurable Outcome 2.11]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO211)

As we saw in Section [2.3.2]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-methods), finite difference (or finite volume) approximations can potentially be written in a semi-discrete form as,

| \\\[\\frac{{\\rm d}U}{{\\rm d}t} = AU + b. \\label{equ:semidiscrete}\\\] | (2.133) 

While there are some PDE discretization methods that cannot be written in that form, the majority can be. So, we will take the semi-discrete Equation ([2.133](javascript: void(0))) as our starting point. Note: the term semi-discrete is used to signify that the PDE has only been discretized in space.

Let \\(U(t)\\) be the exact solution to the semi-discrete equation. Then, consider perturbation \\(e(t)\\) to the exact solution such that the perturbed solution, \\(V(t)\\), is:

| \\\[V(t) = U(t) + e(t).\\\] | (2.134) 

The questions that we wish to resolve are: (1) can the perturbation \\(e(t)\\) grow in time for the semi-discrete problem, and (2) what the stability limits are on the timestep for a chosen time integration method.

First, we substitute \\(V(t)\\) into Equation ([2.133](javascript: void(0))),

| &nbsp; | \\(\\displaystyle \\frac{{\\rm d}V}{{\\rm d}t}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle AV + b\\) | &nbsp; | (2.135) |
| &nbsp; | \\(\\displaystyle \\frac{{\\rm d}(U+e)}{{\\rm d}t}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle A(U+e) + b\\) | &nbsp; | (2.136) |
| &nbsp; | \\(\\displaystyle \\frac{{\\rm d}e}{{\\rm d}t}\\) | \\(\\displaystyle =\\) | \\(\\displaystyle A e.\\) | &nbsp; | (2.137) 

Thus, the perturbation must satisfy the homogeneous equation, \\(e\_ t = A e\\). Having studied the behavior of linear system of equations in Section [1.6.2]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/systems-of-odes-and-eigenvalue-stability/1690r-linear-constant-coefficient-systems), we know that \\(e(t)\\) will grow unbounded as \\(t \\rightarrow \\infty\\) if any of the real parts of the eigenvalues of \\(A\\) are positive.

The problem is that determining the eigenvalues of \\(A\\) can be non-trivial. In fact, for a general problem finding the eigenvalues of \\(A\\) can be about as hard as solving the specific problem. So, while the matrix stability method is quite general, it can also require a lot of time to perform. Still, the matrix stability method is an indispensible part of the numerical analysis toolkit.

As we saw in the eigenvalue analysis of ODE integration methods, the integration method must be stable for all eigenvalues of the given problem. One manner that we can determine whether the integrator is stable is by plotting the eigenvalues scaled by the timestep in the complex \\(\\lambda {\\Delta t}\\) plane and overlaying the stability region for the desired ODE integrator. Then, \\({\\Delta t}\\) can be adjusted to attempt to bring all eigenvalues into the stability region for the desired ODE integrator.

Matrix Stability of FTCS for 1-D convection
-------------------------------------------

Earlier, we used a forward time, central space (FTCS) discretization for 1-d convection,

| \\\[\\frac{U\_ i^{n+1}-U\_ i^ n}{{\\Delta t}} + u\_{i}^ n\\delta \_{2x} U^ n\_{i} = 0. \\label{equ:con1d\_ ftcs}\\\] | (2.138) 

Since this method is explicit, the matrix \\(A\\) does not need to be constructed directly, rather Equation ([2.138](javascript: void(0))) can be used to find the new values of \\(U\\) at each point \\(i\\). However, if we are interested in calculating the eigenvalues to analyze the eigenvalue stability, then the \\(A\\) matrix is required. The following script does exactly that (i.e. calculates \\(A\\), determines the eigenvalues of \\(A\\), and then plots the eigenvalues scaled by \\({\\Delta t}\\) overlayed with the forward Euler stability region). The script can set either the inflow/outflow boundary conditions described in Example [2.3.3]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-difference-methods/1690r-finite-difference-method-applied-to-1-d-convection), or can set periodic boundary conditions. We will look at the eigenvalues of both cases.

% This MATLAB script calculates the eigenvalues of
% the one-dimensional convection equation discretized by
% finite differences.  The discretization uses central
% differences in space and forward Euler in time.
%
% Periodic bcs are set if periodic\_flag == 1.
%
% Otherwise, an inflow (dirichlet) bc is set and at
% the outflow a one-sided (backwards) difference is used.
%

clear all;

periodic\_flag = 1;

% Set-up grid
xL = -4;
xR =  4;
Nx = 21; % number of points
x = linspace(xL,xR,Nx);

% Calculate cell size in control volumes (assumed equal)
dx = x(2) - x(1);

% Set velocity
u = 1;

% Set timestep
CFL = 1;
dt = CFL\*dx/abs(u);

% Set bc state at left (assumes u>0)
UL = exp(-xL^2);

% Allocate matrix to hold stiffness matrix (A).
%
A = zeros(Nx-1,Nx-1);

% Construct A except for first and last row
for i = 2:Nx-2,
  A(i,i-1) =  u/(2\*dx);
  A(i,i+1) = -u/(2\*dx);
end

if (periodic\_flag == 1), % Periodic bcs

  A(1   ,2   ) = -u/(2\*dx);
  A(1   ,Nx-1) =  u/(2\*dx);
  A(Nx-1,1   ) = -u/(2\*dx);
  A(Nx-1,Nx-2) =  u/(2\*dx);

else % non-periodic bc's

  % At the first interior node, the i-1 value is known (UL).
  % So, only the i+1 location needs to be set in A.
  A(1,2) = -u/(2\*dx);

  % Outflow boundary uses backward difference
  A(Nx-1,Nx-2) =  u/dx;
  A(Nx-1,Nx-1) = -u/dx;

end

% Calculate eigenvalues of A
lambda = eig(A);

% Plot lambda\*dt
plot(lambda\*dt,'\*');
xlabel('Real \\lambda\\Delta t');
ylabel('Imag \\lambda\\Delta t');

% Overlay Forward Euler stability region
th = linspace(0,2\*pi,101);
hold on;
plot(-1 + sin(th),cos(th));
hold off;
axis('equal');
grid on;

Figures [2.21]({{< baseurl >}}/resources/ftcs_eig) and [2.22]({{< baseurl >}}/resources/ftcs_eig_per) show plots of \\(\\lambda {\\Delta t}\\) for a CFL set to one. Recall that for this one-dimensional problem, the CFL number was defined as,

| \\\[\\mathrm{CFL} = \\frac{&#124;u&#124;{\\Delta t}}{{\\scriptstyle \\Delta } x}.\\\] | (2.139) 

In the inflow/outflow boundary condition case (shown in Figure [2.21]({{< baseurl >}}/resources/ftcs_eig)) the eigenvalues lay slightly inside the negative real half-plane. As they move away from the origin, they approach the imaginary axis at \\(\\pm i\\). The periodic boundary conditions give purely imaginary eigenvalues but these also approach \\(\\pm i\\) as the move away from the origin. Note that the periodic boundary conditions actually give a zero eigenvalue so that the matrix \\(A\\) is actually singular (Why is this?). Regardless what we see is that for a \\(\\mathrm{CFL} = 1\\), some \\(\\lambda {\\Delta t}\\) exist which are outside of the forward Euler stability region. We could try to lower the timestep to bring all of the \\(\\lambda {\\Delta t}\\) into the stability region, however that will prove to be practically impossible since the extreme eigenvalues approach \\(\\pm \\alpha i\\) (i.e. they are purely imaginary). Thus, no finite value of \\({\\Delta t}\\) exists for which these eigenvalues can be brought inside the circular stability region of the forward Euler method (i.e. the FTCS is unstable for convection).

![This graph shows a large circle, which represents the negative real half-plane, with a vertical line of asteriks, representing the eigenvalues for Dirichlet boundary conditions, that overlap the circle on the far right.](BASEURL_PLACEHOLDER/resources/ftcs_eig)

**Figure 2.21**: \\(\\Lambda {\\Delta t}\\) distribution for one-dimensional convection example with Dirichlet boundary conditions. Note \\({\\Delta t}\\) set such that \\(CFL=1\\).

![This graph shows a large circle, which represents the negative real half-plane, with a vertical line of asteriks, representing the eigenvalues for periodic boundary conditions, that only overlaps the circle at one point on the far right.](BASEURL_PLACEHOLDER/resources/ftcs_eig_per)

**Figure 2.22**: \\(\\Lambda {\\Delta t}\\) distribution for one-dimensional convection example with periodic boundary conditions. Note \\({\\Delta t}\\) set such that \\(CFL=1\\).

We may also be interested in what happens to the eigenvalue spectrum of \\(A\\) when we change \\(\\Delta x\\) keeping the CFL constant. Figures [2.23]({{< baseurl >}}/resources/ftcs_eig_dx) and [2.24]({{< baseurl >}}/resources/ftcs_eig_per_dx) plot the eigenvalue spectrum for both periodic and Dirichlet boundary conditions refining \\(\\Delta x\\) by a factor of 10. For the periodic BC case, again we see purely imaginary eigenvalues approaching \\(\\pm i\\) (though, of course, we have more eigenvalues as \\(A\\) is now a larger system). For the Dirichlet case, the eigenvalues again lie slightly inside the negative real half-plane, though in this case closer to the imaginary axis than for the coarser system. In fact, the eigenvalues of the Dirichlet problem approach those of the periodic problem in the limit as \\(\\Delta x \\to 0\\).

![This graph shows a large circle, which represents the negative real half-plane, with a vertical line of asteriks, representing the eigenvalue spectrum for periodic and Dirichlet boundary conditions, that intersect the circle on the far right.](BASEURL_PLACEHOLDER/resources/ftcs_eig_dx)

**Figure 2.23**: \\(\\Lambda {\\Delta t}\\) distribution for one-dimensional convection example with Dirichlet boundary conditions. Note \\(\\Delta x=\\frac{1}{20}\\) and \\({\\Delta t}\\) set such that \\(CFL=1\\).

![This graph shows a large circle, which represents the negative real half-plane, with a vertical line of asteriks, representing the eigenvalue spectrum for periodic and Dirichlet boundary conditions, that only intersect the circle at the far right edge.](BASEURL_PLACEHOLDER/resources/ftcs_eig_per_dx)

**Figure 2.24**: \\(\\Lambda {\\Delta t}\\) distribution for one-dimensional convection example with periodic boundary conditions. Note \\(\\Delta x = \\frac{1}{20}\\) and \\({\\Delta t}\\) set such that \\(CFL=1\\).

BackEigenvalue Stability of Finite Difference Methods ContinueCirculant Matrices