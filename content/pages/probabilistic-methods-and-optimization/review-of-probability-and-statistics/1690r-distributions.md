---
content_type: page
parent_title: 3.2 Review of Probability and Statistics
parent_uid: 972a23bc-2208-f9b1-2895-30de24175e7d
title: 3.2 Review of Probability and Statistics
uid: 0c7b4a5a-66d4-c9d6-0849-150ad651b9c6
---

*   [<Outcomes and Events]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-outcomes-and-events)
*   [3.2.1Random Variables]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics)
*   [3.2.2Outcomes and Events]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-outcomes-and-events)
*   [3.2.3Distributions]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-distributions)
*   [3.2.4Expectations]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-expectations)
*   [3.2.5The Central Limit Theorem]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-the-central-limit-theorem)
*   [\>Expectations]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-expectations)

3.2.3 Distributions
-------------------

[Measurable Outcome 3.3]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO33), [Measurable Outcome 3.4]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO34)

In the first unit, we were introduced to the concept of a random variable, where we distinguished it from a deterministic variable. The first step in an engineering analysis is to identify the random variables present in the system. Then, we need to characterize these random variables, i.e. specify appropriate models of their uncertain behavior.

Random variables can be characterized by assigning them with a probability distribution function. A discrete random variable is characterized by its probability mass function, which assigns probabilities to the event that the random variable takes certain values. A continuous random variable is characterized by its probability density function, which assigns probabilities to the event that the random variable lies in a certain interval. We first discuss the probability mass functions, and then move on the probability density functions.

Probability Mass Functions
--------------------------

Consider a discrete random variable \\(X\\), and the event \\(A\\) that \\(X\\) is equal to a specific value \\(x\\). The probability of \\(A\\) can be written as,

| \\\[P\\{ A\\} =P\\{ X=x\\} =p\_ X(x)\\\] | (3.3) 

where \\(p\_ X(x)\\) is called the probability mass function of \\(X\\). Note that since \\(p\_ X(x)\\) is a probability value, it is always less than one, and it is zero at all those points which the random variable \\(X\\) will never be equal to.

**Example 3:** Consider the rotor blades in example 1 of unit 1. Suppose the total number of rotor blades was 4. The random variable \\(N\_ R\\) is a discrete random variable, which can take 5 different values. A possible probability mass funtion for \\(N\_ R\\) is as follows,

| \\\[p\_{N\_ R}(x) = \\left\\{ \\begin{array}{ll} 0.6 & \\mbox{for } x = 0, \\\\\[0.1in\] 0.2 & \\mbox{for } x = 1, \\\\\[0.1in\] 0.1 & \\mbox{for } x = 2, \\\\\[0.1in\] 0.05 & \\mbox{for } x = 3, \\\\\[0.1in\] 0.05 & \\mbox{for } x = 4, \\\\\[0.1in\] 0 & \\mbox{for } x \\neq \\{ 0,1,2,3,4\\} \\end{array}\\right.\\\] | (3.4) 

Note that since the \\(p\_{N\_ R}(x)\\) are probability values, they sum to 1 over their domain \\(x\\).

Probability Density Functions
-----------------------------

A probability density function (PDF) is used to describe the probability of a continuous random variable being in some range. In particular, consider a random variable \\(X\\), and the event \\(A\\) that it lies between the numbers \\(a\\) and \\(b\\), i.e., \\(a \\leq X \\leq b\\). The probability of the event \\(A\\) can be written as,

| \\\[P\\{ A\\} = P\\{ a \\leq X \\leq b\\} = \\int \\limits \_{a}^{b} f\_ X(x) dx,\\\] | (3.5) 

where \\(f\_ X(x)\\) is called the probability density of \\(X\\). Note that unlike the probability mass function, the probability density function \\(f\_ X(x)\\), by itself, does not give the probability of an event occuring. Indeed, \\(f\_ X(x)\\) can be more than one for a given value of \\(x\\), however it can never be less than zero for any \\(x\\).

A common (and probably the simplest) distribution is the uniform distribution. In this case, the probability density is constant within some range and zero outside of this range,

| \\\[f\_ X(x) = \\left\\{ \\begin{array}{ll} \\frac{1}{b-a} & \\mbox{for } a \\leq x \\leq b, \\\\\[0.1in\] 0, & \\mbox{otherwise}. \\end{array}\\right.\\\] | (3.6) 

We would say that the random variable \\(X\\) is uniformly distributed, and denote it as \\(X \\sim U(a,b)\\). Other distribution types are described later in the unit.

Cumulative Density Functions
----------------------------

The cumulative distribution function (CDF) of a random variable \\(X\\) is defined as the probability of the event that \\(X \\leq x\\). Specifically,

| \\\[F(x) \\equiv P\\{ X \\leq x\\}\\\] | (3.7) 

The CDF and PDF of \\(X\\) are related as follows,

| \\\[F(a) = \\int ^{a}\_{-\\infty } f\_ X(x)\\, dx\\\] | (3.8) 

Thus, we can show,

| \\\[F(b) - F(a) = \\int ^{b}\_{a} f\_ X(x)\\, dx.\\\] | (3.9) 

Furthermore, this implies that

| \\\[f\_ X = \\frac{dF}{dx}\\\] | (3.10) 

Some Common Types of Distributions
----------------------------------

The normal (or Gaussian) distribution is,

| \\\[f\_ X(x) = \\frac{1}{\\sigma \_ x\\sqrt {2\\pi }}e^{-(x-\\mu \_ x)^2/2\\sigma \_ x^2}\\\] | (3.11) 

We will use the common notation \\(X \\sim \\mathcal{N}(\\mu ,\\sigma ^2)\\) to indicate that \\(X\\) is a normally-distributed random variable with mean \\(\\mu\\) and variance \\(\\sigma ^2\\).

Let \\(N\_ R\\) be distributed as in example 3. For example 1, let \\(B\\) be the event that the number of blades to be replaced are more than 2. Then \\(P\\{ B\\}\\) is

Exercise 1

 0.2

 0.1

 0.05

 None of the above

Answer:

\\(P\\{ B\\}\\) = \\(P\\{ NR > 2\\}\\) = \\(P\\{ N\_ R = 3 \\text { or } N\_ R = 4\\}\\) = \\(p\_{N\_ R}(3) + p\_{N\_ R}(4)\\) = 0.05 + 0.05 = 0.1

Let \\(X\\) be a continuous random variable, such that \\(a \\leq X \\leq b\\). Then the probability that \\(X=\\frac{a+b}{2}\\) is:

Exercise 2

 \\(\\int \_{\\frac{a+b}{2}}^{\\frac{a+b}{2}} f\_ X(x) \\, dx\\)

 \\(f\_ X(\\frac{a+b}{2})\\)

 0

 Both a and c

Answer:

For a continuous random variable, the probability of the random variable taking any single value is 0, only events where the random variable lies in an interval have non-zero probability. Another way to see this is that

| \\\[P\\{ \\frac{a+b}{2} \\leq X \\leq \\frac{a+b}{2}\\} = \\int \_{\\frac{a+b}{2}}^{\\frac{a+b}{2}} f\_ X(x) \\, dx = 0\\\] | (3.12) 

by the definition of a definite integral.

Let \\(X\\) be the same random variable as in Exercise. Then \\(F(b)\\)

Exercise 3

 \\(\\int \_{a}^{\\infty } f\_ X(x) \\, dx\\)

 \\(\\int \_{a}^{b} f\_ X(x) \\, dx\\)

 \\(\\int \_{-\\infty }^{\\infty } f\_ X(x) \\, dx\\)

 All of the above

CheckShow Answer

Answer:

The distribution of \\(X\\), \\(f\_ X(x)\\) is non-zero in the interval \\(\\{ a \\leq X \\leq b \\}\\), and 0 everywhere else. Now by definition \\(F(b)=\\int \_{-\\infty }^{b} f\_ X(x) \\, dx\\). This is equal to all the three integrals above because \\(f\_ X(x)\\) is zero outside the interval \\(\\{ a \\leq X \\leq b\\}\\).

BackOutcomes and Events ContinueExpectations