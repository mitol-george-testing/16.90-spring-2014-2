---
content_type: page
parent_title: 3.2 Review of Probability and Statistics
parent_uid: 972a23bc-2208-f9b1-2895-30de24175e7d
title: 3.2 Review of Probability and Statistics
uid: 48e310af-9f94-1a31-5e65-7482fc62956d
---

*   [<Expectations]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-expectations)
*   [3.2.1Random Variables]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics)
*   [3.2.2Outcomes and Events]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-outcomes-and-events)
*   [3.2.3Distributions]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-distributions)
*   [3.2.4Expectations]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-expectations)
*   [3.2.5The Central Limit Theorem]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-the-central-limit-theorem)
*   [\>Monte Carlo Methods]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/monte-carlo-methods)

3.2.5 The Central Limit Theorem
-------------------------------

[Measurable Outcome 3.7]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO37), [Measurable Outcome 3.9]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO39)

In the first four units, we have introduced the concept of a random variable, the basic axioms of probability and probability distribution functions. We have seen that just like variables can be characterized by their value, random variables can be characterized by their probability distribution. We have also seen that we can have random variables that are functions of other random variables, just like deterministic variables can be functions of other deterministic variables.

Sums of Random Variables
------------------------

It is natural to ask whether there are more parallel properties that random variables and deterministic variables share. For example, we know that the sum of two deterministic variables is another deterministic variable. What can we say about the sum of two random variables? Quite obviously, the sum of two random variables \\(X\\) and \\(Y\\) is a new random variable,

| \\\[Z=Z(X,Y)=X+Y\\\] | (3.17) 

When we are adding two deterministic variables, we just have to add their values. What does it mean to add two random variables ?

Since \\(Z\\) is a random variable, it is characterized by its probability distribution, and this probability distribution has to depend on the distributions of \\(X\\) and \\(Y\\). Suppose \\(X\\) and \\(Y\\) are independent, continuous random variables, and have densities \\(f\_ X\\) and \\(f\_ Y\\). Then the density \\(f\_ Z\\) is given by the convolution,

| \\\[f\_ Z(z) = \\int \\limits \_{-\\infty }^{+\\infty } f\_{X}(x)f\_{Y}(z-x) \\, dx\\\] | (3.18) 

Thus, it is indeed possible to think about adding random variables, and the result of such an addition gives us the density of a new random variable via a convolution.

Examples of Sums of Two Random Variables
----------------------------------------

As a first example, suppose \\(X\_1 \\sim \\mathcal{U}(0,1)\\) and \\(X2 \\sim \\mathcal{U}(0,1)\\), then the convolution above results in a density for a triangularly distributed random variable.

| \\\[f\_{Z}(z) = \\left\\{ \\begin{array}{ll} z & \\mbox{for } 0 \\leq z \\leq 1, \\\\\[0.1in\] 2 - z & \\mbox{for } 1 \\leq z \\leq 2, \\\\\[0.1in\] 0 & \\mbox{otherwise } \\end{array}\\right.\\\] | (3.19) 

The sum of these two uniformly distributed random variables \\(X\_1\\) and \\(X\_2\\) is a triangularly distributed random variable. Now suppose we add another random variable \\(X3 \\sim \\mathcal{U}(0,1)\\) to this sum, we again get a new random variable, but calculating its density using the convolution is not easy.

However, there is an important exception. Suppose \\(X\_1 \\sim \\mathcal{N}(1,1)\\) and \\(X\_2 \\sim \\mathcal{N}(1,1)\\), then the convolution above results in a density for a normally distributed random variable \\(Z \\sim \\mathcal{N}(2,2)\\). So, the sum of two normally distributed random variables is again a normal random variable. The mean and variance of this sum are the sum of means and variances of the normals we added.

Further, if we average this sum we have,

| \\\[\\frac{Z}{2} = \\frac{X\_1 + X\_2}{2} \\sim \\mathcal{N}(1,\\frac{1}{2})\\\] | (3.20) 

If we now add \\(X\_3 \\sim \\mathcal{N}(1,1)\\), and average over all three, we again get a normally distributed random with density \\(\\mathcal{N}(1,\\frac{1}{3})\\), and so on. Adding \\(N\\) independent, normal random variables with density \\(\\mathcal{N}(1,1)\\) we obtain,

| \\\[\\frac{X\_1 + X\_2 + X\_3 + .... + X\_{N-1} + X\_ N}{N} \\sim \\mathcal{N}(1, \\frac{1}{N})\\\] | (3.21) 

Since this is true, no matter how large we make \\(N\\), we can say that it holds true as \\(N \\to \\infty\\).

The Central Limit Theorem
-------------------------

We saw above that for the particular case of independent, identically and normally distributed variables, the asymptotic average of these variables remains normally distributed. The mean of this asymptotic average is the average of means of each variable, and its variance tends to zero as \\(\\frac{1}{N}\\). Remarkably, this is property is true for the asymptotic average of any independent and identically distributed random variables, even if they are not normally distributed !

This is the basic result of the Central Limit Theorem, which tells us that if \\(X\_1\\), \\(X\_2\\), ... \\(X\_ N\\) are independent, identically distributed random variables, with \\(E(X\_1) = E(X\_2) = ... E(X\_ N) = \\mu\\) and \\(Var(X\_1) = Var(X\_2) = ... Var(X\_ N) = \\sigma ^2\\), then we have

| \\\[\\frac{\\sum \\limits \_{i=1}^{N} X\_ i}{N} - \\mu \\to \\mathcal{N}(0, \\frac{\\sigma ^{2}}{N})\\\] | (3.22) 

as \\(N \\to \\infty\\). So instead of averaging normals, if we kept averaging the uniform random variables that we added earlier, then eventually, the resultant random variable is guaranteed to have a normal distribution ! Not only that, the mean of this normal random variable will have the mean of the uniform random variables we added, and its variance will tend to zero.

Let \\(X\_1\\), \\(X\_2\\), \\(X\_3\\), \\(\\ldots\\) , \\(X\_ N\\) be i.i.d variables with \\(E(X\_1)=E(X\_2)=\\ldots =E(X\_ n)=\\mu\\). Then the means of the random variables \\(X\_1-\\mu\\), \\(X\_2-\\mu\\), \\(X\_3-\\mu\\), \\(\\ldots\\) , \\(X\_ N-\\mu\\) are

Exercise 1

 undefined

 \\(\\mu , \\mu , \\ldots , \\mu\\)

 \\(E(X\_1),E(X\_2), \\ldots , E(X\_ N)\\)

 0,0,\\(\\ldots\\),0

Answer:

\\(E(X\_1 - \\mu ) = \\int \_{-\\infty }^{+\\infty } (x - \\mu ) f\_ X(x)\\, dx = \\int \_{-\\infty }^{+\\infty } x f\_ X(x)\\, dx - \\int \_{-\\infty }^{+\\infty } \\mu f\_ X(x)\\, dx = \\mu - \\mu \\int \_{-\\infty }^{+\\infty } f\_ X(x)\\, dx = \\mu - \\mu = 0\\)

Further, let \\(Var(X\_1)=Var(X\_2)=\\ldots =Var(X\_ N)=\\sigma ^2\\). Then as \\(N \\to \\infty\\) we have,

Exercise 2

 \\(\\frac{\\sum \\limits \_{i=1}^{N} X\_ i}{N} - \\mu \\to N(\\mu , \\frac{\\sigma ^2}{N}) - \\mu\\)

 \\(\\frac{\\sum \\limits \_{i=1}^{N} X\_ i}{N} - \\mu \\to N(\\mu , \\frac{\\sigma ^{2}}{N})\\)

 \\(\\frac{\\sum \\limits \_{i=1}^{N} X\_ i}{N} - \\mu \\to N(0, \\frac{\\sigma ^{2}}{N})\\)

 None of the above

CheckShow Answer

Answer:

Direct application of the Central Limit Theorem.

BackExpectations ContinueMonte Carlo Methods