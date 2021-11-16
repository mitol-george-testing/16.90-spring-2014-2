---
content_type: page
parent_title: 3.5 Variance Reduction Techniques for the Monte Carlo Method
parent_uid: e719ff51-42ac-62fb-c38b-4410308e2feb
title: 3.5 Variance Reduction Techniques for the Monte Carlo Method
uid: bb1256bc-6917-d853-f4c6-36ce5943967f
---

*   [<Variance Reduction Techniques for the Monte Carlo Method]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/variance-reduction-techniques-for-the-monte-carlo-method)
*   [3.5.1Monte Carlo Error as a Random Variable]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/variance-reduction-techniques-for-the-monte-carlo-method)
*   [3.5.2Importance Sampling]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/variance-reduction-techniques-for-the-monte-carlo-method/1690r-importance-sampling)
*   [\>Introduction to Design Optimization]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/introduction-to-design-optimization)

3.5.2 Importance Sampling
-------------------------

[Measurable Outcome 3.4]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO34)

Introduction
------------

A Monte Carlo method better than SRS will reduce the variance of the error. Such methods are called variance reduction techniques. One important variance reduction technique is called importance sampling. Importance Sampling reduces variance by cleverly changing the underlying distribution from which we sample. Suppose that we seek to approximate the expected value,

| \\\[\\mu = \\int \\limits \_{-\\infty }^{\\infty } h(x) \\, f\_ X(x) \\, dx\\\] | (3.61) 

Suppose we know another probability density \\(w(x)\\). The expectation can then be written as,

| \\\[\\mu = \\int \\limits \_{-\\infty }^{\\infty } h(x) \\, \\frac{f\_ X(x)}{w(x)} \\, w(x) \\, dx\\\] | (3.62) 

Now instead of sampling from \\(f\_ X(x)\\), we would sample from \\(w(x)\\), but we would have to modify the canonical estimator to the weighted form,

| \\\[\\bar{y}\_{IS} = \\frac{1}{N} \\sum \\limits \_{i=1}^{N} h(x\_ i)\\frac{f\_ X(x\_ i)}{w(x\_ i)} = \\frac{1}{N} \\sum \\limits \_{i=1}^{N} h(x\_ i) w^{\*}(x\_ i)\\\] | (3.63) 

We have modified the underlying distribution from which we are sampling, and hence we have weighted each sample to correct for the bias our modification introduced.

Properties of Importance Sampling Based Methods
-----------------------------------------------

Clearly \\(E(\\bar{y}\_{IS}) = \\mu\\) (show this), but what about \\(Var(\\bar{y}\_{IS})\\) ? We have,

| \\\[Var(\\bar{y}\_{IS}) = \\frac{1}{N^2} \\sum \\limits \_{i=1}^{N} Var(h(x\_ i w^{\*}(x\_ i))) = \\frac{1}{N} Var(h(x) w^{\*}(x))\\\] | (3.64) 

The importance sampling method thus reduces variance if we pick a \\(w(x)\\) such that, \\(Var\_{f\_ X}(h(x)) \\leq Var\_{w}(h(x) w^{\*}(x))\\). A little algebra shows that this is true if

| \\\[\\int h^2(x) \\, \\frac{f(x)}{w(x)} \\, f(x) \\, dx \\leq \\int h^2(x) \\, f(x) \\, dx\\\] | (3.65) 

In class, we will discuss how we can pick such a density \\(w(x)\\) and develop an importance sampling algorithm for estimating the probability of low probability events.

BackVariance Reduction Techniques for the Monte Carlo Method ContinueIntroduction to Design Optimization