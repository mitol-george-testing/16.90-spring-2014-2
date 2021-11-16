---
content_type: page
parent_title: 2.10 More on Finite Element Methods
parent_uid: 62673265-55df-f200-dae2-644697a179db
title: 2.10 More on Finite Element Methods
uid: 365c70a7-4666-ed1c-d140-8aeb96bff4a6
---

*   [<More on Finite Element Methods]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/more-on-finite-element-methods)
*   [2.10.1Gaussian Quadrature]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/more-on-finite-element-methods)
*   [2.10.2Boundary Conditions for Finite Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/more-on-finite-element-methods/1690r-boundary-conditions-for-finite-elements)
*   [\>The Finite Element Method for Two-Dimensional Diffusion]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/the-finite-element-method-for-two-dimensional-diffusion)

2.10.2 Boundary Conditions for Finite Elements
----------------------------------------------

[Measurable Outcome 2.19]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO219), [Measurable Outcome 2.20]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO220)

Boundary conditions generally fall into one of three types:

*   Set \\(\\tilde{T}\\) at the boundary (known as a Dirichlet boundary condition). For heat transfer problems, this type of boundary condition occurs when the temperature is known at some portion of the boundary.
    
*   Set \\(\\tilde{T}\_{x}\\) at the boundary (known as a Neumann boundary condition). For heat transfer problems, this type of boundary condition occurs when the heat transfer rate is known at the boundary. For example, an adiabatic boundary would require that \\(\\tilde{T}\_{x}=0\\).
    
*   Set \\(\\alpha \_0\\tilde{T} + \\alpha \_1 \\tilde{T}\_{x}\\) at the boundary (known as a Robin boundary condition) where \\(\\alpha \_0\\) and \\(\\alpha \_1\\) do not depend on the temperature. For heat transfer problems, this type of boundary condition occurs when modeling convection (we will see this in the convective boundary condition example below).
    

Convection Boundary Condition for Heat Transfer
-----------------------------------------------

Consider the flow of air over a solid object with the velocity and temperature of the external air being \\(U\_{ext}\\) and \\(T\_{ext}\\), respectively. Aligning the \\(x\\)-direction into the surface of the object, then the heat transfer rate at the surface is

| \\\[q\_{wall} = -k T\_ x, \\label{equ:qwall}\\\] | (2.246) 

where \\(T(x)\\) is the temperature inside the solid and \\(k\\) is the thermal conductivity of the solid. A common approach to modeling the heat transfer into the solid as a result of the airflow is based on specifying a heat transfer coefficient for the airflow, \\(h\_{ext}\\), which is related to the heat transfer rate by

| \\\[h\_{ext} \\equiv \\frac{q\_{wall}}{T\_{ext}-T\_{wall}}. \\label{equ:hdef}\\\] | (2.247) 

Note that \\(h\_{ext}\\) is generally a function of the external velocity and other flow properties. Combining Equations ([2.246](javascript: void(0))) and ([2.247](javascript: void(0))) gives the following boundary condition at the surface of the solid,

| \\\[-k T\_ x = h\_{ext}\\left(T\_{ext}-T\_{wall}\\right), \\label{equ:convectbc}\\\] | (2.248) 

where \\(T\_{wall}\\) is the temperature of the solid at its surface. This equation can be re-arranged into the Robin boundary condition form,

| \\\[-k T\_ x + h\_{ext} T\_{wall} = h\_{ext}T\_{ext}.\\\] | (2.249) 

Implementation of Dirichlet Boundary Conditions
-----------------------------------------------

To demonstrate the implementation of a Dirichlet boundary condition, suppose that the value of the temperature is known at \\(x=-L/2\\), specifically,

| \\\[T(-L/2) = T\_{left}.\\\] | (2.250) 

This condition is set by forcing the corresponding nodal degree of freedom to be the desired value. At \\(x=-L/2\\), the corresponding nodal degree of freedom would be \\(a\_1\\) (the value of the temperature at the first node), thus, the boundary condition is implemented as

| \\\[a\_1 = T\_{left}.\\\] | (2.251) 

Implementation of Neumann Boundary Conditions
---------------------------------------------

To demonstrate the implementation of a Neumann boundary condition, suppose that the heat transfer rate is known at \\(x=L/2\\), specifically,

| \\\[-k T\_ x(L/2) = q\_{right}.\\\] | (2.252) 

This condition is enforced through the weighted residual for the last node, \\(i=N+1\\). Specifically,

| \\\[R\_{N+1} = \\left\[\\phi \_{N+1}\\, k \\tilde{T}\_ x\\right\]^{L/2}\_{-L/2} - \\int \_{-L/2}^{L/2} {\\phi \_{N+1}}\_ x\\, k \\tilde{T}\_ x\\, dx + \\int \_{-L/2}^{L/2} \\phi \_{N+1} f\\, dx.\\\] | (2.253) 

Because \\(\\phi \_{N+1}(x)\\) is zero except in the last element, this weighted residual reduces to

| \\\[R\_{N+1} = \\left.\\left(\\phi \_{N+1} k \\tilde{T}\_ x\\right)\\right&#124;\_{x=x\_{N+1}} - \\int \_{x\_{N}}^{x\_{N+1}} {\\phi \_{N+1}}\_ x\\, k \\tilde{T}\_ x\\, dx + \\int \_{x\_{N}}^{x\_{N+1}} \\phi \_{N+1} f\\, dx.\\\] | (2.254) 

The two integral terms are calculated in the standard manner. The first term is where the Neumann boundary condition is set through substitution of \\(-k \\tilde{T}\_ x = q\_{right}\\). Specifically, the weighted residual becomes

| \\\[R\_{N+1} = -\\phi \_{N+1}(x\_{N+1})q\_{right} - \\int \_{x\_{N}}^{x\_{N+1}} {\\phi \_{N+1}}\_ x\\, k \\tilde{T}\_ x\\, dx + \\int \_{x\_{N}}^{x\_{N+1}} \\phi \_{N+1} f\\, dx.\\\] | (2.255) 

Note that the boundary term, \\(-\\phi \_{N+1}(x\_{N+1})q\_{right}\\) does not depend on the temperature and thus this boundary condition does not impact the stiffness matrix.

Implementation of Robin Boundary Conditions
-------------------------------------------

To demonstrate the implementation of a Robin boundary condition, suppose that a convective heat transfer boundary condition were to be set at \\(x=L/2\\), specifically,

| \\\[-k T\_ x(L/2) = h\_{ext}\\left\[T\_{ext}-T(L/2)\\right\].\\\] | (2.256) 

Following the basic process outlined in the Neumann boundary condition, the weighted residual for \\(i=N+1\\) is

| \\\[R\_{N+1} = \\left.\\left(\\phi \_{N+1} k \\tilde{T}\_ x\\right)\\right&#124;\_{x=x\_{N+1}} - \\int \_{x\_{N}}^{x\_{N+1}} {\\phi \_{N+1}}\_ x\\, k \\tilde{T}\_ x\\, dx + \\int \_{x\_{N}}^{x\_{N+1}} \\phi \_{N+1} f\\, dx.\\\] | (2.257) 

Substituting \\(-k \\tilde{T}\_ x = h\_{ext}\\left\[T\_{ext}-\\tilde{T}(x\_{N+1})\\right\]\\) in the boundary term gives

| \\\[R\_{N+1} = -\\phi \_{N+1}(x\_{N+1})h\_{ext}\\left\[T\_{ext}-\\tilde{T}(x\_{N+1})\\right\] - \\int \_{x\_{N}}^{x\_{N+1}} {\\phi \_{N+1}}\_ x\\, k \\tilde{T}\_ x\\, dx + \\int \_{x\_{N}}^{x\_{N+1}} \\phi \_{N+1} f\\, dx.\\\] | (2.258) 

As opposed to the Neumann boundary condition, the Robin boundary condition implementation does introduce a new dependence on the solution, specifically on \\(\\tilde{T}(x\_{N+1})\\). This will cause a change in the stiffness matrix. Furthermore, the \\(T\_{ext}\\) term will alter the right-hand side vector in the FEM numerical implementation.

Boundary Condition Implementation Details
-----------------------------------------

In class, we will discuss the details of the implementation of the boundary conditions into a computer program using the following MATLAB® script.

% FEM solver for k d2T/dx2 + f = 0 where f = 50 exp(x)
%
% Thermal conductivity is set to one, k=1.
%
% BC's:
%
% At x=-1:   T(-1) = 100   (Dirichlet)
%
% At x=1, two options exist:
%
%            Specified heat transfer: dT/dX = qright
%
%            Convection: -k dT/dx = hext \* (Text - T(1))
%
% The choice of which bc to use is made through RightBC.
% If RightBC = 0, heat transfer rate is specified.  Otherwise,
% a convection BC is applied.
%
% Gaussian quadrature is used in evaluating the forcing integral.
%
% Note: the finite element degrees of freedom are
%       stored in the vector, T.

clear all;

% Number of elements
nElem = 5;
x = linspace(-1,1,nElem+1);

% Set RightBC info
RightBC = 1;
if (RightBC == 0),
  qright = 0;
else,
  hext = 10;
  Text = 100;
end

% Set quadrature rule
Nq = 2;
if (Nq == 1),
  alphaq(1) = 2.0; xiq(1) = 0.0;
elseif (Nq == 2),
  alphaq(1) = 1.0; xiq(1) = -1/sqrt(3);
  alphaq(2) = 1.0; xiq(2) =  1/sqrt(3);
else
  fprintf('Error: Unknown quadrature rule (Nq = %i)\\n',Nq);
  return;
end

% Zero stiffness matrix
K = zeros(nElem+1, nElem+1);
F = zeros(nElem+1, 1);

% Loop over all elements and calculate stiffness and residuals
for elem = 1:nElem,

  n1 = elem;
  n2 = elem+1;

  x1 = x(n1);
  x2 = x(n2);

  dx = x2 - x1;

  % Add contribution to n1 weighted residual due to n1 function
  K(n1, n1) = K(n1, n1) - (1/dx);

  % Add contribution to n1 weighted residual due to n2 function
  K(n1, n2) = K(n1, n2) + (1/dx);

  % Add contribution to n2 weighted residual due to n1 function
  K(n2, n1) = K(n2, n1) + (1/dx);

  % Add contribution to n2 weighted residual due to n2 function
  K(n2, n2) = K(n2, n2) - (1/dx);

  % Evaluate forcing term using quadrature
  for nn = 1:Nq,

    % Get xi location of quadrature point
    xi = xiq(nn);

    % Calculate x location of quadrature point
    xq = x1 + 0.5\*(1+xi)\*dx;

    % Calculate f
    f = 50\*exp(xq);

    % Calculate phi1 and phi2
    phi1 = 0.5\*(1-xi);
    phi2 = 0.5\*(1+xi);

    % Add forcing term to n1 weighted residual
    F(n1) = F(n1) - alphaq(nn)\*0.5\*phi1\*f\*dx;

    % Add forcing term to n2 weighted residual
    F(n2) = F(n2) - alphaq(nn)\*0.5\*phi2\*f\*dx;

  end

end


% Set Dirichlet conditions at x=-1
n1 = 1;
K(n1,:)    = zeros(size(1,nElem+1));
K(n1, n1)  = 1.0;
F(n1)      = 100.0;


% Set boundary condition at x=1
n1 = nElem+1;
if (RightBC == 0), % Specify heat transfer rate (Neumann)

  F(n1)     = F(n1) + qright;

else, % Convective

  K(n1,n1)  = K(n1,n1) + hext;
  F(n1)     = F(n1) + hext\*Text;

end


% Solve for solution
T = K\\F;


% Plot solution
plot(x,T,'\*-');
xlabel('x');
ylabel('T');

BackMore on Finite Element Methods ContinueThe Finite Element Method for Two-Dimensional Diffusion