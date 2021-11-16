---
content_type: page
parent_title: 'Unit 3: Probabilistic Methods and Optimization'
parent_uid: 487c3b15-ab67-d7c9-5cff-a6b147049d0c
title: 3.4 Error Estimates for the Monte Carlo Method
uid: 74bb46fc-55cb-5dc9-1f9b-7be6791726ec
---

*   [<Inversion Method for Sampling]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods/1690r-inversion-method-for-sampling)
*   [3.4.1The Error in Estimating the Mean]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method)
*   [3.4.2The Error in Estimating Probabilities]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-the-error-in-estimating-probabilities)
*   [3.4.3The Error in Estimating the Variance]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-the-error-in-estimating-the-variance)
*   [3.4.4Bootstrapping]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-bootstrapping)
*   [\>The Error in Estimating Probabilities]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-the-error-in-estimating-probabilities)

3.4.1 The Error in Estimating the Mean
--------------------------------------

[Measurable Outcome 3.6]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO36), [Measurable Outcome 3.7]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO37), [Measurable Outcome 3.8]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO38), [Measurable Outcome 3.9]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO39), [Measurable Outcome 3.10]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO310), [Measurable Outcome 3.11]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO311), [Measurable Outcome 3.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO312)

In this unit, we will analyze the accuracy of Monte Carlo simulation in estimating the mean of a distribution. In the next sections, we will look at other probabilistic outputs, such as the variance and probability.

Let the output of interest be labelled \\(y\\). For example, \\(y=T\_{mh}\\) (the hot-side metal temperature) in the turbine blade heat transfer problem of the last unit. For a Monte Carlo simulation of sample size \\(N\\), let the individual values from each trial be labelled \\(y\_ i\\) where \\(i\\)=1 to \\(N\\). In this section, we will consider the error made when estimating the expected value, also known as the mean, of \\(y\\) when using a sample that has \\(N\\) trials.

If the probability density of \\(y\\) is \\(f(y)\\), then the expected value of \\(y\\) is,

| \\\[\\mu \_ y \\equiv E(y) = \\int \\limits \_{-\\infty }^{\\infty } y \\, f(y) \\, dy.\\\] | (3.34) 

Using the \\(N\\) trials, a reasonable estimator for \\(\\mu \_ y\\) would be the sample mean,

| \\\[\\bar{y} \\equiv \\frac{1}{N} \\sum \\limits \_{i=1}^{N} y\_ i\\\] | (3.35) 

Since a Monte Carlo simulation involves pseudo-random draws of the inputs, we will get different results each time we perform the probabilistic analysis. That is, each time we run a Monte Carlo simulation, we will obtain slightly different results for \\(\\bar{y}\\). In the following analysis, we will see that the variability in our results of \\(\\bar{y}\\) (i.e., how much the mean estimate varies from Monte Carlo simulation to Monte Carlo simulation) depends on \\(N\\), the number of trials in each Monte Carlo simulation.

The Moments of the Error
------------------------

The first question we will ask is: on average how accurate is \\(\\bar{y}\\) as an estimate of \\(\\mu \_ y\\)? To answer this, take the expectation of \\(\\bar{y} - \\mu \_ y\\):

| \\\[E(\\bar{y} - \\mu \_ y)= E(\\bar{y}) - \\mu \_ y \\\\ =E\\left(\\frac{1}{N}\\sum \\limits \_{i=1}^{N} y\_ i \\right) - \\mu \_ y \\\\ =\\frac{1}{N}\\sum \\limits \_{i=1}^{N} E(y\_ i) - \\mu \_ y\\\] | (3.36) 

Since the \\(y\_ i\\)'s occur from a random sampling of the inputs when using the Monte Carlo method, then \\(E(y\_ i)=\\mu \_ y\\). Thus we have:

| \\\[E(\\bar{y} - \\mu \_ y) = \\frac{1}{N} N \\mu \_ y - \\mu \_ y = 0\\\] | (3.37) 

This result shows that on average, the error in using \\(\\bar{y}\\) to approximate \\(\\mu \_ y\\) is zero. When an estimator gives an expected error of zero, it is called an unbiased estimator.

Next, to quantify the variability in \\(\\bar{y}\\), we use the variance of \\(\\bar{y}-\\mu \_ y\\), noting that the variance of \\(\\mu \_ y\\) is zero as it is a constant:

| \\\[V(\\bar{y} - \\mu \_ y) = V(\\bar{y}) - V(\\mu \_ y) \\\\ = V(\\bar{y}) \\\\ = V\\left(\\frac{\\sum \\limits \_{i=1}^{N} y\_ i}{N}\\right) \\\\ = \\frac{1}{N^2}V\\left(\\sum \\limits \_{i=1}^{N} y\_ i\\right)\\\] | (3.38) 

Because the Monte Carlo method draws independent, random samples, the variance of the sum of the samples \\(y\_ i\\) is the sum of their variances. Therefore, we have,

| \\\[V(\\bar{y} - \\mu \_ y) = \\frac{1}{N^2}\\sum \\limits \_{i=1}^{N} V(y\_ i) \\\\ = \\frac{1}{N^2} N \\sigma \_ y^{2} = \\frac{\\sigma \_ y^{2}}{N}\\\] | (3.39) 

Summarizing, we have found that,

| \\\[\\mu \_{\\bar{y}} \\equiv E(\\bar{y}) = \\mu \_ y,\\quad \\sigma \_{\\bar{y}}^2 \\equiv E\[(\\bar{y} - \\mu \_ y)^2\] = \\frac{\\sigma \_ y^{2}}{N}\\\] | (3.40) 

The quantity \\(\\sigma \_{\\bar{y}}\\) is known as the standard error of the estimator. Thus, the standard error decreases with the square root of the sample size, \\(\\sqrt {N}\\). In other words, to decrease the variability in the mean estimate by a factor of 10 requires a factor of 100 increase in the number of Monte Carlo trials.

The Probability Distribution of the Error
-----------------------------------------

For large sample size \\(N\\), the central limit theorem can be applied to approximate the distribution of \\(\\bar{y}\\). Specifically, the central limit theorem says for large \\(N\\), the distribution of \\(\\bar{y} - \\mu \_ y\\) will approach a normal distribution with mean 0 and variance \\(\\frac{\\sigma \_ y^2}{N}\\):

| \\\[f(\\bar{y} - \\mu \_ y) \\to \\mathcal{N}(0,\\sigma \_{\\bar{y}}) = \\mathcal{N}\\left(0,\\frac{\\sigma \_ y^{2}}{N}\\right)\\\] | (3.41) 

We can now use this to make precise statements about the error in \\(\\bar{y}\\). Suppose, for example, that we want to have \\(95\\%\\) confidence on the possible values for \\(\\mu \_ y\\). Since the normal distribution has approximately \\(95\\%\\) of its values within \\(\\pm\\)2 standard deviations of the mean, then we know that,

| \\\[P\\{ -2\\frac{\\sigma \_ y}{\\sqrt {N}} \\leq \\bar{y} - \\mu \_ y \\leq 2\\frac{\\sigma \_ y}{\\sqrt {N}} \\} \\approx 0.95.\\\] | (3.42) 

If even higher confidence is wanted, then a wider range of error must be accepted. For example, a \\(99\\%\\) confidence interval occurs at \\(\\pm\\)3 standard deviations for a normal distribution. Thus,

| \\\[P\\{ -3\\frac{\\sigma \_ y}{\\sqrt {N}} \\leq \\bar{y} - \\mu \_ y \\leq 3\\frac{\\sigma \_ y}{\\sqrt {N}} \\} \\approx 0.99.\\\] | (3.43) 

Unfortunately, in a practical situation, we cannot actually calculate the above error estimates or confidence intervals because they depend on \\(\\sigma \_ y\\) and we do not know \\(\\sigma \_ y\\). So, we typically use an estimate of \\(\\sigma \_ y\\). In particular, an unbiased estimate of \\(\\sigma \_ y^2\\) is

| \\\[s\_ y^2 \\equiv \\frac{1}{N-1}\\sum \\limits \_{i=1}^{N}(y\_ i - \\bar{y})^2.\\\] | (3.44) 

So, the usual practice is to replace \\(\\sigma \_ y\\) by \\(s\_ y\\) in the various error estimates. Note, this does introduce additional uncertainty in the quality of the estimate and for small sample sizes this could be significant.

Suppose \\(y\\) is a continuous random variable with expected value \\(\\mu \_ y\\). We approximate \\(\\mu \_ y\\) by taking \\(N\\) i.i.d. samples from \\(y\\), \\(\\{ y\_ i\\} \_{i=1}^{N}\\), and computing the sample mean \\(\\bar{y} \\equiv \\frac{\\sum \\limits \_{i=1}^{N} y\_ i}{N}\\). Then the error, \\(e= \\mu \_ y - \\frac{\\sum \\limits \_{i=1}^{N} y\_ i}{N}\\) is a

Exercise 1

 undefined

 deterministic variable

 random variable

 can be either a random or deterministic variable

CheckShow Answer

Answer:

The \\(y\_ i\\)'s are all random variables. Therefore their sum and average is also a random variable. Subtracting a random variable from a deterministic variable also gives a random variable.

BackInversion Method for Sampling ContinueThe Error in Estimating Probabilities