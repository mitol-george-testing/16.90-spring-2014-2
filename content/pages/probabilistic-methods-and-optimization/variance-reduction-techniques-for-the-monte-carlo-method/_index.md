---
content_type: page
parent_title: 'Unit 3: Probabilistic Methods and Optimization'
parent_uid: 487c3b15-ab67-d7c9-5cff-a6b147049d0c
title: 3.5 Variance Reduction Techniques for the Monte Carlo Method
uid: e719ff51-42ac-62fb-c38b-4410308e2feb
---

*   [<Bootstrapping]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-bootstrapping)
*   [3.5.1Monte Carlo Error as a Random Variable]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/variance-reduction-techniques-for-the-monte-carlo-method)
*   [3.5.2Importance Sampling]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/variance-reduction-techniques-for-the-monte-carlo-method/1690r-importance-sampling)
*   [\>Importance Sampling]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/variance-reduction-techniques-for-the-monte-carlo-method/1690r-importance-sampling)

3.5.1 Monte Carlo Error as a Random Variable
--------------------------------------------

[Measurable Outcome 3.9]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO39)

Monte Carlo Error as a Random Variable
--------------------------------------

In the last subsection, we analyzed the error made while using the Monte Carlo method to tackle problems exhibiting uncertainty. The key ideas in our analysis were:

1.  The recognition of the Monte Carlo error as a random variable.
    
2.  The result that the error has a normal distribution under certain sampling conditions.
    

Specifically, we recognized that the error \\(e\\) made in estimating the expected value of a random variable \\(X\\) with a distribution \\(f\_ X\\),

| \\\[\\mu \_ X = \\int \\limits \_{-\\infty }^{\\infty } x \\, f\_ X(x) \\, dx\\\] | (3.58) 

using the canonical estimator,

| \\\[\\bar{y} = \\frac{1}{N} \\sum \\limits \_{i=1}^{N} y\_ i\\\] | (3.59) 

is a normally distributed random variable,

| \\\[e \\to \\mathcal{N}\\left(0,\\frac{\\sigma ^2}{N}\\right)\\\] | (3.60) 

Improving the Monte Carlo Method
--------------------------------

The standard Monte Carlo method that we have seen so far is also called Simple Random Sampling (SRS). As this name suggests, the standard Monte Carlo method is the most simple approach towards dealing with randomness in a system. It is intuitive to think that there are more sophisticated approaches to handle randomness, which would decrease the error faster than SRS.

BackBootstrapping ContinueImportance Sampling