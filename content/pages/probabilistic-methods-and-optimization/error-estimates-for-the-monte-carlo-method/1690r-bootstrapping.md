---
content_type: page
parent_title: 3.4 Error Estimates for the Monte Carlo Method
parent_uid: 74bb46fc-55cb-5dc9-1f9b-7be6791726ec
title: 3.4 Error Estimates for the Monte Carlo Method
uid: 22e0637c-8322-5bd8-a9d4-e80723fbc928
---

*   [<The Error in Estimating the Variance]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-the-error-in-estimating-the-variance)
*   [3.4.1The Error in Estimating the Mean]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method)
*   [3.4.2The Error in Estimating Probabilities]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-the-error-in-estimating-probabilities)
*   [3.4.3The Error in Estimating the Variance]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-the-error-in-estimating-the-variance)
*   [3.4.4Bootstrapping]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-bootstrapping)
*   [\>Variance Reduction Techniques for the Monte Carlo Method]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/variance-reduction-techniques-for-the-monte-carlo-method)

3.4.4 Bootstrapping
-------------------

The standard errors and confidence intervals for a variety of estimators often rely upon assumptions on the underlying output values, \\(y\\). For example, the standard error for the variance as given in the previous unit requires the assumption that \\(y\\) is distributed normally. Clearly, in most applications that will not be the case. In this situation, an alternative method is required if confidence intervals are desired. One such method is known as bootstrapping.

As an example, let's consider the Monte Carlo estimation of the 50-percentile value of a population. From a Monte Carlo sample, the 50-percentile value of the population could be estimated as the median of the sample. If we wanted to determine the standard error associated with using the median of sample size \\(N\\) as an estimate for the 50-percentile value, one possibility would be to run multiple Monte Carlo's of sample size \\(N\\) and estimate the variability of the estimator directly. Suppose the a total of \\(M\\) Monte Carlo samples are run (each of size \\(N\\)), then the total number of simulations would be \\(M \\times N\\). Labelling \\(\\theta \_ i\\) as the estimator (i.e. the median) from the \\(i\\)-th Monte Carlo sample, the distribution of \\(\\theta\\) can be determined and confidence intervals can be built using the \\(M\\) values of \\(\\theta \_ i\\). This, however, could be very expensive since \\(M \\times N\\) simulations are required.

Bootstrapping avoids the need for \\(M \\times N\\) simulations by resampling from a single Monte Carlo simulation. After a single Monte Carlo simulation, \\(N\\) simulations have been performed and the results of the simulations are all equally likely to have occurred (since they were drawn in a random, independent manner). A bootstrap resampling is performed by drawing with uniform probability from this original Monte Carlo sample. Specifically, if we wanted to generate \\(M\\) bootstrap samples of size \\(N\\):

1.  Perform an initial Monte Carlo sample of size \\(N\\) to produce \\(y\_ i\\) with \\(i=1\\) to \\(N\\). From this sample, calculate the desired estimator \\(\\theta \_1 = \\theta (y\_ i)\\).
    
2.  Resample the values of \\(y\_ i\\) assuming uniform probability of the events (i.e. each \\(y\_ i\\) has a probability of \\(1/N\\)). Since the same event may occur a different number of times in this resample and in the original sample, this will generate a new sample, \\(\\hat{y}\_ i\\). From this resample, calculate the desired estimator, \\(\\theta \_ j = \\theta (\\hat{y}\_ i)\\).
    
3.  Perform the resampling in Step 2 a total of \\(M-1\\) times. In all, this will produce \\(M\\) values of the estimator, \\(\\theta \_1\\) through \\(\\theta \_ M\\).
    
4.  From the \\(M\\) values of \\(\\theta \_ i\\), confidence intervals can be determined.
    

BackThe Error in Estimating the Variance ContinueVariance Reduction Techniques for the Monte Carlo Method