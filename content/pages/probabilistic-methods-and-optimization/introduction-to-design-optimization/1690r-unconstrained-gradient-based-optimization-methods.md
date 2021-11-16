---
content_type: page
parent_title: 3.6 Introduction to Design Optimization
parent_uid: 6f317b0d-95c1-d32c-f178-c9fdbae632d2
title: 3.6 Introduction to Design Optimization
uid: da1cf617-8af1-53b1-4d4a-177f24979948
---

*   [<Gradient Based Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-gradient-based-optimization)
*   [3.6.1Design Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization)
*   [3.6.2Gradient Based Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-gradient-based-optimization)
*   [3.6.3Unconstrained Gradient-Based Optimization Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-unconstrained-gradient-based-optimization-methods)
*   [3.6.4Finite Difference Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-finite-difference-methods)
*   [3.6.5The 1d Search]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-the-1d-search)
*   [\>Finite Difference Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization/1690r-finite-difference-methods)

3.6.3 Unconstrained Gradient-Based Optimization Methods
-------------------------------------------------------

[Measurable Outcome 3.17]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO317)

**First-Order Methods:** use gradient information to calculate the search direction \\(S\\). Examples: steepest descent method, conjugate gradient method, quasi-Newton methods.

**Second-Order Methods:** use gradients and Hessian to calculate the search direction \\(S\\). Example: Newton method.

The required gradients and Hessian information can be computed using finite differences (as well as other methods). We will discuss this more in the next section.

Often, a constrained problem can be cast as an equivalent unconstrained problem and the resulting optimization problem is solved using a gradient based method for unconstrained problems. These unconstrained methods are embedded in many of the more complicated constrained optimization algorithms.

Steepest Descent Method
-----------------------

In the steepest descent method, we choose \\(S^ q = -\\nabla J(x^{q-1})\\) to be our search direction. If we use a sufficiently small step size, we are guaranteed that the objective function decreases when we move in this direction. The steepest descent algorithm is as follows:

*   Choose \\(x^0\\), set \\(x=x^0\\)
    
*   Repeat until converged:  
    
*   \\(S = -\\nabla J(x)\\)
    
*   Choose \\(\\alpha\\) to minimize \\(J(x+\\alpha S)\\)
    
*   \\(x = x + \\alpha S\\)
    

The step size \\(\\alpha\\) is chosen with a 1-D search (interpolation or Golden section). This may be an iterative process, so that step 2 may require multiple iterations. These iterations do not require additional evaluation of the gradient, and only the objective function value is used. The stepeest descent direction typically converges very slowly.

Conjugate Gradient Method
-------------------------

The conjugate gradient method is another popular gradient based method that only uses gradient information to choose the search direction. The conjugate gradient method uses the following search directions:

*   For the first iteration, use the steepest descent search direction: \\(S^1 = -\\nabla J(x^{0})\\)
    
*   For all subsequent steps, use \\(S^ q = -\\nabla J(x^{q-1}) + \\beta ^ q S^{q-1}\\) where \\(\\beta ^ q = \\frac{|\\nabla J(x^{q-1})|^2}{|\\nabla J(x^{q-2})|^2}\\)
    

The step size \\(\\alpha ^ q\\) is chosen in the same way it is for the steepest descent method. This choice of search direction results in succesive search directions that are conjugate, i.e.,

| \\\[S^{jT} H S^ k = 0\\\] | (3.71) 

The conjugate gradient method makes use of information from previous iterations without having to store a matrix. This greatly improves the convergence rate compared to the steepest descent method, which only uses information from the current iteration to choose the search direction.

Newton Method
-------------

The Newton Method makes use of the Hessian matrix to compute the search direction. In much the same way that the Newton-Raphson method determines stationary points of a set of nonlinear equations, the Newton method determines stationary points of the gradient of a function. The Taylor series of the objective function is given by:

| \\\[J(x) = J(x^0) + \\nabla J(x^0)^ T \\Delta x + \\Delta x^ T H(x^0) \\Delta x + \\cdots\\\] | (3.72) 

where \\(\\Delta x = x - x^0\\) and \\(H=\\nabla ^2 J\\).

If we differentiate the Taylor series expantion and neglect higher order terms, we have that:

| \\\[\\nabla J(x) \\approx \\nabla J(x^0) + H(x^0) \\Delta x\\\] | (3.73) 

At optimum, \\(\\nabla J(x)=0\\), so

| \\\[\\nabla J(x^0) + H(x^0) \\Delta x = 0 \\\\ \\Delta x = -H^{-1}(x^0)\\nabla J(x^0)\\\] | (3.74) 

If \\(J(x)\\) is quadratic, Newton's method gives exact solution in one iteration. If \\(J(x)\\) not quadratic (as is usually the case), we perform a Taylor series about new point and repeat until converged. Newton's method is an efficient technique if the optimization is started near the solution. Typically, the advantage of using Newton's method over other alternatives arises when we are near to an optimal solution.

We should note that the Hessian matrix \\(H\\) is not usually available analytically, and using finite differences to compute the Hessian is usually is too expensive. The solution to this problem are Quasi-Newton methods, which build up approximations to the inverse of the Hessian matrix using gradient information, giving improved convergence rates (quasi-second-order) at low computational cost.

BackGradient Based Optimization ContinueFinite Difference Methods