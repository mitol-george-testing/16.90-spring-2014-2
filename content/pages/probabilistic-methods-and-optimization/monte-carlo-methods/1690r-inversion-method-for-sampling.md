---
content_type: page
parent_title: 3.3 Monte Carlo Methods
parent_uid: 2733fa33-374f-cb88-814c-413cb75b3483
title: 3.3 Monte Carlo Methods
uid: 91c4e401-232c-3823-cf38-1f612b323bb6
---

*   [<Monte Carlo Example]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-monte-carlo-example)
*   [3.3.1Introduction]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods)
*   [3.3.2Monte Carlo Analysis]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-monte-carlo-analysis)
*   [3.3.3Monte Carlo Example]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-monte-carlo-example)
*   [3.3.4Inversion Method for Sampling]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-inversion-method-for-sampling)
*   [\>Error Estimates for the Monte Carlo Method]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method)

3.3.4 Inversion Method for Sampling
-----------------------------------

[Measurable Outcome 3.4]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO34)

Input variability can be distributed in many ways beyond the simple uniform distribution considered above. In this section, we discuss a common approach used to implement the Monte Carlo method for non-uniform distributions. However, we note that for many of the most common distribution types, random number generators are widely available. For example, in MATLAB, the function randn returns random numbers that are normally distributed with a mean of zero and a standard deviation of one. In MATLAB's Statistics Toolbox, many other distribution types are available (see the documentation for the random function for details).

Inversion Method for Generating Random Numbers
----------------------------------------------

In these notes, we will discuss the inversion method for generating random numbers with non-uniform distributions. While other methods exist for generating random numbers, they are often based on the inversion method. The basic principle of the inversion method is to utilize the inverse of the cumulative distribution function (CDF) to transform a uniform distribution to a desired distribution. Recall that the CDF is defined as the integral of the PDF,

| \\\[F(x)= \\int \\limits \_{-\\infty }^{x} f(\\xi ) \\, d\\xi\\\] | (3.27) 

and that the CDF is related to probability by,

| \\\[F(x) \\equiv P{X \\leq x}\\\] | (3.28) 

That is, the probability of the random variable \\(X \\leq x\\) is the CDF evaluated at \\(x\\). As shown in Figure [3.6]({{< baseurl >}}/resources/normcdf), \\(F(x)\\) ranges from 0 to 1.

![](BASEURL_PLACEHOLDER/resources/normcdf)

**Figure 3.6**: Cumulative distribution function (CDF) of a normally distributed variable with zero mean and unit variance.

The inversion method for generating random numbers of an arbitrary distribution consists of the following two steps:

1.  Generate a random number, \\(u\\), from a uniform distribution between 0 and 1.
    
2.  Given \\(u\\), find the value of \\(x\\) at which \\(u=F(x)\\). In other words, invert \\(F(x)\\) such that, \\(x=F^{-1}(u)\\).
    

Sampling Triangular Distributions
---------------------------------

A triangular distribution is defined by the parameters \\(x\_{min}\\), the minimum value of \\(x\\), \\(x\_{mpp}\\), the most-probable value of \\(x\\), and \\(x\_{max}\\), the maximum value of \\(x\\). The cumulative distribution function (CDF) of a triangular distribution is,

| \\\[F(x) = \\frac{x\_{mpp}-x\_{min}}{x\_{max}-x\_{min}}\\left(\\frac{x-x\_{min}}{x\_{mpp}-x\_{min}}\\right)^2\\\] | (3.29) 

for \\(x\_{min} < x < x\_{mpp}\\), and

| \\\[F(x)=1-\\frac{x\_{max}-x\_{mpp}}{x\_{max}-x\_{min}}\\left(\\frac{x\_{max}-x}{x\_{max}-x\_{mpp}}\\right)^2\\\] | (3.30) 

for \\(x\_{mpp} < x < x\_{max}\\). Given a percentile drawn from a uniform random distribution, \\(u=F(x\_ u)\\), the value \\(x\_ u\\) can be found by inverting the previous relationships for \\(F(x)\\). Specifically, note that,

| \\\[F(x\_{mpp}) = \\frac{x\_{mpp}-x\_{min}}{x\_{max}-x\_{min}}.\\\] | (3.31) 

Thus, if \\(u < F(x\_{mpp})\\) then \\(x\_{min} < x < x\_{mpp}\\), we invert Equation 21.1 to find,

| \\\[x\_ u = x\_{min} + \\sqrt {u(x\_{max}-x\_{min})(x\_{mpp}-x\_{min})}\\\] | (3.32) 

Otherwise, if \\(u > F(x\_{mpp})\\) then \\(x\_{mpp} < x < x\_{max}\\), we invert Equation 21.2 to find,

| \\\[x\_ u = x\_{max}-\\sqrt {(1-u)(x\_{max}-x\_{min})(x\_{max}-x\_{mpp})}\\\] | (3.33) 

Consider a triangular distribution with the following parameters, \\(x\_{min}\\) = 0, \\(x\_{max}\\) = 1 and \\(x\_{mpp} = \\frac{1}{2}\\), which we want to draw a sample from. Suppose we sample a \\(U\[0,1\]\\) and obtain \\(u=\\frac{3}{4}\\), the corresponding sample from the triangular distribution \\(x\_ u\\) is,

Exercise 1

&nbsp; \\(\\sqrt {\\frac{3}{8}}\\) &nbsp;

&nbsp; \\(\\frac{1}{4}\\) &nbsp;

&nbsp; \\(\\frac{3}{4}\\) &nbsp;

&nbsp; \\(\\frac{\\sqrt {8}-1}{\\sqrt {8}}\\) &nbsp;

CheckShow Answer

Answer:

\\(F(\\frac{1}{2})\\) = \\(\\frac{1}{2}\\), the drawn \\(u > F(\\frac{1}{2})\\) and hence we can use Equation 21.2, which gives \\(x\_ u= 1 - \\frac{1}{\\sqrt {8}}\\).

BackMonte Carlo Example ContinueError Estimates for the Monte Carlo Method