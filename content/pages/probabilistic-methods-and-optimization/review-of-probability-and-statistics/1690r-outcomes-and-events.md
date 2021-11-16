---
content_type: page
parent_title: 3.2 Review of Probability and Statistics
parent_uid: 972a23bc-2208-f9b1-2895-30de24175e7d
title: 3.2 Review of Probability and Statistics
uid: a3d2bfd5-90c2-ddaf-a1c4-73639ba4be5e
---

*   [<Review of Probability and Statistics]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics)
*   [3.2.1Random Variables]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics)
*   [3.2.2Outcomes and Events]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-outcomes-and-events)
*   [3.2.3Distributions]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-distributions)
*   [3.2.4Expectations]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-expectations)
*   [3.2.5The Central Limit Theorem]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-the-central-limit-theorem)
*   [\>Distributions]({{< baseurl >}}/pages/probabilistic-methods-and-optimization/review-of-probability-and-statistics/1690r-distributions)

3.2.2 Outcomes and Events
-------------------------

[Measurable Outcome 3.2]({{< baseurl >}}/pages/measurable-outcome-index/#anchorMO32)

In this unit, we give some definitions and introduce some formalism from probability theory. Consider an experiment or activity that will be performed several times. Each time the experiment is performed, its outcome can be recorded. An event is a set of outcomes for which certain conditions have been met. An elementary event consists of only a single outcome.

**Example 3:** Consider the inspection of rotor blades in the turbine of a jet engine example from the last unit. We had earlier mentioned that the outcome of a single inspection is the determination of the number of blades that must be replaced due to damage. Thus, the outcomes are the set of non-negative integers, {0,1,2,...,N}. If the number of blades replaced in a single engine is greater than 5, than this might indicate more significant damage has occurred, and regulations dictate a more thorough inspection of the engine. In this situation, we would be interested in the event where the number of replaced blades is {6,7,8,...,N}. This is not an elementary event since it consists of more than one outcome. However, we would also be interested in the situation where no blades are replaced. In this case, the event consists of a single outcome (i.e. 0) and therefore is an elementary event.

The Axioms of Probability
-------------------------

Given an event, \\(A\\), the probability of the event is \\(P\\{ A\\}\\). Probabilities are assumed to satisfy the following properties:

1.  \\(P\\{ A\\}\\) \\(\\geq\\) 0.
    
2.  If and only if the event is certain to occur, then \\(P\\{ A\\} =1\\).
    
3.  Given two mutually exclusive events, \\(A\\) and \\(B\\), then \\(P\\{ A+B\\} =P\\{ A\\} +P\\{ B\\}\\).
    

BackReview of Probability and Statistics ContinueDistributions