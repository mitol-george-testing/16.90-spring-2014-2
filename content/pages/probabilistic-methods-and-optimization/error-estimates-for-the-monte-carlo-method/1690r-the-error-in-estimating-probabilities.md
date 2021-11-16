---
content_type: page
parent_title: 3.4 Error Estimates for the Monte Carlo Method
parent_uid: 74bb46fc-55cb-5dc9-1f9b-7be6791726ec
title: 3.4 Error Estimates for the Monte Carlo Method
uid: ed041125-462b-3411-0831-40b32f255066
---

*   [<Error Estimates for the Monte Carlo Method]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method)
*   [3.4.1The Error in Estimating the Mean]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method)
*   [3.4.2The Error in Estimating Probabilities]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-the-error-in-estimating-probabilities)
*   [3.4.3The Error in Estimating the Variance]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-the-error-in-estimating-the-variance)
*   [3.4.4Bootstrapping]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-bootstrapping)
*   [\>The Error in Estimating the Variance]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/error-estimates-for-the-monte-carlo-method/1690r-the-error-in-estimating-the-variance)

3.4.2 The Error In Estimating Probabilities
-------------------------------------------

[Measurable Outcome 3.8]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO38), [Measurable Outcome 3.11]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO311), [Measurable Outcome 3.12]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO312)

Often, Monte Carlo simulations are used to estimate the probability of an event occurring. For example, in the turbine blade example, we might be interested in the probability that the hot metal temperature exceeds a critical value. Generically, suppose that the event of interest is \\(A\\). Then, an estimate of \\(P\\{ A\\}\\) is the fraction of times the event \\(A\\) occurs out of the total number of trials,

| \\\[\\hat{p}(A) = \\frac{N\_ A}{N}\\\] | (3.45) 

where \\(N\_ A\\) is the number of times \\(A\\) occurred in the Monte Carlo simulation of sample size \\(N\\).

\\(\\hat{p}(A)\\) is an unbiased estimate of \\(P\\{ A\\}\\). To see this, define a function \\(I(A\_ i)\\) which equals 1 if event \\(A\\) occurred on the \\(i\\)-th trial, and equals zero if \\(A\\) did not occur. For example, if the event \\(A\\) is defined as \\(y > y\_{limit}\\), \\(I(A\_ i)\\) would be defined as,

| \\\[I(A\_ i) = I(y\_ i > y\_{limit}) = \\left\\{ \\begin{array}{cc} 1 & \\mbox{if } y\_ i > y\_{limit}, \\\\ 0 & \\mbox{if } y\_ i \\leq y\_{limit}. \\end{array}\\right.\\\] | (3.46) 

Using this definition, the number of times that \\(A\\) occurred can be written as

| \\\[N\_ A = \\sum \_{i=1}^ N I(A\_ i).\\\] | (3.47) 

Finding the expectation of \\(N\_ A\\) gives,

| \\\[E\[N\_ A\] = E\[\\sum \_{i=1}^ N I(A\_ i)\] = \\sum \_{i=1}^ N E\[I(A\_ i)\].\\\] | (3.48) 

Since we assume that the Monte Carlo trials are drawn at random and independently from each other, then \\(E\[I(A\_ i)\] = P\\{ A\\}\\). Thus,

| \\\[E\[N\_ A\] = N P\\{ A\\}\\\] | (3.49) 

Finally, using this result we see that

| \\\[E\[\\hat{p}(A)\] = \\frac{E\[N\_ A\]}{N} = P\\{ A\\} .\\\] | (3.50) 

We can also use the central limit theorem to show that \\(\\hat{p}(A)\\) is normally distributed for large \\(N\\) with mean \\(P\\{ A\\}\\) and standard error,

| \\\[\\sigma \_{\\hat{p}} = \\sqrt {\\frac{P\\{ A\\} (1-P\\{ A\\} )}{N}}\\\] | (3.51) 

In the exposition above, we calculated the standard error in estimating the probability of an event \\(A\\) defined as \\(A=\\{ y:y > y\_{limit} \\}\\) using Monte Carlo sampling as \\(\\sqrt {\\frac{P\\{ A\\} (1-P\\{ A\\} )}{N}}\\). Now suppose we estimate the probability of the event \\(B\\), which is defined as \\(B = \\{ y:y > \\frac{y\_{limit}}{2} \\}\\) using the Monte Carlo method, with the same number of samples. The standard error in estimating this probability will be given by,

Exercise 1

&nbsp; \\(\\sqrt {\\frac{P\\{ A\\} (1-P\\{ A\\} )}{2N}}\\) &nbsp;

&nbsp; \\(\\sqrt {\\frac{P\\{ B\\} (1-P\\{ B\\} )}{N}}\\) &nbsp;

&nbsp; \\(\\sqrt {\\frac{P\\{ B\\} (1-P\\{ B\\} )}{2N}}\\) &nbsp;

CheckShow Answer

Answer:

For estimating the standard error associated with computing \\(P\\{ B\\}\\), the exposition above remains the same, except \\(P\\{ A\\}\\) is replaced by \\(P\\{ B\\}\\).

BackError Estimates for the Monte Carlo Method ContinueThe Error in Estimating the Variance