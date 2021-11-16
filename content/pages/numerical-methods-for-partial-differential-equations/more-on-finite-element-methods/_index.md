---
content_type: page
parent_title: 'Unit 2: Numerical Methods for Partial Differential Equations'
parent_uid: 125c58ac-6a34-5a7c-bba8-de2d3160cb8b
title: 2.10 More on Finite Element Methods
uid: 62673265-55df-f200-dae2-644697a179db
---

*   [<Calculation of the Stiffness Matrix]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-calculation-of-the-stiffness-matrix)
*   [2.10.1Gaussian Quadrature]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/more-on-finite-element-methods)
*   [2.10.2Boundary Conditions for Finite Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/more-on-finite-element-methods/1690r-boundary-conditions-for-finite-elements)
*   [\>Boundary Conditions for Finite Elements]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/more-on-finite-element-methods/1690r-boundary-conditions-for-finite-elements)

2.10.1 Gaussian Quadrature
--------------------------

[Measurable Outcome 2.14]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO214), [Measurable Outcome 2.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO217), [Measurable Outcome 2.18]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO218)

The finite element method requires the calculation of integrals over individual elements, for example,

| \\\[\\int \_{x\_{i}}^{x\_{i+1}} {\\phi \_ i}\_ x\\, k \\tilde{T}\_ x\\, dx, \\quad \\mbox{or} \\quad \\int \_{x\_{i}}^{x\_{i+1}} {\\phi \_ i}\\, f \\, dx.\\\] | (2.221) 

While in some settings these integrals can be calculated analytically, often they are too difficult. In this situation, numerical integration methods are used.

Gaussian quadrature is one of the most commonly applied numerical integration methods. Gaussian quadrature approximates an integral as the weighted sum of the values of its integrand. Consider integrating the general function \\(g(\\xi )\\), over the domain \\(-1 \\leq \\xi \\leq 1\\). Gaussian quadrature approximates this integral as a weighted sum of the values of \\(g\\) evaluated at discrete points over the domain:

| \\\[\\int \_{-1}^{+1} g(\\xi )\\, d\\xi \\approx \\sum \_{q=1}^{N\_ q} \\alpha \_ q g(\\xi \_ q). \\label{equ:gq}\\\] | (2.222) 

Here we have used \\(N\_ q\\) quadrature points (i.e., integrand evaluations). \\(\\xi \_ q\\) is the location of the \\(q\\)th quadrature point in the domain and \\(\\alpha \_ q\\) is the corresponding quadrature weight.

Note that Gaussian quadrature rules are developed for specific integration limits, in this case between \\(\\xi = -1\\) to \\(+1\\). Thus, for integration in an element, we will need to transform from \\(x\\) to \\(\\xi\\).

Gaussian quadrature integration rules are determined by requiring exact integration of polynomial integrands, i.e., by considering integration of the function

| \\\[g(\\xi ) = c\_0 + c\_1\\xi + c\_2\\xi ^2 + c\_3\\xi ^3 + \\cdots + c\_ M\\xi ^ M,\\\] | (2.223) 

for all values of the \\(c\_ m\\) coefficients. Note that

| \\\[\\int \_{-1}^{+1} \\xi ^ m\\, d\\xi = \\left\\{ \\begin{array}{cl} 0 & \\mbox{if } m = \\mbox{odd} \\\\\[0.1in\] \\frac{2}{m+1} & \\mbox{if } m = \\mbox{even} \\end{array}\\right.\\\] | (2.224) 

This gives us the result:

| \\\[\\int \_{-1}^{+1} \\sum \_{m=0}^{M} c\_ m\\xi ^ m\\, d\\xi = 2\\left(c\_0 + \\frac{1}{3}c\_2 + \\frac{1}{5}c\_4 + \\cdots \\right). \\label{equ:poly\_ integral}\\\] | (2.225) 

The \\(N\_ q = 1\\) Quadrature Rule
-----------------------------------

For \\(N\_ q=1\\), the quadrature rule is

| \\\[\\int \_{-1}^{+1} g(\\xi )\\, d\\xi \\approx \\alpha \_1 g(\\xi \_1).\\\] | (2.226) 

Now, using Equation ([2.225](javascript: void(0))), we determine the highest order polynomial that is integrable by a single quadrature point:

| &nbsp; | \\(\\displaystyle 2\\left(c\_0 + \\frac{1}{3}c\_2 + \\frac{1}{5}c\_4 + \\cdots \\right)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\alpha \_1 g(\\xi \_1)\\) | &nbsp; | (2.227) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\alpha \_1 \\left(c\_0 + c\_1\\xi \_1 + c\_2\\xi \_1^2 + c\_3\\xi \_1^3 + \\cdots + c\_ M\\xi \_1^ M\\right).\\) | &nbsp; | (2.228) 

Matching term by term gives

| &nbsp; | \\(\\displaystyle c\_0\\) | \\(\\displaystyle :\\) | \\(\\displaystyle 2 = \\alpha \_1 \\qquad \\Rightarrow \\alpha \_1 = 2,\\) | &nbsp; | (2.229) |
| &nbsp; | \\(\\displaystyle c\_1\\) | \\(\\displaystyle :\\) | \\(\\displaystyle 0 = \\alpha \_1\\xi \_1 \\qquad \\Rightarrow \\xi \_1 = 0.\\) | &nbsp; | (2.230) 

Then, checking the \\(c\_2\\) term shows that it is not integrated exactly. So, with one point, a linear polynomial is the highest order polynomial that can be evaluated exactly and the quadrature rule is

| \\\[\\int \_{-1}^{+1} g(\\xi )\\, d\\xi \\approx \\alpha \_1 g(\\xi \_1), \\qquad \\alpha \_1 = 2, \\quad \\xi \_1 = 0.\\\] | (2.231) 

The \\(N\_ q = 2\\) Quadrature Rule
-----------------------------------

For \\(N\_ q=2\\), the quadrature rule is,

| \\\[\\int \_{-1}^{+1} g(\\xi )\\, d\\xi \\approx \\alpha \_1 g(\\xi \_1) + \\alpha \_2 g(\\xi \_2).\\\] | (2.232) 

Again using Equation ([2.225](javascript: void(0))), we determine the highest order polynomial that is integrable by two quadrature points:

| &nbsp; | \\(\\displaystyle 2\\left(c\_0 + \\frac{1}{3}c\_2 + \\frac{1}{5}c\_4 + \\cdots \\right)\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\alpha \_1 g(\\xi \_1) + \\alpha \_2 g(\\xi \_2)\\) | &nbsp; | (2.233) |
| &nbsp; | \\(\\displaystyle =\\) | \\(\\displaystyle \\alpha \_1 \\left(c\_0 + c\_1\\xi \_1 + c\_2\\xi \_1^2 + c\_3\\xi \_1^3 + \\cdots + c\_ M\\xi \_1^ M\\right) +\\) | &nbsp; | (2.234) |
| &nbsp; | \\(\\displaystyle \\alpha \_2 \\left(c\_0 + c\_1\\xi \_2 + c\_2\\xi \_2^2 + c\_3\\xi \_2^3 + \\cdots + c\_ M\\xi \_2^ M\\right).\\) | &nbsp; | (2.235) 

Matching the first four terms gives the following constraints:

| &nbsp; | \\(\\displaystyle c\_0\\) | \\(\\displaystyle :\\) | \\(\\displaystyle 2 = \\alpha \_1 + \\alpha \_2,\\) | &nbsp; | (2.236) |
| &nbsp; | \\(\\displaystyle c\_1\\) | \\(\\displaystyle :\\) | \\(\\displaystyle 0 = \\alpha \_1\\xi \_1 + \\alpha \_2\\xi \_2,\\) | &nbsp; | (2.237) |
| &nbsp; | \\(\\displaystyle c\_2\\) | \\(\\displaystyle :\\) | \\(\\displaystyle \\frac{2}{3} = \\alpha \_1\\xi \_1^2 + \\alpha \_2\\xi \_2^2,\\) | &nbsp; | (2.238) |
| &nbsp; | \\(\\displaystyle c\_3\\) | \\(\\displaystyle :\\) | \\(\\displaystyle 0 = \\alpha \_1\\xi \_1^3 + \\alpha \_2\\xi \_2^3.\\) | &nbsp; | (2.239) 

These constraints can be met by choosing

| \\\[\\alpha \_1 = \\alpha \_2 = 1, \\quad \\xi \_1 = -\\frac{1}{\\sqrt {3}}, \\quad \\xi \_2 = \\frac{1}{\\sqrt {3}}.\\\] | (2.240) 

Thus, this rule will integrate cubic polynomials exactly.

Calculation of Forcing Integral with Gauss Quadrature
-----------------------------------------------------

We wish to apply Gaussian quadrature to evaluate the forcing integral,

| \\\[\\int \_{x\_{i}}^{x\_{i+1}} {\\phi \_ i}\\, f \\, dx. \\label{equ:wf}\\\] | (2.241) 

Remember that this is the last term in the definition of the weighted residual for our diffusion problem, Equation ([2.211](javascript: void(0))).

To do this, we first transform between the \\(x\\) and \\(\\xi\\) space. For this integral in element \\(i\\), the transformation is

| \\\[x(\\xi ) = x\_{i} + \\frac{1}{2}(1+\\xi )(x\_{i+1}-x\_ i), \\quad \\Rightarrow dx = \\frac{1}{2}(x\_{i+1}-x\_ i)d\\xi .\\\] | (2.242) 

Substitution in the forcing integral gives

| \\\[\\int \_{x\_{i}}^{x\_{i+1}} \\phi \_ i \\, f \\, dx = \\int \_{-1}^{+1} \\frac{1}{2}(x\_{i+1}-x\_ i) \\phi \_ i \\, f \\, d\\xi , \\qquad \\Rightarrow \\qquad g(\\xi ) = \\frac{1}{2}(x\_{i+1}-x\_ i)\\, \\phi \_ i\[x(\\xi )\]\\, f\[x(\\xi )\].\\\] | (2.243) 

Note that the dependence of \\(\\phi \_ i\\) and \\(f\\) on \\(\\xi\\) is shown through the dependence of these functions on \\(x = x(\\xi )\\). However, for the basis functions, it is often easier to directly determine \\(\\phi \_ i\\) from \\(\\xi\\). For example, in the case of linear polynomial basis functions, the basis functions with element \\(i\\) can be written as

| &nbsp; | \\(\\displaystyle \\phi \_1(\\xi )\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{1}{2}(1-\\xi ),\\) | &nbsp; | (2.244) |
| &nbsp; | \\(\\displaystyle \\phi \_2(\\xi )\\) | \\(\\displaystyle =\\) | \\(\\displaystyle \\frac{1}{2}(1+\\xi ).\\) | &nbsp; | (2.245) 

Clearly, these functions vary linearly with \\(\\xi\\). \\(\\phi \_1(\\xi )\\) is one at \\(\\xi =-1\\) and decreases linearly to zero at \\(\\xi =+1\\). \\(\\phi \_2(\\xi )\\) is zero at \\(\\xi =-1\\) and increases linearly to one at \\(\\xi =+1\\).

The following is a MATLAB® script that uses Gaussian quadrature to evaluate the forcing integral and solve the problem described in Section [2.8.1]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/method-of-weighted-residuals). The number of points being used is set at the beginning of the script. Results for both 1-point and 2-point quadrature are shown in Figures [2.41]({{< baseurl >}}/resources/n5_nq1)\-[2.46]({{< baseurl >}}/resources/error_nq2) for \\(5\\) and \\(10\\) elements. While the 2-point quadrature rule has lower error than the 1-point rule, both appear to be second-order accurate since the errors reduce by nearly a factor of \\(4\\) for the factor 2 change in mesh size. Also, the results are no longer exact at the nodes like they were in Section [2.9.3]({{< baseurl >}}/pages/numerical-methods-for-partial-differential-equations/introduction-to-finite-elements/1690r-1-d-linear-elements-and-the-nodal-basis) (though the 2-point quadrature rules are quite close).

% FEM solver for d2T/dx2 + f = 0 where f = 50 exp(x)
%
% BC's: T(-1) = 100 and T(1) = 100.
%
% Gaussian quadrature is used in evaluating the forcing integral.
%
% Note: the finite element degrees of freedom are
%       stored in the vector T.

% Number of elements
nElem = 5;
x = linspace(-1,1,nElem+1);

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

% Set Dirichlet conditions at x=1
n1 = nElem+1;
K(n1,:)    = zeros(size(1,nElem+1));
K(n1, n1)  = 1.0;
F(n1)      = 100.0;

% Solve for solution
T = K\\F;


% Plot solution
figure(1);
plot(x,T,'\*-');
xlabel('x');
ylabel('T');

% For the exact solution, we need to use finer spacing to plot
% it correctly.  If we only plot it at the nodes of the FEM mesh,
% the exact solution would also look linear between the nodes.  To
% make sure there is always enough resolution relative to the FEM
% nodes, the size of the vector for plotting the exact solution is
% set to be 20 times the number of FEM nodes.
Npt = 20\*nElem+1;
xe = linspace(-1,1,Npt);
Te = -50\*exp(xe) + 50\*xe\*sinh(1) + 100 + 50\*cosh(1);
hold on; plot(xe,Te); hold off;

% Plot the error.  To do this, calculate the error on the same
% set of points in which the exact solution was plot.  This
% requires that the location of the point xx(i) be found in the
% FEM mesh to construct the true solution at this point by linearly
% interpolating between the two nodes of the FEM mesh.

Terr(1) = T(1) - Te(1);
h = x(2)-x(1);
for i = 2:Npt-1,
  xxi = xe(i);
  Tei = Te(i);
  j = floor((xxi-xe(1))/h) + 1;
  x0 = x(j);
  x1 = x(j+1);
  T0 = T(j);
  T1 = T(j+1);
  xi = 2\*(xxi - x0)/(x1-x0)-1;  % This gives xi between +/-1
  Ti = 0.5\*(1-xi)\*T0 + 0.5\*(1+xi)\*T1;
  Terr(i) = Ti - Tei;
end
Terr(Npt) = T(nElem+1) - Te(Npt);

figure(2);
plot(xe,Terr);
xlabel('x');
ylabel('Error');

![This graph shows two very similar lines, each with a single peak, that represent the exact solution and the finite element solution using Nq=1 point Gaussian quadrature with 5 elements.](BASEURL_PLACEHOLDER/resources/n5_nq1)

**Figure 2.41**: Comparison of finite element solution using \\(N\_ q=1\\) point Gaussian quadrature with \\(N=5\\) elements to the exact solution.

![This graph shows two very similar lines, each with a single peak, that represent the exact solution and the finite element solution using Nq=1 point Gaussian quadrature with 10 elements.](BASEURL_PLACEHOLDER/resources/n10_nq1)

**Figure 2.42**: Comparison of finite element solution using \\(N\_ q=1\\) point Gaussian quadrature with \\(N=10\\) elements to the exact solution.

![This graph shows two lines of inverted peaks representing the error between the exact and finite element solution with Gaussian quadrature using Nq=1 points. There are twice as many and smaller inverted peaks for the 5 element line than the 10 element line.](BASEURL_PLACEHOLDER/resources/error_nq1)

**Figure 2.43**: Error between exact solution and finite element solutions (\\(N=5\\) and \\(N=10\\)) with Gaussian quadrature using \\(N\_ q=1\\) points.

![This graph shows two very similar lines, each with a single peak, that represent the exact solution and the finite element solution using Nq=2 point Gaussian quadrature with 5 elements.](BASEURL_PLACEHOLDER/resources/n5_nq2)

**Figure 2.44**: Comparison of finite element solution using \\(N\_ q=2\\) point Gaussian quadrature with \\(N=5\\) elements to the exact solution.

![This graph shows two very similar lines, each with a single peak, that represent the exact solution and the finite element solution using Nq=2 point Gaussian quadrature with 10 elements.](BASEURL_PLACEHOLDER/resources/n10_nq2)

**Figure 2.45**: Comparison of finite element solution using \\(N\_ q=2\\) point Gaussian quadrature with \\(N=10\\) elements to the exact solution.

![This graph shows two lines of inverted peaks representing the error between the exact and finite element solution with Gaussian quadrature using Nq=1 points. There are twice as many and smaller inverted peaks for the 5 element line than the 10 element line. ](BASEURL_PLACEHOLDER/resources/error_nq2)

**Figure 2.46**: Error between exact solution and finite element solutions (\\(N=5\\) and \\(N=10\\)) with Gaussian quadrature using \\(N\_ q=2\\) points.

BackCalculation of the Stiffness Matrix ContinueBoundary Conditions for Finite Elements