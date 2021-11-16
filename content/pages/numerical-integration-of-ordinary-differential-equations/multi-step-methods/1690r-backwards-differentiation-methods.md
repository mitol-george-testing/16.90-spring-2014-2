---
content_type: page
parent_title: 1.8 Multi-Step Methods
parent_uid: 67717326-dffb-7444-5162-101fd9a9ec91
title: 1.8 Multi-Step Methods
uid: 998bd383-00b6-8dbd-2d38-c251f8262e37
---

*   [<Adams-Moulton Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-adams-moulton-methods)
*   [1.8.1Adams-Bashforth Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods)
*   [1.8.2Adams-Moulton Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-adams-moulton-methods)
*   [1.8.3Backwards Differentiation Methods]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-methods)
*   [1.8.4Backwards Differentiation Excercise]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-excercise)
*   [\>Backwards Differentiation Excercise]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/multi-step-methods/1690r-backwards-differentiation-excercise)

1.8.3 Backwards Differentiation Methods
---------------------------------------

[Measurable Outcome 1.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO112), [Measurable Outcome 1.15]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO115), [Measurable Outcome 1.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO117), [Measurable Outcome 1.18]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO118), [Measurable Outcome 1.19]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO119)

Backwards differentiation methods are some of the best multi-step methods for stiff problems. The backwards differentiation formulae are of the form,

| \\\[v^{n+1} + \\sum \_{i=1}^ s \\alpha \_ i v^{n+1-i} = {\\Delta t}\\beta \_0 f^{n+1}. \\label{equ:bd}\\\] | (1.138) 

The coefficients for the first through fourth order methods are given in the table below.

|  {{< br >}}{{< br >}} \\(p\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\alpha \_1\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\alpha \_2\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\alpha \_3\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\alpha \_4\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\beta \_0\\) {{< br >}}{{< br >}}  |
|  {{< br >}}{{< br >}} 1 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \-1 {{< br >}}{{< br >}}  | &nbsp; |  {{< br >}}{{< br >}} 1 {{< br >}}{{< br >}}  |
|  {{< br >}}{{< br >}} 2 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{4}{3}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{1}{3}\\) {{< br >}}{{< br >}}  | &nbsp; |  {{< br >}}{{< br >}} \\(\\frac{2}{3}\\) {{< br >}}{{< br >}}  |
|  {{< br >}}{{< br >}} 3 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{18}{11}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{9}{11}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{2}{11}\\) {{< br >}}{{< br >}}  | &nbsp; |  {{< br >}}{{< br >}} \\(\\frac{6}{11}\\) {{< br >}}{{< br >}}  |
|  {{< br >}}{{< br >}} 4 {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{48}{25}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{36}{25}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(-\\frac{16}{25}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{3}{25}\\) {{< br >}}{{< br >}}  |  {{< br >}}{{< br >}} \\(\\frac{12}{25}\\) {{< br >}}{{< br >}}  

**Table 4**: Coefficients for backward differentiation methods

The stability boundary for these methods are shown below. As can be seen, all of these methods are stable everywhere on the negative real axis, and are mostly stable in the left-half plane in general. Thus, backwards differentiation work well for stiff problems in which stong damping is present.

![This figure shows the overlapping backwards differentiation stability regions for p=1 through p=4 method.](BASEURL_PLACEHOLDER/resources/bd_stab)

**Figure 1.21**: Backwards differentiation stability regions for \\(p=1\\) through \\(p=4\\) method. Note: interior of curves is unstable region.

MATLAB®'s ODE Integrators
-------------------------

MATLAB has a a set of tools for integration of ODE's. We will briefly look at two of them: **ode45** and **ode15s**. **ode45** is designed to solve problems that are not stiff while **ode15s** is intended for stiff problems. **ode45** is based on a four and five-stage Runge-Kutta integration (discussed in Section [1.9]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/runge-kutta-methods)), while **ode15s** is based on a range of highly stable implicit integration formulas (one option when using **ode15s** is to use the backwards differentiation formulas). As a short illustration on how these MATLAB ODE integrators are implemented, the following script solves the one-dimensional diffusion problem from Section [1.7.1]({{< baseurl >}}/pages/numerical-integration-of-ordinary-differential-equations/stiffness-and-implicit-methods) using either **ode45** or **ode15s**. The specific problem we consider here is a bar which is initially at a temperature \\(T\_{init} = 400 K\\) and at \\(t=0\\), the temperature at the left and right ends is suddenly raised to \\(800 K\\) and \\(1000 K\\), respectively.

% MATLAB script: dif1d\_main.m
%
% This code solve the one-dimensional heat diffusion equation
% for the problem of a bar which is initially at T=Tinit and
% suddenly the temperatures at the left and right change to
% Tleft and Tright.
%
% Upon discretization in space by a finite difference method,
% the result is a system of ODE's of the form,
%
% u\_t = Au + b
%
% The code calculates A and b.  Then, uses one of MATLAB's
% ODE integrators, either ode45 (which is based on a Runge-Kutta
% method and is not designed for stiff problems) or ode15s (which
% is based on an implicit method and is designed for stiff problems).
%

clear all; close all;

sflag = input('Use stiff integrator? (1=yes, \[default=no\]): ');

% Set non-dimensional thermal coefficient
k   = 1.0; % this is really k/(rho\*cp)

% Set length of bar
L = 1.0; % non-dimensional

% Set initial temperature
Tinit = 400;

% Set left and right temperatures for t>0
Tleft = 800;
Tright = 1000;

% Set up grid size
Nx = input(\['Enter number of divisions in x-direction: \[default=' ...
            '51\]'\]);
if (isempty(Nx)),
  Nx = 51;
end

h  = L/Nx;
x  = linspace(0,L,Nx+1);

% Calculate number of iterations (Nmax) needed to iterate to t=Tmax
Tmax = 0.5;

% Initialize a sparse matrix to hold stiffness & identity matrix
A = spalloc(Nx-1,Nx-1,3\*(Nx-1));
I = speye(Nx-1);

% Calculate stiffness matrix

for ii = 1:Nx-1,

  if (ii > 1),
    A(ii,ii-1) = k/h^2;
  end

  if (ii < Nx-1),
    A(ii,ii+1) = k/h^2;
  end

  A(ii,ii) = -2\*k/h^2;

end

% Set forcing vector
b = zeros(Nx-1,1);
b(1)    = k\*Tleft/h^2;
b(Nx-1) = k\*Tright/h^2;

% Set initial vector
v0 = Tinit\*ones(1,Nx-1);

if (sflag == 1),

  % Call ODE15s
  options = odeset('Jacobian',A);
  \[t,v\] = ode15s(@dif1d\_fun,\[0 Tmax\],v0,options,A,b);

else

  % Call ODE45
  \[t,v\] = ode45(@dif1d\_fun,\[0 Tmax\],v0,\[\],A,b);

end

% Get midpoint value of T and plot vs. time
Tmid = v(:,floor(Nx/2));
plot(t,Tmid);
xlabel('t');
ylabel('T at midpoint');

As can be seen, this script pre-computes the linear system \\(A\\) and the column vector \\(b\\) since the forcing function for the one-dimensional diffusion problem can be written as the linear function, \\(f = Av + b\\). Then, when calling either ODE integrator, the function which returns \\(f\\) is the first argument in the call and is named, **dif1d\_fun**. This function is given below:

% MATLAB function: dif1d\_fun.m
%
% This routine returns the forcing term for
% a one-dimensional heat diffusion problem
% that has been discretized by finite differences.
% Note that the matrix A and the vector b are pre-computed
% in the main driver routine, dif1d\_main.m, and passed
% to this function.  Then, this function simply returns
% f(v) = A\*v + b.  So, in reality, this function is
% not specific to 1-d diffusion.

function \[f\] = dif1d\_fun(t, v, A, b)

f = A\*v + b;

As can be seen from **dif1d\_fun**, \\(A\\) and \\(b\\) have been passed into the function and thus the calculation of \\(f\\) simply requires the multiplication of \\(v\\) by \\(A\\) and the addition of \\(b\\).

The major difference between the implementation of the ODE integrators in MATLAB and our discussions is that MATLAB's implementations are adaptive. Specifically, MATLAB's integrators estimate the error at each iteration and then adjust the timestep to either improve the accuracy (i.e. by decreasing the timestep) or efficiency (i.e. by increasing the timestep).

The results for the stiff integrator, **ode15s** are shown in Figure [1.22]({{< baseurl >}}/resources/dif1d_ode15s).

![The graph shows the rapidly increasing temperature evolution using MATLAB's ode15s integrator.](BASEURL_PLACEHOLDER/resources/dif1d_ode15s)

**Figure 1.22**: Temperature evolution at the middle of bar with suddenly raised end temperatures using MATLAB's **ode15s** integrator

![The graph shows the rapidly increasing temperature evolution using MATLAB's ode45 integrator.](BASEURL_PLACEHOLDER/resources/dif1d_ode45)

**Figure 1.23**: Temperature evolution at the middle of bar with suddenly raised end temperatures using MATLAB's **ode45** integrator

![The graph shows a zoomed in version of the rapidly increasing temperature evolution using MATLAB's ode45 integrator, which more easily display the small scale oscillations.](BASEURL_PLACEHOLDER/resources/dif1d_ode45_zoom)

**Figure 1.24**: Temperature evolution at the middle of bar with suddenly raised end temperatures using MATLAB's **ode45** integrator (zoomed version).

These results look as expected (note: in integrating from \\(t=0\\) to \\(t=0.5\\), a total of 64 timesteps were taken).

The results for the non-stiff integrator are shown in Figure [1.23]({{< baseurl >}}/resources/dif1d_ode45) and in a zoomed view in Figure [1.24]({{< baseurl >}}/resources/dif1d_ode45_zoom). The presence of small scale oscillations can be clearly observed in the **ode45** results. These oscillations are a result of the large negative eigenvalues which require small \\({\\Delta t}\\) to maintain stability. Since the **ode45** method is adaptive, the timestep automatically decreases to maintain stability, but the oscillatory results clearly show that the stability is barely achieved. Also, as a measure of the relative inefficiency of the **ode45** integrator for this stiff problem, note that 6273 timesteps were required to integrate from \\(t=0\\) to \\(t=0.5\\).

One final concern regarding the efficiency of the stiff integrator **ode15s**. In order for this method to work in an efficient manner for large systems of equations such as in this example, it is very important that the Jacobian matrix, \\({\\partial f}/{\\partial u}\\) be provided to MATLAB. If this is not done, then **ode15s** will construct an approximation to this derivative matrix using finite differences and for large systems, this will become a significant cost. In the script **dif1d\_main**, the Jacobian is communicated to the **ode15s** integrator using the **odeset** routine. Note: **ode45** is an explicit method and does not need the Jacobian so it is not provided in that case.

BackAdams-Moulton Methods ContinueBackwards Differentiation Excercise