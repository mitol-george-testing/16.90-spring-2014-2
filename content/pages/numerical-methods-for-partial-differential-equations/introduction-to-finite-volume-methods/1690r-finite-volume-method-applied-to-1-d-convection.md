---
content_type: page
parent_title: 2.5 Introduction to Finite Volume Methods
parent_uid: 3d8df8b8-2291-7094-b5a6-9893808a75cc
title: 2.5 Introduction to Finite Volume Methods
uid: 767b5c96-4bd2-394b-92da-ca9fa25f2e1e
---

*   [<Introduction to Finite Volume Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods)
*   [2.5.1Finite Volume Method in 1-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods)
*   [2.5.2Finite Volume Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-applied-to-1-d-convection)
*   [2.5.3Finite Volume Method in 2-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-in-2-d)
*   [2.5.4Finite Volume Method for 2-D Convection on a Rectangular Mesh]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-2-d-convection-on-a-rectangular-mesh)
*   [2.5.5Finite Volume Method for Nonlinear Systems]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-nonlinear-systems)
*   [\>Finite Volume Method in 2-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-in-2-d)

2.5.2 Finite Volume Method applied to 1-D Convection
----------------------------------------------------

[Measurable Outcome 2.1]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO21), [Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22), [Measurable Outcome 2.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO23)

The following MATLAB® script solves the one-dimensional convection equation using the finite volume algorithm given by Equation [2.107](javascript: void(0)) and [2.108](javascript: void(0)). The problem is assumed to be periodic so that whatever leaves the domain at \\(x = x\_ R\\) re-enters it at \\(x=x\_ L\\).

% Script: convect1d.m

clear all;

% Set-up grid
xL = -4;
xR =  4;
Nx = 40; % number of control volumes
x = linspace(xL,xR,Nx+1);

% Calculate midpoint values of x in each control volume
xmid = 0.5\*(x(1:Nx) + x(2:Nx+1));

% Calculate cell size in control volumes (assumed equal)
dx = x(2) - x(1);

% Set velocity
u = 1;

% Set final time
tfinal = 100;

% Set timestep
CFL = 0.5;
dt = CFL\*dx/abs(u);

% Set initial condition to U0 = exp(-x^2)
% Note: technically, we should average the initial
% distribution in each cell but I chose to just set
% the value of U in each control volume to the midpoint
% value of U0.

U = exp(-xmid.^2);
t = 0;

% Loop until t > tfinal
while (t < tfinal),

  Ubc = \[U(Nx), U, U(1)\]; % This enforces the periodic bc

  % Calculate the flux at each interface
  F =   0.5\*    u \*( Ubc(2:Nx+2) + Ubc(1:Nx+1)) ...
      - 0.5\*abs(u)\*( Ubc(2:Nx+2) - Ubc(1:Nx+1));

  % Calculate residual in each cell
  R = F(2:Nx+1) - F(1:Nx);

  % Forward Euler step
  U = U - (dt/dx)\*R;

  % Increment time
  t = t + dt;

  % Plot current solution
  stairs(x,\[U, U(Nx)\]);
  axis(\[xL, xR, -0.5, 1.5\]);
  grid on;
  drawnow;

end

% overlay exact solution
U = exp(-xmid.^2);
hold on;
stairs(x,\[U, U(Nx)\], 'r-');

Exercise
--------

Copy the MATLAB code above and determine which of the following timesteps (\\(\\Delta t\\)) is the largest that still remains stable.

Exercise 1

&nbsp; 0.04 &nbsp;

&nbsp; 0.07 &nbsp;

&nbsp; 0.10 &nbsp;

&nbsp; 0.20 &nbsp;

CheckShow Answer

Answer: The CFL condition (to be discussed in a later module) tells us that \\(\\Delta t = 0.20\\) is the largest timestep choice that will remain stable.

BackIntroduction to Finite Volume Methods ContinueFinite Volume Method in 2-D