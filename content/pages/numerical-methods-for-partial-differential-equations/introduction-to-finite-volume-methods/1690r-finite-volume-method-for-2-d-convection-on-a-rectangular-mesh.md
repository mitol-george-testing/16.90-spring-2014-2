---
content_type: page
parent_title: 2.5 Introduction to Finite Volume Methods
parent_uid: 3d8df8b8-2291-7094-b5a6-9893808a75cc
title: 2.5 Introduction to Finite Volume Methods
uid: a9d8dcc7-e873-f01e-6dc3-6f07884b2f23
---

*   [<Finite Volume Method in 2-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-in-2-d)
*   [2.5.1Finite Volume Method in 1-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods)
*   [2.5.2Finite Volume Method Applied to 1-D Convection]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-applied-to-1-d-convection)
*   [2.5.3Finite Volume Method in 2-D]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-in-2-d)
*   [2.5.4Finite Volume Method for 2-D Convection on a Rectangular Mesh]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-2-d-convection-on-a-rectangular-mesh)
*   [2.5.5Finite Volume Method for Nonlinear Systems]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-nonlinear-systems)
*   [\>Finite Volume Method for Nonlinear Systems]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-volume-methods/1690r-finite-volume-method-for-nonlinear-systems)

2.5.4 Finite Volume Method for 2-D Convection on a Rectangular Mesh
-------------------------------------------------------------------

[Measurable Outcome 2.1]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO21), [Measurable Outcome 2.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO22), [Measurable Outcome 2.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO23), [Measurable Outcome 2.4]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO24)

% Script: convect2d.m

close all;
clear all;

% Specify x range and number of points
x0 = -2;
x1 =  2;
Nx = 40;

% Specify y range and number of points
y0 = -2;
y1 =  2;
Ny = 40;

% Construct mesh
x       = linspace(x0,x1,Nx+1);
y       = linspace(y0,y1,Ny+1);
\[xg,yg\] = ndgrid(x,y);

% Construct mesh needed for plotting
xp = zeros(4,Nx\*Ny);
yp = zeros(4,Nx\*Ny);
n = 0;
for j = 1:Ny,
  for i = 1:Nx,

    n = n + 1;
    xp(1,n) = x(i);
    yp(1,n) = y(j);

    xp(2,n) = x(i+1);
    yp(2,n) = y(j);

    xp(3,n) = x(i+1);
    yp(3,n) = y(j+1);

    xp(4,n) = x(i);
    yp(4,n) = y(j+1);

  end
end

% Calculate midpoint values in each control volume
xmid = 0.5\*(x(1:Nx) + x(2:Nx+1));
ymid = 0.5\*(y(1:Ny) + y(2:Ny+1));

\[xmidg,ymidg\] = ndgrid(xmid,ymid);

% Calculate cell size in control volumes (assumed equal)
dx = x(2) - x(1);
dy = y(2) - y(1);
A  = dx\*dy;

% Set velocity
u = 1;
v = 1;

% Set final time
tfinal = 10;

% Set timestep
CFL = 1.0;
dt = CFL/(abs(u)/dx + abs(v)/dy);

% Set initial condition to U0 = exp(-x^2 - 20\*y^2)
% Note: technically, we should average the initial
% distribution in each cell but I chose to just set
% the value of U in each control volume to the midpoint
% value of U0.
U = exp(-xmidg.^2 - 20\*ymidg.^2);
t = 0;


% Loop until t > tfinal
while (t < tfinal),

  % The following implement the bc's by creating a larger array
  % for U and putting the appropriate values in the first and last
  % columns or rows to set the correct bc's
  Ubc(2:Nx+1,2:Ny+1) = U; % Copy U into Ubc
  Ubc(   1,2:Ny+1)   = U(Nx, :); % Periodic bc
  Ubc(Nx+2,2:Ny+1)   = U( 1, :); % Periodic bc
  Ubc(2:Nx+1,   1)   = U( :,Ny); % Periodic bc
  Ubc(2:Nx+1,Ny+2)   = U( :, 1); % Periodic bc

  % Calculate the flux at each interface

  % First the i interfaces
  F =   0.5\*    u \*( Ubc(2:Nx+2,2:Ny+1) + Ubc(1:Nx+1,2:Ny+1)) ...
      - 0.5\*abs(u)\*( Ubc(2:Nx+2,2:Ny+1) - Ubc(1:Nx+1,2:Ny+1));

  % Now the j interfaces
  G =   0.5\*    v \*( Ubc(2:Nx+1,2:Ny+2) + Ubc(2:Nx+1,1:Ny+1)) ...
      - 0.5\*abs(v)\*( Ubc(2:Nx+1,2:Ny+2) - Ubc(2:Nx+1,1:Ny+1));

  % Add contributions to residuals from fluxes
  R = (F(2:Nx+1,:) - F(1:Nx,:))\*dy + (G(:,2:Ny+1) - G(:,1:Ny))\*dx;

  % Forward Euler step
  U = U - (dt/A)\*R;

  % Increment time
  t = t + dt;

  % Plot current solution
  Up = reshape(U,1,Nx\*Ny);
  clf;
  \[Hp\] = patch(xp,yp,Up);
  set(Hp,'EdgeAlpha',0);
  axis('equal');
  caxis(\[0,1\]);
  colorbar;
  drawnow;

end

Exercise
--------

Copy the MATLAB® code above and determine which of the following timesteps (\\(\\Delta t\\)) is the largest that still remains stable.

Exercise 1

&nbsp; 0.04 &nbsp;

&nbsp; 0.05 &nbsp;

&nbsp; 0.10 &nbsp;

&nbsp; 0.13 &nbsp;

CheckShow Answer

Answer: The CFL condition (to be discussed in a later module) tells us that \\(\\Delta t = 0.05\\) is the largest timestep choice that will remain stable.

BackFinite Volume Method in 2-D ContinueFinite Volume Method for Nonlinear Systems